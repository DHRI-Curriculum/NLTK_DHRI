← [Length and Unique Words](07-length-and-unique-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Data Cleaning: Removing Stop Words](09-data-cleaning-removing-stop-words.md) →

---

# 8. Lexical Density

Now we can calculate the **lexical density**, the number of unique words per total words. [Statistical studies](https://pdfs.semanticscholar.org/c2a8/56959d7f5880c98ccd4cfeb4b4f5b7133ec7.pdf) have shown that lexical density is a good metric to approximate lexical diversity—the range of vocabulary an author uses. For our first pass at lexical density, we will simply divide the number of unique words by the total number of words:

```python
len(set(text1_tokens)) / len(text1_tokens)
```

If we want to use this metric to compare texts, we immediately notice a problem. Lexical density is dependent upon the length of a text and therefore is strictly a comparative measure. It is possible to compare 100 words from one text to 100 words from another, but because language is finite and repetitive, it is not possible to compare 100 words from one to 200 words from another. Even with these restrictions, lexical density is a useful metric in grade level estimations, [vocabulary use](http://www.mdpi.com/2226-471X/2/3/7) and genre classification, and a reasonable proxy for lexical diversity.

Let's take this constraint into account by working with only the first 10,000 words of our text. First we need to slice our list, returning the words in position 0 to position 9,999 (we'll actually write it as "up to, but not including" 10,000).

```python
text1_slice = text1_tokens[0:10000]
```

Now we can do the same calculation we did above:

```python
len(set(text1_slice)) / len(text1_slice)
```

This is a much higher number, though the number itself is arbitrary. When comparing different texts, this step is essential to get an accurate measure.

## Challenge

Let's compare the lexical density of _Moby Dick_ with _Sense and Sensibility_. Make sure to:

1. Make all the words lowercase and remove punctuation.
2. Make a slice of the first 10,000 words.
3. Calculate lexical density by dividing the length of the set of the slice by the length of the slice.

Remember to be aware of the ethical implications for the conclusions that we might draw about our data. What assumptions might we be reifying about these writers?

## Solution

```python
text2_tokens = []
for t in text2:
    if t.isalpha():
        t = t.lower()
        text2_tokens.append(t)

text2_slice = text2_tokens[0:10000]

len(set(text2_slice)) / len(text2_slice)
```

## Evaluation

Check all sentences below that are correct:
- The `len` method returns the length of the input, which can mean different things depending on its type. If it is a string, it will return the number of characters; if it is a list or dictionary, it will return the number of items.*
- The lexical density measures the number of unique words per total word, and it is an objective measure of writing quality.
- Comparing the lexical density between texts of different sizes can give a problematic result. A possible solution is to use list slice and compare parts of both texts of a similar size.*

---

← [Length and Unique Words](07-length-and-unique-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Data Cleaning: Removing Stop Words](09-data-cleaning-removing-stop-words.md) →