← [Searching for Words](04-searching-for-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Types vs. tokens](06-types-vs.-tokens.md) →

---

# 5. Positioning Words

In many ways, `concordance` and `similar` are heightened word searches that tell us something about what is happening near the target words. Another metric we can use is to visualize where the words appear in the text. In the case of _Moby Dick_, we want to compare where "whale" and "monster" appear throughout the text. In this case, the text is functioning as a list of words, and will make a mark where each word appears, offset from the first word. We will _pass_ this _function_ a _list_ of _strings_ to plot. In the next cell, type:

```python
text1.dispersion_plot(["whale", "monster"])
```

A graph should appear with a tick mark everywhere that "whale" appears and everywhere that "monster" appears. Knowing the story, we can interpret this graph and align it to what we know of how the narrative progresses, helping us develop a visual of the story — where the whale goes from being a whale to being a monster to being a whale again. If we did not know the story, this could give us hints of the narrative arc.

## Challenge

Try this with `text2`, _Sense and Sensibility_, [as we saw here](#downloading-the-corpus). Some relevant words are "marriage," "love," "home," "mother," "husband," "sister," and "wife." Pick a few to compare. You can compare an unlimited number, but it's easier to read a few at a time. (Note that the comma in our writing here is _inside_ the quotation mark, because that is how proper English grammar works. However, in Python, you would have to put commas _outside_ of the quotation marks to create a _list_.)

NLTK has many more functions built-in, but some of the most powerful functions are related to cleaning, part-of-speech tagging, and other stages in the text analysis pipeline (where the pipeline refers to the process of loading, cleaning, and analyzing text).

## Solution

```python
text2.dispersion_plot(["love", "marriage"])
```

```python
text2.dispersion_plot(["husband", "wife"])
```

## Evaluation

Check all sentences below that are correct:
- You can get a visual representation of ocurrences of a word with the `dispersion_plot` method.*
- The `dispersion_plot` method allows you to input a list of strings, as long as you split them with commas.*
- Contrary to grammar rule, in a list of strings, the commas must come outside of the quotation marks.*

---

← [Searching for Words](04-searching-for-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Types vs. tokens](06-types-vs.-tokens.md) →