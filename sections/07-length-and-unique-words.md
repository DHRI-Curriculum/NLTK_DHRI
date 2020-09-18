← [Types vs. Tokens](06-types-vs.-tokens.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Lexical Density](08-lexical-density.md) →

---

# 7. Length and Unique Words

Great! Now `text1_tokens` is a list of all of the tokens in our corpus, with the punctuation removed, and all the words in lowercase. Let's check it:

```python
text1_tokens.count("whale")
```

And now we have 1226 tokens for "whale", which is the exact some of the counts we did before. To double check, count "Whale" and "WHALE" again and you should see no results for them.

Now we want to know how many words there are in our corpus—that is, how many tokens in total. Therefore, we want to ask, "What is the length of that list of words?" Python has a built-in `len` function that allows you to find out the length of many types. Pass it a list, and it will tell you how many items are in the list. Pass it a string, and it will tell you how many characters are in the string. Pass it a dictionary, and it will tell you how many items are in the dictionary. In the next cell, type:

```python
len(text1_tokens)
```

Just for comparison, check out how many words were in `text1`—before we removed the punctuation and the numbers.

```python
len(text1)
```

We see there are over 218,000 words in _Moby Dick_ (including metadata). But this is the number of words total—we want to know the number of unique words. That is, we want to know how many _types_, not just how many tokens.

In order to get unique words, rather than just all words in general, we will make a **set** from the list. A `set` in Python works just like it would [in math](https://en.wikipedia.org/wiki/Set_(mathematics)), it's all the unique values, with any duplicate items removed.

So let's find out the length of our set. just like in math, we can also nest our functions. So, rather than saying `x = set(text1_tokens)` and then finding the length of "x", we can do it all in one step.

```python
len(set(text1_tokens))
```

---

← [Types vs. Tokens](06-types-vs.-tokens.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Lexical Density](08-lexical-density.md) →