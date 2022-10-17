---
layout: page
title: Scrape and Load
date:   2022-10-16 10:00:09 +0200
categories: simple-code
permalink: /:categories/
---
![image](/assets/images/chinese-wall.png)
*@rawpixel - Freepik.com*

I have always been filled with Chinese culture.

Learning chinese language was a huge challenge because you need to *reverse* your traditional way of constructing ideas. Indeed, if you desire to grasp any foreigners languages you will have to gymnastics your brain.

One of the most difficult part of learning chinese language is to remember the correspondance between the characters and its pinyin signification.

Pinyins are the phonetic transcription of chinese characters.
More informations on [pinyin](https://en.wikipedia.org/wiki/Pinyin)

Testing your knowledge is an important part of the learning process. Needless to say that being active is the path of sucess.

I am also a python enthusiast.
How can we make a simple dictionary to store our fresh chinese knowledge ?

I will use Python version 3.10.6 and two famous python libraries for webscraping : requests and beautifulsoup4.

Our target will be a html table from a french website which refers to the list of vocabularies to suceed the HSK level 1. HSK is the Chinese Proficiency Test. 

More informations on [HSK](https://en.wikipedia.org/wiki/Hanyu_Shuiping_Kaoshi)


## First step : create a virtual environment.

Learning how to create and work with virtual environment is a good habit to take. 

Setup the environment :

    $ pip install virtualenv                # Install virtualenv using python 
    $ cd my_folder                          # Wherever you want to put the virtual enviroment folder
    $ virtualenv -p /usr/bin/python3 venv   # Create the environment, with the Python 3.x interpreter
    $ source venv/bin/activate              # Active the environment


## Second step : install the libraries.

Requests : *Requests is a simple, yet elegant, HTTP library.*
More informations on [requests](https://pypi.org/project/requests/)

Beautifulsoup4 : *Beautiful Soup is a library that makes it easy to scrape information from web pages.*
More informations on [beautifulsoup](https://pypi.org/project/beautifulsoup4/)

A good practice is to create a requirements.txt which contains the packages.

requirements.txt file:

    beautifulsoup4>=4.11.1
    requests>=2.28.1


Now install the packages:

    $ pip install -r requirements.txt

More informations on [virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/).


## Third step : the code.

```python
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
    return dict(zip(sinograms_list,pinyins_list))

def load_data(url):
    """Save the data in a json file
    """
    with open("sino_pinyin.json","w",encoding="utf-8") as f:
        json.dump(transform_data(url),f)

if __name__ == "__main__":
    url = "https://www.chineseinstitute.fr/formation-chinois/particuliers/cours-de-chinois-adultes/preparation-hsk-bct/hsk-test-de-niveau-de-chinois/hsk-niveau-1/hsk-1-vocabulaire-a-connaitre"
    load_data(url)
```

Take care.