← [Positioning Words](05-positioning-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Length and Unique Words](07-length-and-unique-words.md) →

---

# 6. Types vs. Tokens

We will now turn our attention away from the NLTK library and work with our text using the _built-in Python functions_, the ones that come included with the Python language, rather than the NLTK library. (This difference is relevant because built-in python functions will work with any list of strings, while some of the functions that are specific to the NLTK library will require you to make your text "nltk ready". Don't worry about that now, we will show you how to do it later in this workshop).

First, let's find out how many times a given word appears in the corpus. In this case (and all cases going forward), our text will be treated as a list of words. Therefore, we will use the `count` function. We could just as easily do this with a text editor, but performing this in Python allows us to save it to a variable and then utilize this statistic in other calculations (for example, if we want to know what percentage of words in a corpus are 'lol', we would need a count of the 'lol's). In the next cell, type:

```python
text1.count("whale")
```

We see that "whale" occurs 906 times, but that seems a little low. Let's check the same thing, but now for "Whale" and "WHALE":

```python
text1.count("Whale")
```

```python
text1.count("WHALE")
```

What is clear here is that the `count` method is case-sensitive.
"Whale" with a capital "W" appears 282 times, and "WHALE" another 38 times. Depending on the type of analysis, this distinction can be a problem, and we might want "whale", "Whale" and "WHALE" to be collapsed into one single word. We will deal with that in a moment. For the time being, we will accept that we have three different entries for "whale."

This gets at a distinction between **type** and **token**. "Whale" and "whale" are different types (as of now) because they do not match identically. Every instance of "whale" in the corpus is another **token**—it is an instance of the type, "whale." Therefore, there are 906 tokens of "whale" in our corpus, 282 tokens of "Whale" and 38 tokens of "WHALE".

But that's not what we want. Let's fix this by making all of the words lowercase. We will make a new list of words, and call it `text1_tokens`. We will fill this list with all the words in `text1`, but in their lowercase form. Python has a built-in function, `lower()` that takes all letters and makes them lowercase. In this same step, we are going to do a kind of tricky move, and only keep the words that are alphabetical and pass over anything that is punctuation or numbers. There is a built-in function, `isalpha()`, that will allow us to save only those words that are made of letters. If `isalpha()` is true, we'll make the word lowercase, and keep the word. If not, we'll pass over it and move to the next one.

Type the following code into a new cell in your notebook. Pay special attention to the indentation, which must appear as below. (Note that in Jupyter Notebook, indentation usually comes automatically. If not, make sure to type the <kbd>space</kbd> key 4 times)

```python
text1_tokens = []
for t in text1:
    if t.isalpha():
        t = t.lower()
        text1_tokens.append(t)
```

If everything went right, you should get no output. Remember the "silent success?"

Another way to perform the same action more tersely is to use what's called a [list comprehension](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions). A list comprehension is a shorter, faster way to write a for-loop. It is syntactically a little more difficult to read (for a human), but, in this case, it's much faster to process.

Don't worry too much about understanding the syntax of list comprehensions right now, just try to recognize on it the elements you've seen in the for loop. For every example, we will show both the for loop and list comprehension options so you can slowly get used to the latter.

```python
text1_tokens = [t.lower() for t in text1 if t.isalpha()]
```

## Take a Breath

Let's take a breath, because this was a difficulty spike. For loops are weird and not super intuitive. It usually takes some time for us to get used to them.

I suggest going back to the loop above, review it, try to understand why all indentations are where they are.

Feel like you understand it? Try deleting it and writing the loop yourself without looking at this guide.

You can also copy the whole loop to a new jupyter notebook cell and play around with it. What happens when you change the order of the commands? How about the indentation? Don't be afraid to break it.

If you feel like you are done playing with the loop, time to move to the next section to see the results.

## Evaluation

Check all sentences below that are correct:
- "Whale", "WHALE", and "whale" are all different tokens of the same type.
- The `lower()` method returns the lowercase form of all of the alphabetical characters in a string.*
- The `isalpha()` method transforms integers in alphabetical strings.
- The `append()` method adds an item to the end of the list.*

## Token

Do you remember the glossary terms from this section?

- [Token](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/token.md)
- [Tokenizing](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/tokenizing.md)
- [Type](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/type.md)

---

← [Positioning Words](05-positioning-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Length and Unique Words](07-length-and-unique-words.md) →