← [Make Your Own Corpus](13-make-your-own-corpus.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Part-of-Speech Tagging](15-part-of-speech-tagging.md) →

---

# 14. Make Your Own Corpus (continued)

Now we are going to transform that string into a text that we can perform NLTK functions on. Since we already imported nltk at the beginning of our program, we don't need to import it again, we can just use its functions by specifying `nltk` before the function. The first step is to tokenize the words, transforming the giant string into a list of words. A simple way to do this would be to split on spaces, and that would probably be fine, but we are going to use the NLTK tokenizer to ensure that edge cases are captured (i.e., "don't" is made into 2 words: "do" and "n't"). In the next cell, type:

```python
don_tokens = nltk.word_tokenize(don)
```

You can check out the type of `don_tokens` using the `type()` function to make sure it worked—it should be a list. Let's see how many words there are in our novel:

```python
len(don_tokens)
```

Since this is a list, we can look at any slice of it that we want. Let's inspect the first ten words:

```python
don_tokens[:10]
```

That looks like metadata—not what we want to analyze. We will strip this off before proceeding. If you were doing this to many texts, you would want to use [Regular Expressions](https://regexone.com/). Regular Expressions are an extremely powerful way to match text in a document. However, we are just using this text, so we could either guess, or cut and paste the text into a text reader and identify the position of the first content (i.e., how many words in is the first word). That is the route we are going to take. We found that the content begins at word 320, so let's make a slice of the text from word position 320 to the end.

```python
dq_text = don_tokens[320:]
```

Now print the first 30 words to see if it worked:

```python
print(dq_text[:30]
```

Finally, if we want to use the NLTK specific functions:

- `concordance`
- `similar`
- `dispersion_plot`
- or others from the [NLTK book](https://www.nltk.org/book/)

we would have to make a specific NLTK `Text` object.

```python
dq_nltk_text = nltk.Text(dq_text)
```

And we could check that it worked by running:

```python
type(dq_nltk_text)
```

But if we only need to use the built-in Python functions, we can just stick with our list of words in `dq_text`.

## Challenge

Using the `dq_text` variable:

- Remove the stop words
- Remove punctuation
- Remove capitalization
- Lemmatize the words

If you want to spice your challenge up, do the first three operations _in a single if statement_. Google "python nested if statements" for examples.

## Solution

1. Lowercase, remove punctuation and stop words:

    ```python
    dq_clean = []
    for word in dq_text:
        if word.isalpha():
            if word.lower() not in stops:
                dq_clean.append(word.lower())
    print(dq_clean[:50])
    ```

2. Lemmatize:

    ```python
    from nltk.stem import WordNetLemmatizer
    wordnet_lemmatizer = WordNetLemmatizer()

    dq_lemmatized = []
    for t in dq_clean:
        dq_lemmatized.append(wordnet_lemmatizer.lemmatize(t))
    ```

## Evaluation

Check all sentences below that are correct:
- `urlopen` can save the contents of a webpage into a variable.*
- To use NLTK functions on a string, we can transform it into a NLTK Text object.*
- NLTK let's you tokenize (split) a giant string into a list of substrings, considering punctuations and edge cases like `don't`.*

## Keywords

Do you remember the glossary terms from this section?

- [Metadata](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/metadata.md)
- [Regular Expressions](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/regular-expressions.md)

---

← [Make Your Own Corpus](13-make-your-own-corpus.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Part-of-Speech Tagging](15-part-of-speech-tagging.md) →