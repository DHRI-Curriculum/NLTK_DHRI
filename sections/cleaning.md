[<<< Previous](built-in.md) | [Next >>>](make_corpus.md)

# Making Your Own Corpus: Data Cleaning

Thus far, we have been asking questions that take stopwords and grammatical features into account. For the most part, we want to exclude these features since they don't actually contribute very much semantic content to our models. Therefore, we will:

1. Remove capitalization and punctuation (we've already done this).
2. Remove stop words.
3. Lemmatize (or stem) our words, i.e. "jumping" and "jumps" become "jump."


## Adding Stopwords

We already completed step one, and are now working with our `text1_tokens`. Remember, this variable,  `text1_tokens`, contains a list of strings that we will work with. We want to remove the stop words from that list. The NLTK library comes with fairly comprehensive lists of stop words for many languages. Stop words are function words that contribute very little semantic meaning and most often have grammatical functions. Usually, these are function words such as determiners, prepositions, auxiliaries, and others.

To use NLTK's stop words, we need to import the list of words from the corpus. (We could have done this at the beginning of our program, and in more fully developed code, we would put it up there, but this works, too.) In the next cell, type:

```python
from nltk.corpus import stopwords
```

We need to specify the English list, and save it into its own variable that we can use in the next step:

```python
stops = stopwords.words('english')
```

Now we want to go through all of the words in our text, and if that word is in the stop words list, remove it from our list. Otherwise, skip it. The code below is VERY slow (there's a faster option beneath it). The way we write this in Python is:

```python
for t in text1_tokens:
    if t in stops:
        text1_tokens.remove(t)
    else:
        pass
```
        
A faster option, using list comprehensions, discussed in the previous section: 

```python
text1_tokens = [t for t in text1_tokens if t not in stops]
```


### Verifying List Contents

Now that we removed our stop words, let's see how many words are left in our list:

```python
len(text1_tokens)
```

You should get a much lower number.

For reference, let's also check how many unique words there are. We will do this by making a set of words. Sets are the same in Python as they are in math, they are all of the unique words rather than all the words. So, if "whale" appears 200 times in the list of words, it will only appear once in the set.

```python
len(set(text1_tokens))
```


## Lemmatizing Words

Now that we've removed the stop words from our corpus, the next step is to stem or lemmatize the remaining words. This means that we will strip off the grammatical structure from the words. For example, cats --> cat, and walked --> walk. If that was all we had to do, we could stem the corpus and achieve the correct result, because stemming (as the name implies) really just means cutting off affixes to find the root (or the stem). Very quickly, however, this gets complicated, such as in the case of men --> man and sang --> sing. Lemmatization deals with this by looking up the word in a reference and finding the appropriate root (though note that this still is not entirely accurate). Lemmatization, therefore, takes a relatively long time, since each word must be looked up in a reference. NLTK comes with pre-built stemmers and lemmatizers.

We will use the WordNet Lemmatizer from the NLTK Stem library, so let's import that now: 

```python
from nltk.stem import WordNetLemmatizer
```

Because of the way that it is written "under the hood," an instance of the lemmatizer needs to be called. We know this from reading [the docs](https://www.nltk.org/).

```python
wordnet_lemmatizer = WordNetLemmatizer()
```

Now we will lemmatize the words in the list. This time, we will only use the faster version because it takes a long time.

```python
text1_clean = [wordnet_lemmatizer.lemmatize(t) for t in text1_tokens]
```


### Verifying List Contents

Let's check now to see how long our final, cleaned version of the data is and then check the unique set of words:

```python
len(text1_clean)

len(set(text1_clean))
```

This set should be much smaller than the set before we lemmatized. Now if we were to calculate lexical density, we would be looking at how many word stems with semantic content are represented in *Moby Dick*, which gets at a different question than our first analysis of lexical density.

Now let's have a look at the words Melville uses in *Moby Dick*. We'd like to look at all of the *types*, but not necessarily all of the *tokens.* We will order this set so that it is in an order we can handle. In the next cell, type:

```python
sorted(set(text1_clean))
```

A list of all the words in *Moby Dick* should appear. The list begins with 'a', which we might have expected to be removed in the stemming process, and some words we wouldn't have expected, such as "abbreviate" and "abbreviation". As we mentioned before, lemmatizing looks up the dictionary form of the word, and these would be different entries. A better example is with 'meaning' and 'meanness.' A lemmatizer would retain these two as separate words. A stemmer would not. We will stick with the output of the Lemmatizer, but just for illustration, we can try it out with a stemmer instead (Porter is the most common).  


## Stemming Words

The code to implement this and view the output is below:

```python
from nltk.stem import PorterStemmer
porter_stemmer = PorterStemmer()
t1_porter = [porter_stemmer.stem(t) for t in text1_tokens]
print(len(set(t1_porter)))
print(sorted(set(t1_porter)))
```

A very different list of words is produced. This list is shorter than the list produced by the lemmatizer, but is also more accurate because it avoids collapsing synonyms. You might also notice that some of the words are transformed. Stemmers each have their own rules, the Porter stemmer takes a word like "berry" and "berries" and makes them both "berri" whereas a lemmatizer would return it as "berry". Stemmers are faster than lemmatizers, so when speed matters more than accuracy, go with a stemmer. When accuracy matters more, go with a lemmatizer. In an academic research setting, the choice is clear. We will proceed with our lemmatized corpus.

```python
my_dist = FreqDist(text1_clean)
```

If nothing happened, that is normal. Check to make sure it is there by calling for the type of the "my_dist" object.

```python
type(my_dist)
```

The result should say it is an nltk probability distribution. It doesn't matter too much right now what it is, only that it worked. We can now plot this with the matplotlib function, `plot`. We want to plot the first 50 entries of the my_dist object, but we don't want it to be cumulative. (If we were working with financial data, we might want cumulative.)

```python
my_dist.plot(50,cumulative=False)
```

We've made a nice image here, but it might be easier to comprehend as a list. Because this is a special probability distribution object we can call the "most common" on this, too. Let's find the twenty most common words:

```python
my_dist.most_common(20)
```

What about if we are interested in a list of specific words—perhaps to identify texts that have biblical references. Let's make a (short) list of words that might suggest a biblical reference and see if they appear in *Moby Dick*. Set this list equal to a variable:

```python
b_words = ['god', 'apostle', 'angel']
```

Then we will loop through the words in our cleaned corpus, and see if any of them are in our list of biblical words. We'll then save into another list just those words that appear in both.

```python
my_list = []
for word in b_words:
    if word in text1_clean:
        my_list.append(word)
    else:
        pass
```		

And then we will print the results.

```python
print(my_list)
```

You can obviously do this with much larger lists and even compare entire novels if you wish, though it would take a while with this approach. You can use this to get similarity measures and answer related questions. 


[<<< Previous](built-in.md) | [Next >>>](make_corpus.md)
