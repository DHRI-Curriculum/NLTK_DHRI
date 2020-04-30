[<<< Previous](../README.md) | [Next >>>](02-text_as_data.md)

# Overview

This tutorial will give a brief overview of the considerations and tools involved in basic text analysis with Python. By completing this tutorial, you will have a general sense of how to turn text into data using the Python package, NLTK. You will also be able to take publicly available text files and transform them into a corpus that you can perform your own analysis on. Finally, you will have some insight into the types of questions that can be addressed with text analysis.

## Cloning the repository

Before getting started, clone [this repository](https://github.com/DHRI-Curriculum/text-analysis) to your local machine. Instructions for cloning Git repositories can be found [here](https://github.com/DHRI-Curriculum/git/blob/master/sections/cloning.md).

## Setup and installation

If you have not already installed the [Anaconda](https://www.anaconda.com/download/) distribution of Python 3, please do so.

You will also need [`nltk`](https://github.com/DHRI-Curriculum/install/blob/master/sections/nltk.md) and [`matplotlib`](https://github.com/DHRI-Curriculum/install/blob/master/sections/conda.md) to complete this tutorial. Both packages come installed with Anaconda. To check to be sure you have them, open a new Jupyter Notebook (or any IDE to run Python).

Find Anaconda Navigator on your computer (it should be located in the folder with your other applications), and from Acadonda Navigator's interface, launch a Jupyter Notebook.

![jupyter](images/jupyter.png)

It will open in the browser. All of the directories (folders) in your home directory will appear - we'll get to that later. For now, select 'New' >> Python3 in the upper right corner.

![jupyter](images/jupyter1.png)

A blank page with an empty box should appear.

![jupyter](images/jupyter2.png)

In the box, type:

```python
import nltk
import matplotlib
```

Press **Shift** + **Enter** to run the cell (or click run at the top of the page). Don't worry too much about what this is doing - that will be explained later in this tutorial. For now, we just want to make sure the packages we will need are installed.

![jupyter](images/jupyter3.png)

If nothing happens, they are installed and you are ready to move on! If you get an error message, either you have a typo or they are not installed. If it is the latter, open the command line and type:

```bash
conda install nltk -y
conda install matplotlib -y
```


Now we need to install the nltk corpus. This is very large and may take some time if you are on a weak connection.

In the next cell, type:

```python
nltk.download()
```

and run the cell.

The NLTK downloader should appear. Please install all of the packages. If you are short on time, focus on book" for this tutorial—you can download the other packages at another time for later use.

Yours will look a little different, but the same interface. Click on the 'all' option and then 'Download'. Once they all trun green, you can close the Downloader dialogue box.

![nltk downloader](images/nltk.png)

Return to your Jupyter Notebook and type:

```python
from nltk.book import *
```

A list of books should appear. If this happens, great! If not, return to the downloader to make sure everything is ok.

Close this Notebook without saving - the only purpose was to check if we have the appropriate packages installed.

[<<< Previous](../README.md) | [Next >>>](02-text_as_data.md)
