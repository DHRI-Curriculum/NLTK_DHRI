↻ [Start](../README.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Cleaning and Normalizing](02-cleaning-and-normalizing.md) →

---

# 1. Text as Data

When we think of "data," we often think of numbers, things that can be summarized, statisticized, and graphed. Rarely when I ask people "what is data?" do they respond "_Moby Dick_." And yet, more and more, text is data. Whether it is _Moby Dick_, or every romance novel written since 1750, or today's newspaper or twitter feed, we are able to transform written (and spoken) language into data that can be quantified and visualized. That has been done for a while, but now we can do it in a much larger scale, in a much faster way.

## Corpora

The first step in gathering insights from texts is to create a **corpus**. A corpus is a collection of texts that are somehow related to each other. For example, the [Corpus of Contemporary American English](https://corpus.byu.edu/coca/), [Donald Trump's Tweets](http://www.trumptwitterarchive.com/), [text messages](https://byts.commons.gc.cuny.edu/) sent by bilingual young adults, [digitized newspapers](https://chroniclingamerica.loc.gov/newspapers/), or [books](https://www.gutenberg.org/) in the public domain are all corpora. There are infinitely many corpora, and, sometimes, you will want to make your own—that is, one that best fits your research question.

The route you take from here will depend on your research question. Let's say, for example, that you want to examine gender differences in writing style. Based on previous linguistic research, you hypothesize that male-identified authors use more definitives than female-identified. So you collect two corpora—one written by men, one written by women—and you count the number of *the*s, *this*s, and *that*s compared to the number of *a*s, *an*s, and *one*s. Maybe you find a difference, maybe you don't. We can already see that this is a relatively crude way of going about answering this question, but it is a start.

Keep in mind that, oftentimes our analysis of gender assumes pre-existing gender roles that reproduce gender as a binary system. Some digital humanists have pointed out that, if gender is binary, then the relation between male and female will likely be one of opposition. As [Laura Mandell](https://dhdebates.gc.cuny.edu/read/untitled-f2acf72c-a469-49d8-be35-67f9ac1e3a60/section/5d9c1b63-7b60-42dd-8cda-bde837f638f4#ch01) says, the categories of "male" and "female" are socially constructed, and quantitative analysis practitioners should avoid jumping to conclusions about "male" and "female" styles of thinking and writing "as if the M/F terms were simple pointers to an unproblematic reality, transparently referential and not discursively constituted."

There has been some research about how the [linguistic complexity of written language](http://science.sciencemag.org/content/sci/331/6014/176.full.pdf) in long-form pieces (i.e., books, articles, letters, etc.) has decreased over time. Simply put, people today use shorter sentences with fewer embedded clauses and complex tense constructions than people did in the past. (Note that this is not necessarily a bad or good thing.) Based on this research, we want to know if short-form platforms are emblematic of the change (we predict that they are based on our own experience with short-form platforms like email and Twitter). One way to do this would be to use Part-of-Speech tagging. Part-of-Speech (POS) tagging is a way to identify the category of words in a given text.

For example, the sentence:

> I like the red bicycle.

has one pronoun, one verb, one determiner, one adjective, and one noun.

> (**I** : Pronoun), (**like** : Verb), (**the** : Determiner), (**red** : Adjective), (**bicycle** : Noun)

NLTK uses the [Penn Tree Bank Tag Set](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html). This is a very detailed tag list that goes far beyond just nouns, verbs, and adjectives, but gives insight into different types of nouns, prepositions, and verbs as well. Virtually all POS taggers will create a list of (word, POS) pairs. If newspaper articles have a higher ratio of function words (prepositions, auxiliaries, determiners, etc.) to semantic words (nouns, verbs, adjectives), than tweets, then we have one piece of evidence supporting our hypothesis. It's important to note here that we must use either ratios or otherwise normalized data (in the sense that raw numbers will not work). Because of the way that language works (function words are often repeated, for example), a sample of 100 words will have more unique words than a sample of 1,000. Therefore, to compare different data types (articles vs. tweets), this fact should be taken into account.

## A note about languages

Even though in this workshop we will use the English language in the examples, NLTK does support many other languages, due to amazing contributions from the Python Text Analysis community. The support, however, varies according to the desired task. Not all functions and tools will be available for all the supported languages. The good news is that the available tools keep growing in quantity and quality.

If you are planning to work with other languages than English, you will have to figure out what tools are available and how to use them. Unfortunately, it is not something that can be fully explained in a general workshop like this. Some times it is as easy as changing `stopwords.words("English")` (a command we will teach you later) to `stopwords.words("Spanish")`. Ocasionally, it will be harder than that. A search engine (Google, DuckDuckGo...) will be your best friend here.

## Evaluation

Check all sentences below that are correct:

- A text is not data in itself, but can produce data if converted into numbers.
- Part-of-Speech (POS) tagging can help identifying verbs, adjectives and nouns in a text.*
- A corpus is any collection of texts, independently of being related to each other or not.

## Keywords

Do you remember the glossary terms from this section?

- [NLTK](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/nltk.md)

---

↻ [Start](../README.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Cleaning and Normalizing](02-cleaning-and-normalizing.md) →