[<<< Previous](overview.md) | [Next >>>](data_cleaning.md)

# Text as Data

When we think of "data," we often think of numbers, things that can be summarized, statisticized, and graphed. Rarely when I ask people "what is data?" do they respond "*Moby Dick*." And yet, more and more, text is data. Whether it is Moby Dick, or every romance novel written since 1750, or today's newspaper or twitter feed, we are able to transform written (and spoken) language into data that can be quantified and visualized. 

## Corpora

The first step in gathering insights from texts is to create a **corpus**. A corpus is a collection of texts that are somehow related to each other. For example, the [Corpus of Contemporary American English](https://corpus.byu.edu/coca/), [Donald Trump's Tweets](http://www.trumptwitterarchive.com/), [digitized newspapers](https://chroniclingamerica.loc.gov/newspapers/), or [books](https://www.gutenberg.org/) in the public domain are all corpora. There are infinitely many corpora, and, sometimes, you will want to make your own—that is, one that best fits your research question.

The route you take from here will depend on your research question. Let's say, for example, that you want to examine gender differences in writing style. Based on previous linguistic research, you hypothesize that male-identified authors use more definitives than female-identified. So you collect two corpora—one written by men, one written by women—and you count the number of *the*s, *this*s, and *that*s compared to the number of *a*s, *an*s, and *one*s. Maybe you find a difference, maybe you don't. We can already see that this is a relatively crude way of going about answering this question, but it is a start. (More likely, you'd use a *supervised classification task*, which you will learn about in the Machine Learning Tutorial.)

There has been some research about how the [linguistic complexity of written language](http://science.sciencemag.org/content/sci/331/6014/176.full.pdf) in long-form pieces (i.e., books, articles, letters, etc.) has decreased over time. Simply put, people today use shorter sentences with fewer embedded clauses and complex tense constructions than people did in the past. (Note that this is not necessarily a bad or good thing.) Based on this research, we want to know if short-form platforms are emblematic of the change (we predict that they are based on our own experience with short-form platforms like email and Twitter). One way to do this would be to use Part-of-Speech tagging. Part-of-Speech (POS) tagging is a way to identify the category of words in a given text.

For example, the sentence: 

> I like the red bicycle.

has one pronoun, one verb, one determiner, one adjective, and one noun.

> (I : Pronoun), (like : Verb), (the : Determiner), (red : Adjective), (bicycle : Noun) 

NLTK uses the [Penn Tree Bank Tag Set](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html). This is a very detailed tag list that goes far beyond just nouns, verbs, and adjectives, but gives insight into different types of nouns, prepositions, and verbs as well. Virtually all POS taggers will create a list of (word, POS) pairs. If newspaper articles have a higher ratio of function words (prepositions, auxiliaries, determiners, etc.) to semantic words (nouns, verbs, adjectives), than tweets, then we have one piece of evidence supporting our hypothesis. It's important to note here that we must use either ratios or otherwise normalized data (in the sense that raw numbers will not work). Because of the way that language works (function words are often repeated, for example), a sample of 100 words will have more unique words than a sample of 1,000. Therefore, to compare different data types (articles vs. tweets), this fact should be taken into account.

[<<< Previous](overview.md) | [Next >>>](data_cleaning.md)
