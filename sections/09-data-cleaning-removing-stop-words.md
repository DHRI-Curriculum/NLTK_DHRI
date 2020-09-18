← [Lexical density](08-lexical-density.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Data cleaning: Lemmatizing Words](10-data-cleaning-lemmatizing-words.md) →

---

# 9. Data Cleaning: Removing Stop Words

Thus far, we have been asking questions that take stop words and grammatical features into account. For the most part, we want to exclude these features since they don't actually contribute very much semantic content to our models. Therefore, we will:

1. Remove capitalization and punctuation (we've already done this).
2. Remove stop words.
3. Lemmatize (or stem) our words, i.e. "jumping" and "jumps" become "jump."

We already completed step one, and are now working with our `text1_tokens`. Remember, this variable, `text1_tokens`, contains a list of strings that we will work with. We want to remove the stop words from that list. The NLTK library comes with fairly comprehensive lists of stop words for many languages. Stop words are function words that contribute very little semantic meaning and most often have grammatical functions. Usually, these are function words such as determiners, prepositions, auxiliaries, and others.

To use NLTK's stop words, we need to import the list of words from the corpus. (We could have done this at the beginning of our program, and in more fully developed code, we would put it up there, but this works, too.) In the next cell, type:

```python
from nltk.corpus import stopwords
```

We need to specify the English list, and save it into its own variable that we can use in the next step:

```python
stops = stopwords.words('english')
```

Now let's take a look at those words:

```python
print(stops)
```

Now we want to go through all of the words in our text, and if that word is in the stop words list, remove it from our list. Otherwise, we want it to skip it. (The code below is slow, so it may take some time to process). The way we can write this in Python is:

```python
text1_stops = []
for t in text1_tokens:
    if t not in stops:
        text1_stops.append(t)
```

A faster option, if you are feeling bold, would be using list comprehension:

```python
text1_stops = [t for t in text1_tokens if t not in stops]
```

To check the result:

```python
print(text1_stops[:30])
```

## Verifying List Contents

Now that we removed our stop words, let's see how many words are left in our list:

```python
len(text1_stops)
```

You should get a much lower number.

For reference, let's also check how many unique words there are. We will do this by making a set of words. Sets are the same in Python as they are in math, they are all of the unique words rather than all the words. So, if "whale" appears 200 times in the list of words, it will only appear once in the set.

```python
len(set(text1_stops))
```

## Evaluation

Check all sentences below that are correct:
- Stop words are words that usually don't contribute with much semantic content, like prepositions, determiners, etc.*
- To use stop words we need to import them from the nltk corpus, using the following code: `import stopwords from nltk.corpus`
- List comprehensions are faster ways of iterating and creating lists when compared with for loops.*

## Keywords

Do you remember the glossary terms from this section?

- [Stop Words](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/stop-words.md)

---

← [Lexical density](08-lexical-density.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Data cleaning: Lemmatizing Words](10-data-cleaning-lemmatizing-words.md) →