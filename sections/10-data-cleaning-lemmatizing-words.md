← [Data Cleaning: Removing Stop Words](09-data-cleaning-removing-stop-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Data cleaning: Stemming Words](11-data-cleaning-stemming-words.md) →

---

# 10. Data cleaning: Lemmatizing Words

Now that we've removed the stop words from our corpus, the next step is to stem or lemmatize the remaining words. This means that we will strip off the grammatical structure from the words. For example, `cats ⭢ cat`, and `walked ⭢ walk`. If that was all we had to do, we could stem the corpus and achieve the correct result, because stemming (as the name implies) really just means cutting off affixes to find the root (or the stem). Very quickly, however, this gets complicated, such as in the case of `men ⭢ man` and `sang ⭢ sing`. Lemmatization deals with this by looking up the word in a reference and finding the appropriate root (though note that this still is not entirely accurate). Lemmatization, therefore, takes a relatively long time, since each word must be looked up in a reference. NLTK comes with pre-built stemmers and lemmatizers.

We will use the WordNet Lemmatizer from the NLTK Stem library, so let's import that now:

```python
from nltk.stem import WordNetLemmatizer
```

Because of the way that it is written "under the hood," an instance of the lemmatizer needs to be called. We know this from reading [the docs](https://www.nltk.org/).

```python
wordnet_lemmatizer = WordNetLemmatizer()
```

Let's quickly see what lemmatizing does.

```python
wordnet_lemmatizer.lemmatize("children")
```

Now try this one:

```python
wordnet_lemmatizer.lemmatize("better")
```

It didn't work, but...

```python
wordnet_lemmatizer.lemmatize("better", pos='a')
```

... sometimes we can get better results if we define a specific part of speech(pos). "a" is for "adjective", as we learned [here](http://www.nltk.org/_modules/nltk/corpus/reader/wordnet.html).

Now we will lemmatize the words in the list.

```python
text1_clean = []
for t in text1_stops:
    t_lem = wordnet_lemmatizer.lemmatize(t)
    text1_clean.append(t_lem)
```

And again, there is a faster version for you to use once you feel comfortable with list comprehensions:

```python
text1_clean = [wordnet_lemmatizer.lemmatize(t) for t in text1_stops]
```

## Verifying Clean List Contents

Let's check now to see the length of our final, cleaned version of the data, and then check the unique set of words. Notice how we will use the `print` function this time. Jupyter Notebook does print commands without the `print` function, but it will only print one thing per cell (the last command), and we wanted to print two different things:

```python
print(len(text1_clean))
print(len(set(text1_clean)))
```

If everything went right, you should have the same length as before, but a smaller number of unique words. That makes sense since we did not remove any word, we only changed some of them.

Now if we were to calculate lexical density, we would be looking at how many word stems with semantic content are represented in _Moby Dick_, which is a different question than the one in our first analysis of lexical density.

Why don't you try that by yourself? Try to remember how to calculate lexical density without looking back first. It is ok if you have forgotten.

Now let's have a look at the words Melville uses in _Moby Dick_. We'd like to look at all of the _types_, but not necessarily all of the _tokens._ We will order this set so that it is in an order we can handle. In the next cell, type:

```python
sorted(set(text1_clean))[:30]
```

`sorted` combined with `set` should give us a list of all the unique words in _Moby Dick_ in alphabetical order, but we only want to see the first ones. Notice how there are some words we wouldn't have expected, such as 'abandon', 'abandoned', 'abandonedly', and 'abandonment'. This process is far from perfect, but it is useful. However, depending on your goal, a different process, like _stemming_ might be better.

## Evaluation

Check all sentences below that are correct:
- Stemming and lemmatizing are different forms of reducing word variations to their roots.*
- `sorted(set(list_of_strings))` returns the unique items of `list_of_strings` in alphabetical order.*

## Keywords

Do you remember the glossary terms from this section?

- [Lemmatization](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/lemmatization.md)
- [Lexical Density](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/lexical-density.md)

---

← [Data Cleaning: Removing Stop Words](09-data-cleaning-removing-stop-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Data cleaning: Stemming Words](11-data-cleaning-stemming-words.md) →