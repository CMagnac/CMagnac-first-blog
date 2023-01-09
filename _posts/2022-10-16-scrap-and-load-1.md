---
layout: post
title: Coding a web-scraper in Python
date: 2022-10-16 10:00:09 +0200
categories: programming
permalink: blog/:categories/:title
image: python_logo.png
---
The idea for this post came from a question: How can I gather information about HSK1 using Python?

HSK stands for **Hanyu Shuiping Kaoshi** (汉语水平考试), it's an exam that measures your level of Mandarin.

The exam has two parts: listening comprehension and reading comprehension.

Learning and speaking Chinese is a long process because you have to think in "Chinese." There are 200 characters to learn before you can understand how Chinese characters are constructed.

In addition to having a good visual memory, you also need to have a good memory for tones.

It's important to go back to the basics and find your own method.
Pinyin is the phonetic transcription of Chinese characters.
One character can be pronounced in four different ways.

Being active is the key to success, and to achieve it you must constantly test your knowledge.

## 1. Set up the environment

I will use Python version 3.10.6 and two popular Python libraries for web scraping: requests and beautifulsoup4.

Our target will be an HTML table from a website that lists the HSK level 1 vocabulary (unofficial).

### 1.1 Create a virtual environment

It's good practice to learn how to create and work with a virtual environment.

Setup the environment:

```bash
pip install virtualenv
cd my_folder
virtualenv -p /usr/bin/python3 venv
source venv/bin/activate
```

### 1.2 Install the libraries

**Requests**: *Requests is a simple, yet elegant, HTTP library.*

If you want more informations on requests, click here: [requests at pypi](https://pypi.org/project/requests/).

**Beautifulsoup4**: *Beautiful Soup is a library that makes it easy to scrape information from web pages.*

If you want more informations on beautifulsoup, click here: [beautifulsoup at pypi](https://pypi.org/project/beautifulsoup4/).

A good practice is to create a requirements.txt file that lists the packages you need.

requirements.txt file:

```text
beautifulsoup4==4.11.1
requests==2.28.1
```

Now install the packages:

```bash
pip install -r requirements.txt
```

More informations on virtualenv ?
Right here: [virtualenv at python.org](http://docs.python-guide.org/en/latest/dev/virtualenvs/).

## 2. The code

Create a main.py file and tape the following code.

```py
import json
import requests
from bs4 import BeautifulSoup as bs

def extract_data(url):
    """Send a GET request to url
    return the raw text
    """
    return requests.get(url).text

def transform_data(url):
    """find td tags for chinese characters and pinyin
    return a dictionary 
    """
    soup = bs(extract_data(url),"html.parser")
    sinograms_list = soup.find_all("td",{"width":"179"})
    sinograms_list = [sino.get_text() for sino in sinograms_list ]
    pinyins_list = [soup.find_all("td",{"width":"90"})]
    pinyins_list = [p for p in pinyins_list[0]]
    pinyins_list = [p.get_text() for p in pinyins_list]
    return dict(zip(sinograms_list, pinyins_list))

def load_data(url):
    """Save the data in a json file
    """
    with open("sino_pinyin.json","w",encoding="utf-8") as f:
        json.dump(transform_data(url), f)

if __name__ == "__main__":
    url = "https://www.chineseinstitute.fr/formation-chinois/particuliers/cours-de-chinois-adultes/preparation-hsk-bct/hsk-test-de-niveau-de-chinois/hsk-niveau-1/hsk-1-vocabulaire-a-connaitre"
    load_data(url)
```

## 3. Run the code

From the terminal and in your working folder, type this.

```bash
python main.py
```
