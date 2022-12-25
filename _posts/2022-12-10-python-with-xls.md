---
layout: post
title: Working on xls with python
date: 2022-12-10 10:00:09 +0200
categories: programming
caption: <a href="https://www.freepik.com/free-vector/data-extraction-concept-illustration_12079896.htm#query=data&from_query=dataframe&position=8&from_view=search&track=sph">Image by storyset</a> on Freepik
image: 4905827-min.jpg
---

In this post I will show you how to extract data from a xls document. Therefore datas will be transform into a html table and load into a sql database.

For this script you will need to install the pandas package.
You can find more informations on pandas [here](https://pandas.pydata.org/).

## The xls data

I work on a project about how to use my programming skills combined with my pharmacy knowledge.
Datas can be found [here](https://mshpriceguide.org/fr/download-files-2/).

Datas were collected on the Management Science for Health website.
They are used by non governmental organization to purchase drugs.

## Issues and discussion

I face two main problems:

+ the format of the dataframe
+ the format of the columns name regarding the sql database

As you see on this picture:

<img src="{{ site.image_path }}/msh_xls.png" class="image">

I need to skip some rows and columns using skiprows and usecols parameters.

```py
skiprows=[0,1,2,1168,1169,1170]
usecols="A,B,C,E,G,J,L,N,P,Q,R,U"
```

The two first lines of the code allow us to create our dataframe.

```py
import pandas as pd
df = pd.read_excel("datas/MSH_Price_Guide_Median_Prices-2015.xls",header=1,usecols="A,B,C,E,G,J,L,N,P,Q,R,U",skiprows=[0,1,2,1168,1169,1170])
```

Then I rename the columns.

```py
df = df.rename(columns={
    'DDD Unit':'DDD_Unit',
    'Supplementary Info':'Supplementary_Info',
    'Dosage Form':'Dosage_Form',
    'Route of Admin':'Route_of_Admin',
    'WHO Status':'WHO_Status',
    'DDD Unit':'DDD_Unit',
    'ATC Code':'ATC_Code',
    'Buyer Median (US$)':'Buyer_Median_(US$)',
    'Supplier Median (US$)':'Supplier_Median_(US$)',
    'Comparison Unit':'Comparison_Unit'
})
```

Finally, I transform the dataframe into a html table.

```py
df.to_html('msh_prices.html')
```

## Load data into a SQL database

Create the database and make the first commit.

```py
import sqlite3

conn = sqlite3.connect('msh_prices.db')
c = conn.cursor()
c.execute('''
CREATE TABLE IF NOT EXISTS prices (Description,Supplementary_Info,
Strength,Dosage Form,Route of Admin,WHO Status,DDD,DDD_Unit,ATC_Code,
Buyer_Median_'('US$')',Supplier_Median_'('US$')',Comparison_Unit)
''')
conn.commit()
```

Load the data into the database.

```py
df.to_sql('prices', conn, if_exists='replace', index=False)
```

We can check the content of our database by using this line of code.

```py
c.execute('''
SELECT * FROM prices
''')
for row in c.fetchall():
    print(row)
```

## Conclusion

You can find all the code on my GitHub account [CMagnac](https://github.com/CMagnac/Extract-and-Load-Script).
