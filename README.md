![Header image for the Text Analysis workshop](https://raw.githubusercontent.com/DHRI-Curriculum/text-analysis/v2.0/_django-meta/header%403x.png)


Digital technologies have made vast amounts of text available to researchers, and this same technological moment has provided us with the capacity to analyze that text faster than humanly possible. The first step in that analysis is to transform texts designed for human consumption into a form a computer can analyze. Using Python and the Natural Language ToolKit (commonly called NLTK), this workshop introduces strategies to turn qualitative texts into quantitative objects. Through that process, we will present a variety of strategies for simple analysis of text-based data.

In this workshop, you will:

In this workshop, you will learn skills like:

- How to prepare texts for computational analysis, including strategies for transforming texts into numbers
- How to use NLTK methods such as `concordance` and `similar` 
- How to clean and standardize your data, including powerful tools such as stemmers and lemmatizers
- Compare frequency distribution of words in a text to quantify the narrative arc
- Understand stop words and how to remove them when needed.
- Utilize Part-of-Speech tagging to gather insights about a text
- Transform any document that you have (or have access to) in a .txt format into a text that can be analyzed computationally
- How to tokenize your data and put it in nltk compatible format.

---

<p align="center">This workshop is estimated to take you 10 hours to complete.</p><p align="center"><a href="sections/01-text-as-data.md">Get Started</a> →</p>

---

## Lessons

1. [Text as Data](sections/01-text-as-data.md)
2. [Cleaning and Normalizing](sections/02-cleaning-and-normalizing.md)
3. [Using the NLTK Corpus](sections/03-using-the-nltk-corpus.md)
4. [Searching for Words](sections/04-searching-for-words.md)
5. [Positioning Words](sections/05-positioning-words.md)
6. [Types vs. tokens](sections/06-types-vs.-tokens.md)
7. [Length and unique words](sections/07-length-and-unique-words.md)
8. [Lexical density](sections/08-lexical-density.md)
9. [Data Cleaning: Removing Stop Words](sections/09-data-cleaning-removing-stop-words.md)
10. [Data cleaning: Lemmatizing Words](sections/10-data-cleaning-lemmatizing-words.md)
11. [Data cleaning: Stemming Words](sections/11-data-cleaning-stemming-words.md)
12. [Data Cleaning: Results](sections/12-data-cleaning-results.md)
13. [Make Your Own Corpus](sections/13-make-your-own-corpus.md)
14. [Make Your Own Corpus (continued)](sections/14-make-your-own-corpus-(continued).md)
15. [Part-of-Speech Tagging](sections/15-part-of-speech-tagging.md)

---

## Before you get started

If you do not have experience or basic knowledge of the following workshops, you may want to look into those before you start with Introduction to Text Analysis with Python and NLTK:

- Intro to Python workshop (required)
- Command Line workshop (recommended)
- Basic knowledge on Jupyter Notebook (recommended)

### Ethical Considerations

Before you start the Introduction to Text Analysis with Python and NLTK workshop, we want to remind you of some ethical considerations to take into account when you read through the lessons of this workshop:

- In working with massive amounts of text, it is natural to lose the original context. We must be aware of that and be careful when analizing it.
- It is important to constantly question our assumptions and the indexes we are using. Numbers and graphs do not tell the story, our analysis does. We must be careful not to draw hasty and simplistic conclusions for things that are complex. Just because we found out that author A uses more unique words than author B, does it mean that A is a better writer than B?

### Pre-reading suggestions

Before you start the Introduction to Text Analysis with Python and NLTK workshop, you may want to read a couple of our pre-reading suggestions:

- [A Beginner’s Tutorial to Jupyter Notebooks](https://towardsdatascience.com/a-beginners-tutorial-to-jupyter-notebooks-1b2f8705888a)
- [What is text analysis](https://www.scribbr.com/methodology/textual-analysis/) <!--- I don't love this one, but haven't found a better one yet -->

### Projects that use these skills

You may also want to check out a couple of projects that use the skills discussed in this workshop:

- [Short list of academic Text & Data mining projects](https://libguides.bc.edu/textdatamining/projects) 
- [Building a Simple Chatbot from Scratch in Python](https://github.com/parulnith/Building-a-Simple-Chatbot-in-Python-using-NLTK)
- [Classifying personality type by social media posts](https://github.com/TGDivy/MBTI-Personality-Classifier)

---

<p align="center"><a href="sections/01-text-as-data.md">Get Started</a> →</p>

---

## Acknowledgements

This workshop is the result of a collaborative effort of a team of people, mostly involved presently or in the past, with the Graduate Center's Digital Initiatives. If you want to see statistics for contributions to this workshop, you can do so [here](https://github.com/DHRI-Curriculum/python/graphs/contributors). This is a list of all the contributors:

- Current author: [Rafael Davis Portela](https://github.com/rafadavis)
- Past contributor: [Michelle McSweeney](https://github.com/michellejm)
- Past contributor: [Rachel Rakov](https://github.com/rachelrakov)
- Past contributor: [Kalle Westerling](https://github.com/kallewesterling)
- Past contributor: [Patrick Smyth](https://github.com/smythp)
- Past contributor: [Hannah Aizenman](https://github.com/story645)
- Past contributor: [Kelsey Chatlosh](https://github.com/kchatlosh)
- Past reviewer: [Filipa Calado](https://github.com/gofilipa)
- Current editor: [Lisa Rhody](https://github.com/lmrhody)
- Current editor: [Kalle Westerling](https://github.com/kallewesterling)

---

<sub>[Digital Research Institute (DRI) Curriculum](http://purl.org/dc/terms/) by [Graduate Center Digital Initiatives](https://gcdi.commons.gc.cuny.edu/) is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/). Based on a work at <https://github.com/DHRI-Curriculum>. When sharing this material or derivative works, preserve this paragraph, changing only the title of the derivative work, or provide comparable attribution.</sub>

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-sa/4.0/)
