← [Text as Data](01-text-as-data.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Using the NLTK Corpus](03-using-the-nltk-corpus.md) →

---

# 2. Cleaning and Normalizing

Generally, however, our questions are more about topics rather than writing style. So, once we have a corpus—whether that is one text or millions—we usually want to clean and normalize it. There are three terms we are going to need:

- **Text normalization** is the process of taking a list of words and transforming it into a more uniform sequence. Usually, this involves removing punctuation, making the words all the same case, removing _stop words_, and either _stemming_ or _lemmatizing_ the words. It can also include expanding abbreviations or matching misspellings (but these are advanced practices that we will not cover).

You probably know what removing punctuation and capitalization refer to, but the other terms may be new:

- **Stop words** are words that appear frequently in a language, often adding grammatical structure, but little semantic content. There is no official list of stop words for any language, though there are some common, all-purpose lists built in to NLTK. However, different tasks require different lists. The purpose of removing stop words is to remove words that are so common that their meaning is diminished across a large number of texts.

- **Stemming and lemmatizing** both of these processes try to consolidate words like "laughs" and "laughing" to  "laugh" since they all mean essentially the same thing, they are just inflected differently. So again, in an attempt to reduce the number of words, and get a realistic understanding of the meaning of a text, these words are collapsed. Stemming does this by cutting off the end (very fast), lemmatizing does this by looking up the dictionary form (very slow).

Language is messy, and created for and by people, not computers. There is a lot of grammatical information in a sentence that a computer cannot use. For example, I could say to you:

> The house is burning.

and you would understand me. You would also understand if I say

> house burn.

The first has more information about tense, and which house in particular, but the sentiment is the same either way.

In going from the first sentence to the normalized words, we removed the stop words (_the_ and _is_), and removed punctuation and case, and lemmatized what was left (_burning_ becomes _burn_—though we might have stemmed this, its impossible to tell from the example). This results in what is essentially a "bag of words," or a corpus of words without any structure. Because normalizing your text reduces the number of words (and therefore the number of dimensions in your data), and keeps only the words that contribute meaning to the document, this cleaning is usually desirable.

This is a very important topic in Machine Learning tutorials. For the time being, we just need to know that there is "clean" and "dirty" versions of text data. Sometimes our questions are about the clean data, but sometimes our questions are in the "dirt."

## A Note on Ethics

The act of cleaning/normalizing subscribes text to predetermined categories of meaning, forcing meaning into existing "boxes," so to speak. This doesn't mean that we should avoid cleaning or normalizing text, but that we should be aware of how some textual reductions have the potential to affect meaning. How does quantification reinforce differences or stratifications within our data? We have to be careful about the kinds of questions we are asking, and how we might be reproducing some of our assumptions in our inquiry.

To read more about ethics and text analysis, see Lauren Klein's "[Distant Reading After Moretti](https://arcade.stanford.edu/blogs/distant-reading-after-moretti)," where she questions, "Instead of first asking what can be modeled—what phenomena we can track at scale—we might instead ask: what might be hidden in this corpus?”

## Evaluation

Check all sentences below that are correct:

- Stop words are useless for text analysis, therefore the first step in any project is to remove them from the text.

- In any type of data analysis, we usually want to cleanse the data in order to prepare it for the analysis. In text analysis, this process is called "text normalization" and can involve tasks such as removing undesired words and punctuation.*

- Textual alterations can potentially change the original intended meaning. Therefore, we must always strive to work with the data exactly as it is in the source.

## Keywords

Do you remember the glossary terms from this section?

- [Machine Learning](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/machine-learning.md)
- [Text Normalization](https://github.com/DHRI-Curriculum/glossary/blob/v2.0/terms/text-normalization.md)

---

← [Text as Data](01-text-as-data.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Using the NLTK Corpus](03-using-the-nltk-corpus.md) →