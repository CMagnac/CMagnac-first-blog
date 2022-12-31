---
layout: post
title: Data scraping in Python
date: 2022-11-06 10:00:09 +0200
categories: programming
permalink: blog/:categories/:title
image: python_logo.png
---
This post is about a python script where you will learn to scrap informations. Data will be store into json dictionaries.

## 1. Configuration

Having more control on our script and for a better understanding of it, these are the purpose of my configuration file.

Python provides a built in module, json. So usefull to make tiny project and improve our skills.

So first, let's create a config.json file and add pairs of keys and values as follow.

```json
{
    "html_tag":"td",
    "attribute":"width",
    "value":["151","179","90","279"],
    "url":"https://www.chineseinstitute.fr/formation-chinois/particuliers/cours-de-chinois-adultes/preparation-hsk-bct/hsk-test-de-niveau-de-chinois/hsk-niveau-1/hsk-1-vocabulaire-a-connaitre/"
}
```

## 2. The code

We will need the same pypi librairies I have used in my previous post about scrapîng.
You can refer to it on how to install and have more informations by clicking on this [link]({% link _posts/2022-10-16-scrap-and-load-1.md %}).

I have also use the time built in module to get the script processing time.

Don't forget to create the script and the json file in the same folder.

```python
import json
import requests
from bs4 import BeautifulSoup as bs
import time

# open the json file
with open("config.json") as f:
    cfg = json.load(f)

def extract_data(url=cfg['url']):
    """http get request
    return the html text
    """
    return requests.get(url).text

def transform_data():
    """parse the html text
    """
    soup = bs(extract_data(), "html.parser")
    return soup

def new_chn_char(soup=transform_data()) -> list:
    """extract the modern sinographs
    return a list
    """
    new_char = soup.find_all(cfg['html_tag'], {cfg['attribute']:cfg['value'][0]})
    return [sino.get_text() for sino in new_char ]

def old_chn_char(soup=transform_data()) -> list:
    """extract the old sinographs
    return a list
    """
    old_char = soup.find_all(cfg['html_tag'], {cfg['attribute']:cfg['value'][1]})
    return [sino.get_text() for sino in old_char]

def pinyin(soup=transform_data()) -> list:
    """extract the pinyin
    return a list
    """
    pinyins = [soup.find_all(cfg['html_tag'], {cfg['attribute']:cfg['value'][2]})]
    pinyins = [p for p in pinyins[0]]
    return  [p.get_text() for p in pinyins]

def french_definition(soup=transform_data()) -> list:
    """extract the french definition
    return a list
    """
    fr_def = [soup.find_all(cfg['html_tag'], {cfg['attribute']:cfg['value'][3]})]
    fr_def = [w for w in fr_def[0]]
    return [words.get_text() for words in fr_def]

def old_chn_dictionary() -> dict:
    """zip the old sinographs with their values
    return a dictionary
    """
    old = old_chn_char()
    pin = pinyin()
    frdef = french_definition()
    return dict(zip(old,zip(pin, frdef)))

def new_chn_dictionary() -> dict:
    """zip the modern sinographs with their values
    return a dictionary
    """
    new = new_chn_char()
    pin = pinyin()
    frdef = french_definition()
    return dict(zip(new,zip(pin, frdef)))

if __name__ == "__main__":

    start = time.time()
    
    d1 = old_chn_dictionary()
    d2= new_chn_dictionary()
    
    with open("old-chinese-dictionary.json", "w") as f:
        json.dump(d1,f)
    
    with open("new-chinese-dictionary.json", "w") as f:
        json.dump(d2,f)
    
    end = time.time()
    
    print(f"EXECUTION TIME : {end-start}")
```

Is it working ? 😎
