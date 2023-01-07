---
layout: post
title: Carfentanil drug facts
date: 2022-12-16 10:00:09 +0200
categories: toxicology
permalink: blog/:categories/:title
image: carfentanil.png
caption: <a href="https://pubchem.ncbi.nlm.nih.gov/compound/62156">Carfentanil by pubchem</a>
---

Carfentanil is an opioid analgesic dérivated from the chemical structure of fentanyl. Carfentanil is used as a tranquilizer for large animals.

By adding an ester compound to fentanyl you get carfentanyl. Then, the activity of carfentanyl is multiply by a hundred.
Carfentanil was first synthesized in 1974 by a team of chemists at Janssen Pharmaceutical which included Paul Janssen.

The only antidote to a carfentanil intoxication is naloxone.

## 1. Pharmacology

Carfentanyl binds to the mu opioid receptors and stimulate the exchange of GTP for GDP on the G-protein complex. The mu-binding sites are distributed in the brain, spinal cord and other tissues. It has effects on the central nervous system which are analgesia, sedation, respiratory depression and myosis.

It also inhibits the release of vasopressin, somatostatin, insulin and glucagon.

Carfentanil is about 10,000 times as potent as morphine.
One microgram is enough for the carfentanil to start it activity on human.

There are no human application.

See more informations about carfentanil on pubchem and drugbank:
[bibliographies](#bibliographies).

## 2. A lethal weapon

Russia had a long history of how to synthetise and use chemicals products.

One of major science revolution in the field of chemistry was the establishment of the Periodic table. It opened a wide range of comprehension on how to use each elements and combines them with others to synthetize more complexes and active structures.

Dmitri Ivanovitch Mendeleïev was Russian. He is the father of the Mendeleïev table.

Russia has also developped a "knowledge" in the infamous field of using chemicals as a weapon. Arkadi Vaksberg has written an insightful book on this topic, "Toxic Politics: The Secret History of the Kremlin's Poison Laboratory".

Recently Russian police forces used carfentanil and remifentanil to resolve a hostage situation in Moscow in 2002.
Where Chechen rebels stormed a Moscow theater and trapped more than 800 people for 57 hours.

According to criminal experts, Carfentanil is the perfect terrorist weapon.

Get more informations about the Moscow theater hostage crisis.
[bibliographies](#bibliographies).

## 3. Illicit usage

One of the most popular singer of this century, Prince is dead because of his addiction to fentanyl.

The United States opioid crisis is still running and may contribute to a similar opioid epidemic in Europe.

The use of novel synthetic opioids as recreational drugs has become a public health concern as they are implicated in numerous fatal intoxications across the world.

Toxic exposure to carfentanil typically occurs through injection, insufflation or inhalation. Carfentanil use is strongly connected to polydrug use.

Nowaday, internet is one of the best place where smugglers and dealers trade illegal drugs. Every body can easly access these dark markets, that's a public health security concern.

Otherwise, the trafficking of opioids is alarming.

Here are just few samples of what we know so far.

Paraguyan pharmacies have long been involved in the black market for medicine. There was a robust black market for medicines sold in pharmacies and that regulators agencies had no control over the situation.

China and India has a bad reputation on the production of fentanyl.
In China, until recently, fentanyl was largely unregulated. Underground Chinese labs began tweaking the fentanyl molecule, which is easy to alter for anyone with basic knowledge of chemistry and lab tools.

Get more informations about fentanyl sold under the counter and underground labs in China.
[bibliographies](#bibliographies).

### 3.1 Facts and figures

#### 3.1.1 Overview Data

Here are some data from US:

+ 70.630 people died from drug overdose in 2019
+ 10.1 million people misused prescription opioids in the past year
+ 1.6 million people had an opioid use disorder in the past year
+ 2 million people used methamphetamine in the past year
+ 745.000 people used heroin in the past year
+ 50.000 people used heroin for the first time
+ 1.6 million people misused prescription pain relievers for the first time
+ 14.480 deaths attributed to overdosing on heroin
+ 48.006 deaths attributed to overdosing on synthetic opioids other than methadone

#### 3.1.2 Overdose Death

I have formated a sample of data which come from the **National Institutes of Health (NIH)** about the "Overdose death rate".
You can find the link to this article in the bibliographies section.
[bibliographies](#bibliographies).

Download the csv file [here]({% link download/anyopioid_data.csv %})

Below is the python code.

```python
%matplotlib inline
import matplotlib.pyplot as plt
import pandas as pd

df = pd.read_csv("anyopioid_data.csv")
x = df['Year']
y = df['Any Opioid']
female = df['Female']
male = df['Male']
total = plt.bar(x, y, align='center', label="Total")
fline = plt.plot(x, female, color="black", linestyle='dashed', label="Female")
mline = plt.plot(x, male, color="red", linestyle='dotted', label="Male")
plt.legend()
plt.xlabel("Year")
plt.ylabel("Overdose Deaths")
plt.title("Any opioid ICD-10 codes Overdose Deaths")
plt.show()
```

Finally, I got this chart.

<img src="{{ site.image_path }}/barchart.png" class="image">

### 3.2 Explanation

As you can see from the chart, the opioid overdose death has increased during the past twenty years.

Most important tools for health care professional are the prevention.

## 4. Prevention

This list of prevention has been copied from the tribal epidemiology website.

+ talk to your kids
+ keep drugs in a safe storage
+ dispose leftover prescription medication
+ talk to your doctor
+ don't take opioids with alcohol and other medication
+ ask for help
+ know what to do in an overdose emergency situation

> ### Bibliographies
>
> 1. [Carfentanil on Pubchem](https://pubchem.ncbi.nlm.nih.gov/compound/62156).
> 2. [Carfentanil on Drugbank](https://go.drugbank.com/drugs/DB01535).
> 3. [Moscow theater hostage crisis](https://www.history.com/news/opioid-chemical-weapons-moscow-theater-hostage-crisis).
> 4. [Overdose Death Rates, NIH](https://nida.nih.gov/research-topics/trends-statistics/overdose-death-rates).
> 5. [Carfentanil - from an animal anesthetic to a deadly illicit drug](https://pubmed.ncbi.nlm.nih.gov/33581655/).
> 6. [Fentanyl Sold Under the Counter](https://insightcrime.org/news/fentanyl-morphine-sold-under-counter-paraguay-pharmacies/).
> 7. [Underground labs in China](https://www.science.org/content/article/underground-labs-china-are-devising-potent-new-opiates-faster-authorities-can-respond).
> 8. [Tribal Epidemiology Center](https://tribalepicenters.org/).
