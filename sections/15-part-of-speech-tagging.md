← [Make Your Own Corpus (continued)](14-make-your-own-corpus-(continued).md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Start](../README.md) ↺

---

# 15. Part-of-Speech Tagging

_Note that we are going to use the pre-cleaned, `dq_text` object for this section._

POS (Part-of-Speech) tagging is going through a text and identifying which part of speech each word belongs to (i.e., Noun, Verb, or Adjective). Every word belongs to a part of speech, but some words can be confusing.

- Floyd is happy.
- Happy is a state of being.
- Happy has five letters.
- I'm going to Happy Cat tonight.

Therefore, part of speech is as much related to the word itself as its relationship to the words around it. A good part-of-speech tagger takes this into account, but there are some impossible cases as well:

- Wanda was entertaining last night.

Part of Speech tagging can be done very simply: with a very small _tag set_, or in a very complex way: with a much more elaborate tag set. We are going to implement a compromise, and use a neither small nor large tag set, the [Penn Tree Bank POS Tag Set](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html).

This is the tag set that is pre-loaded into NLTK. When we call the tagger, we expect it to return an object with the word and the tag associated. Because POS tagging is dependent upon the stop words, we have to use a text that includes the stop words. Therefore, we will go back to using the `dq_text` object for this section. Let's try it out. Type:

```python
dq_tagged = nltk.pos_tag(dq_text)
```

Let's inspect what we have:

```python
print(dq_tagged[:10])
```

This is a list of ordered _tuples_. The Python native type _tuple_ is similar to a list, but can't be changed once it is created. They are also denoted with parentheses, rather than square brackets. Each element in the list is a tuple—or a pairing—consisting of `(word, POS-tag)`. This is great, but it is very detailed. I would like to know how many nouns, verbs, and adjectives I have.

First, I'll make an empty dictionary to hold my results. (If you don't know what a dictionary is and how they work, you can check a quick explanation [here](https://realpython.com/python-dicts/).) After that, I will go through this list of tuples and count the number of times each tag appears. Every time I encounter a new tag, I'll add it to a dictionary and then increment by one every time I encounter that tag again. Let's see what that looks like in code:

```python
tag_dict = {}

# For every word/tag pair in my list,
for (word, tag) in dq_tagged:
    if tag in tag_dict:
        tag_dict[tag]+=1
    else:
        tag_dict[tag] = 1
```

Now let's see what we got:

```python
tag_dict
```

This would be better with some order to it, but dictionaries are made to be unordered. When we google "sort dictionaries python" we find a solution in our great friend [_Stack Overflow_](https://stackoverflow.com/a/613218). Even though we cannot sort a dictionary, we can get a representation of a dictionary that is sorted.

Don't worry too much about understanding the following code, as it uses things we have not discussed, and are out of the scope of this course. It is useful to learn to reuse pieces of code even when we don't fully understand them.

Now let's do it and find out what the most common tag is.

```python
tag_dict_sorted = sorted(tag_dict.items(),
			 reverse=True,
			 key=lambda kv: kv[1])
```

Now let's check out what we have: 

```python
print(tag_dict_sorted)
```

Your result should show that NN is the most common tag. We can look up what NN means in the [Penn Tree Bank](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html). Looks like NN is a Noun, singular or mass. Great! This information will likely help us with genre classification, or identifying the author of a text, or a variety of other functions.

## Evaluation

Which of the following are correct?
- POS tagging does not work well with stop words, therefore you should always clean your text from stop words before using it.
- Tuples are like lists, but you can't change their value once created.*
- `nltk.pos_tag` returns tuples of two values, the first being the word, and the second the tag.*

## Keywords

Do you remember the glossary terms from this section?

- [part-of-speech (POS) tagging](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/part-of-speech.md)
- [Dictionaries](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/dictionaries.md)
- [Tuples](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/tuples.md)

---

← [Make Your Own Corpus (continued)](14-make-your-own-corpus-(continued).md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Start](../README.md) ↺