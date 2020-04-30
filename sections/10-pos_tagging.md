[<<< Previous](09-make_corpus.md) | [Next >>>](11-conclusion.md)

# Part-of-Speech Tagging

*Note that we are going to use the pre-cleaned, `dq_text` object for this section.*

POS tagging is going through a text and identifying which part of speech each word belongs to (i.e., Noun, Verb, or Adjective). Every word belongs to a part of speech, but some words can be confusing.

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

This is a list of ordered tuples. (A tuple is like two variables connected to one another, that can't be changed once it is created.) Each element in the list is a pairing of `(word, POS-tag)`. (Tuples are denoted with parentheses, rather than square brackets.) This is great, but it is very detailed. I would like to know how many Nouns, Verbs, and Adjectives I have.

First, I'll make an empty dictionary to hold my results. Then I will go through this list of tuples and count the number of times each tag appears. Every time I encounter a new tag, I'll add it to a dictionary and then increment by one every time I encounter that tag again. Let's see what that looks like in code:

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

This would be better with some order to it, so let's organize our dictionary to find out what the most common tag is. We need the OrderedDict function. Just like with the url.request library, the 'collections' package comes built-in with Python, but needs to be imported to be used. We will only need the `OrderedDict`, so that's all we will import. Then we will pass the `OrderedDict` function our dictionary with a set of parameters, to tell it exactly how we want it to be ordered, and in which direction. We know what to do for this function because we [read the docs](https://docs.python.org/3/library/collections.html#collections.OrderedDict).

```python
from collections import OrderedDict
tag_dict = OrderedDict(sorted(tag_dict.items(), key=lambda t: t[1], reverse=True))
```

Now check out what we have:

```python
tag_dict
```

It looks like NN is the most common tag, we can look up what that is back at the [Penn Tree Bank](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html). Looks like that is a Noun, singular or mass. Great! This information will likely help us with genre classification (as you will do in the [Machine Learning tutorial](https://www.github.com/DHRI-Curriculum/machine-learning)), or identifying the author of a text, or a variety of other functions.

[<<< Previous](09-make_corpus.md) | [Next >>>](11-conclusion.md)
