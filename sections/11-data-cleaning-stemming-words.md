← [Data cleaning: Lemmatizing Words](10-data-cleaning-lemmatizing-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Data Cleaning: Results](12-data-cleaning-results.md) →

---

# 11. Data cleaning: Stemming Words

The code to implement this and view the output is below:

```python
from nltk.stem import PorterStemmer
porter_stemmer = PorterStemmer()
```

The Porter is the most common Stemmer. Let's see what stemming does to words and compare it with lemmatizers:

```python
print(porter_stemmer.stem('berry'))
print(porter_stemmer.stem('berries'))
print(wordnet_lemmatizer.lemmatize('berry'))
print(wordnet_lemmatizer.lemmatize('berries'))
```

Stemmer doesn't look so good, right? But how about checking how stemmer handles some of the words that our lemmatized "failed" us?

```python
print(porter_stemmer.stem('abandon'))
print(porter_stemmer.stem('abandoned'))
print(porter_stemmer.stem('abandonedly'))
print(porter_stemmer.stem('abandonment'))
```

Still not perfect, but a bit better. So the question is, how to choose between stemming and lemmatizing? As many things in text analysis, that depends. The best way to go is experimenting, seeing the results and chosing the one that better fits your goals.

As a general rule, stemming is faster while lemmatizing is more accurate (but not always, as we just saw). For academics, usually the choice goes for the latter.

Anyway, let's stem our text with the Porter Stemmer:

```python
t1_porter = []
for t in text1_clean:
    t_stemmed = porter_stemmer.stem(t)
    t1_porter.append(t_stemmed)
```

Or, if we want a faster way:

```python
t1_porter = [porter_stemmer.stem(t) for t in text1_clean]
```

And let's check the results:

```python
print(len(set(t1_porter)))
print(sorted(set(t1_porter))[:30])
```

A very different list of words is produced. This list is shorter than the list produced by the lemmatizer, but is also less accurate, and some of the words will completely change their meaning (like 'berry' becoming 'berri').

## Evaluation

Check all sentences below that are correct:
- Both Stemming and Lemmatizing are far from perfect, so they must be used with caution.*
- There is no obvious best choice between Stemmers and Lemmatizers, so the best way to go is experimenting and seeing what results better fit your goals.*

## Keywords

Do you remember the glossary terms from this section?

- [Stemming](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/stemming.md)

---

← [Data cleaning: Lemmatizing Words](10-data-cleaning-lemmatizing-words.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Data Cleaning: Results](12-data-cleaning-results.md) →