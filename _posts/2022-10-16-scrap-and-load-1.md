---
layout: post
title: Coding a web-scraper in Python
date: 2022-10-16 10:00:09 +0200
categories: programming
image: post_2.jpg
caption: <a href="https://fr.freepik.com/vecteurs-libre/programmeur-travaillant-code-developpement-web-ingenieur-programmation-python-php-java-script-ordinateur_14723889.htm#query=python&position=9&from_view=search&track=sph">Image by svstudioart</a>
---
The idea of writing this post came up with a question: How to gather informations about HSK1 using python ?

HSK stands for Hanyu Shuiping Kaoshi (汉语水平考试), it's an exam that demonstrates your level of Mandarin.
The exam is divided into two parts: the listening comprehension and the reading comprehension.

Learning and speaking chinese is a long path because you will have to think in "chinese". There are two hundred keys to learn before understanding a bit of how sinographs are built. Besides having a good graphical memory, you also need to have a good ton memory.

Going back to the drawing board and find your own method.  

Pinyins are the phonetic transcription of chinese characters.
One characters can be pronounced in four differents ways.

Being active is the path to sucess, to achieve it you must constantly test your knowledge.

## 1. Set up the environment

I will use Python version 3.10.6 and two famous python libraries for webscraping : requests and beautifulsoup4.

Our target will be a html table from a website which refers to the HSK level 1 vocabularies list (unofficial).

### 1.1 Create a virtual environment

Learning how to create and work with virtual environment is a good habit to take.

Setup the environment:

    $ pip install virtualenv                # Install virtualenv using python 
    $ cd my_folder                          # Wherever you want to put the virtual enviroment folder
    $ virtualenv -p /usr/bin/python3 venv   # Create the environment, with the Python 3.x interpreter
    $ source venv/bin/activate              # Active the environment

### 1.2 Install the libraries

**Requests**: *Requests is a simple, yet elegant, HTTP library.*

If you want more informations on requests, click here: [requests at pypi](https://pypi.org/project/requests/).

**Beautifulsoup4**: *Beautiful Soup is a library that makes it easy to scrape information from web pages.*

If you want more informations on beautifulsoup, click here: [beautifulsoup at pypi](https://pypi.org/project/beautifulsoup4/).

A good practice is to create a requirements.txt which contains the packages.

requirements.txt file:

    beautifulsoup4==4.11.1
    requests==2.28.1

Now install the packages:

    $ pip install -r requirements.txt

More informations on virtualenv ?
Rigth here: [virtualenv at python.org](http://docs.python-guide.org/en/latest/dev/virtualenvs/).

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

From the terminal and in your working folder, tape this.

```bash
python main.py
```
