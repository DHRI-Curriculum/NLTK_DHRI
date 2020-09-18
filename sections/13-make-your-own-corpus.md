← [Data Cleaning: Results](12-data-cleaning-results.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Make Your Own Corpus (continued)](14-make-your-own-corpus-(continued).md) →

---

# 13. Make Your Own Corpus

Now that we have seen and implemented a series of text analysis techniques, let's go to the Internet to find a new text. You could use something such as historic newspapers, or Supreme Court proceedings, or use any txt file on your computer. Here we will use [Project Gutenberg](http://www.gutenberg.org). Project Gutenberg is an archive of public domain written works, available in a wide variety of formats, including `.txt`. You can download these to your computer or access them via the url. We'll use the latter. We found _Don Quixote_ in the archive (see [here](http://www.gutenberg.org/files/996/996-0.txt)), and will work with that.

The Python package `urllib` comes installed with Python, but is inactive by default, so we still need to import it to utilize the functions. Since we are only going to use the urlopen function, we will just import that one.

In the next cell, type:

```python
from urllib.request import urlopen
```

The `urlopen` function allows your program to interact with files on the internet by opening them. It does not read them, however—they are just available to be read in the next line. This is the default behavior any time a file is opened and read by Python. One reason is that you might want to read a file in different ways. For example, if you have a _really_ big file—think big data—you might want to read line-by-line rather than the whole thing at once.

Now let's specify which URL we are going to use. Though you might be able to find _Don Quixote_ in the Project Gutenberg files, please type this in so that we are all using the same format (there are multiple `.txt` files on the site, one with utf-8 encoding, another with ascii encoding). We want the utf-8 encoded one. The difference between these is beyond the scope of this tutorial, but you can check out this [introduction to character encoding](https://www.w3.org/International/questions/qa-what-is-encoding) from The World Wide Web Consortium (W3C) if you are interested.

Set the URL we want to a variable:

```python
my_url = "http://www.gutenberg.org/files/996/996-0.txt"
```

We still need to open the file and read the file. You will have to do this with files stored locally as well. (in which case, you would type the path to the file (i.e., `data/texts/mytext.txt`) in place of `my_url`)

```python
file = urlopen(my_url)

raw = file.read()
```

This file is in bytes, so we need to decode it into a string. In the next cell, type:

```python
don = raw.decode()
```

Now let's check on what kind of object we have in the "don" variable. Type:

```python
type(don)
```

This should be a string. Great! We have just read in our first file.

---

← [Data Cleaning: Results](12-data-cleaning-results.md)&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;[Make Your Own Corpus (continued)](14-make-your-own-corpus-(continued).md) →