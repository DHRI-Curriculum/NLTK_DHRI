← [Using the NLTK Corpus](03-using-the-nltk-corpus.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Positioning Words](05-positioning-words.md) →

---

# 4. Searching for Words

Let's start by analyzing _Moby Dick_, which is `text1` for NLTK.

The first function we will look at is `concordance`. "Concordance" in this context means the characters on either side of the word. Our text is behaving like one giant string, so concordance will just count the number of characters on either side. By default, this is 25 characters on either side of our target word (including spaces), but [you can change that if you want](http://www.nltk.org/_modules/nltk/text.html#Text.concordance).

In the Jupyter Notebook, type:

```python
text1.concordance("whale")
```

The output shows us the 25 characters on either side of the word "whale" in _Moby Dick_. Let's try this with another word, "love." Just replace the word "whale" with "love," and we get the contexts in which Melville uses "love" in _Moby Dick_. `concordance` is used (behind the scenes) for several other functions, including `similar` and `common_contexts`.

Let's now see which words appear in similar contexts as the word "love." NLTK has a built-in function for this as well: `similar`.

```python
text1.similar("love")
```

Behind the scenes, Python found all the contexts where the word "love" appears. It also finds similar environments, and then what words were common among the similar contexts. This gives a sense of what other words appear in similar contexts. This is somewhat interesting in itself, but more interesting if we compare it to something else. Let's take a look at another text. What about _Sense and Sensibility_ (`text2`)? Let's see what words are similar to "love" in Jane Austen's writing. In the next cell, type:

```python
text2.similar("love")
```

We can compare the two and see immediately that Melville and Austen use the word "love" differently.

## Investigating "lol"

Let's expand from novels for a minute and take a look at the NLTK Chat Corpus. In chats, text messages, and other digital communication platforms, "lol" is exceedingly common. We know it doesn't simply mean "laughing out loud"—maybe the `similar` function can provide some insight into what it does mean.

```python
text5.similar("lol")
```

The resulting list is a lot of greetings, indicating that "lol" probably has more of a [phatic function](https://www.oxfordreference.com/view/10.1093/oi/authority.20110803100321840). Phatic language is language primarily for communicating social closeness. Phatic words stand in contrast to semantic words, which contribute meaning to the utterance.

If you are interested in this type of analysis, take a look at the `common_contexts` function in the [NLTK book](https://www.nltk.org/book/) or in the [NLTK docs](https://www.nltk.org/).

## Evaluation

Check all sentences below that are correct:
- The similar method brings a list of words that are similiar in writing, but not necessarily in meaning, like "whale" and "while".
- Using the `concordance` method with a specific word, such as "whale", returns the words that surround "whale" in different sentences, helping us to get a glimpse of the contexts in which the word "whale" shows up.*

## Keywords

Do you remember the glossary terms from this section?

- [Concordance](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/concordance.md)
- [Phatic Language](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/phatic-language.md)

---

← [Using the NLTK Corpus](03-using-the-nltk-corpus.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Positioning Words](05-positioning-words.md) →