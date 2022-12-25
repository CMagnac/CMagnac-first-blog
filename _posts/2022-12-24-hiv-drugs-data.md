---
layout: post
title: HIV drugs and data
date: 2022-12-24 10:00:09 +0200
categories: infectology
permalink: blog/:categories/:title
caption: <a href="https://www.freepik.com/free-vector/set-medical-icons-3d-designs_3439395.htm#query=online%20pharmacy&position=17&from_view=search&track=sph">Image by rawpixel</a> on Freepik
image: 61792-min.jpg
---
This post has been written from diverse relevant source of informations on HIV and cathinone.

## 1. Antiviral therapy

The viral multiplication is a capacity of host cell.

The antiviral drugs must specifically inhibite the viral multiplication without damaging host cells.

Majority of antiviral drugs specifically inhibites the function of essential viral proteins and blocks only the viral processes in a selective way.

Targets are the key enzymes of viral nucleic acid synthesis, the viral proteases who are necessary for the divide of viral polyproteins and others specific viral enzyme systems.

Some drugs are only activate by viral enzymes therefore effective only on infected cells.

In practice, two main problems are relevant.

Firstly, an antiviral therapy should be introduced early in the evolution of the disease in case of acute infection because the highest spot of viral multiplication is often reach throughout the development of clinical signs. A reliable and quick diagnosis is needed.

Secondly, drug-resistant virus strains could be emerging. A sensitivity test is necessary. If needed, an alternative treatment will be initiated with another mechanism of action.

## 2. Antiviral drugs

There are six majors therapeutic classes for HIV treatments.
{% for items in site.data.arv %}
<li> <strong> Active substance </strong>: {{items.active_substance}}.</li>
<li>Class: {{items.class}}.</li>
<li>Indication: {{items.indication}}.</li>
<li>Side effects: {{items.side_effects}}.</li>
<br>
{% endfor %}

## 3. Death and infection in the last twenty years

Data are extract from a pdf document.

You can find it on the Joint United Nations Programme on HIV and AIDS (UNAIDS) official website.
The link is at the end of the post in the bibliographies section.
(Data Chart).

Or you can download the csv document: [downloadcsv]({% link download/global_hiv_data.csv %}).

```python
%matplotlib inline
import matplotlib.pyplot as plt
import pandas as pd

df = pd.read_csv("global_hiv_data.csv")
x = df['year']
y = df['new hiv infections (million)']
over15 = df['new hiv infections (aged 15+ years in million)']
under15 = df['new hiv infections (aged 0-14 years in million)']
total = plt.bar(x, y, align='center', label="Total")
fline = plt.plot(x, over15, color="black", linestyle='dashed', label="aged 15+ years")
mline = plt.plot(x, under15, color="red", linestyle='dotted', label="aged 0-14 years")
plt.legend()
plt.xlabel("Year")
plt.ylabel("New HIV Infections (million)")
plt.title("Global HIV Data")
plt.show()
```

<img src="{{ site.image_path }}/hivchart.png" class="image">

As shown on the graph, the infection death is decreasing during the last twenty years.
This trend is presumably due to the prevention campaigns and new technologies who provide more informations in a global view.

## 4. Correlation between cathinone usage and hiv

This trend is almost always deal with higher income countries.

### 4.1 Khat

Latin name of Khat is *Catha edulis*. Khat is a shrub and *sempervirens* (always green). Khat belongs to the Celastraceae family. Khat grows in temperate warm and tropical geographical areas.

There are an estimation of 20 millions of people who are daily user of fresh leafs for the soft drug that it contains.

Lower dose Khat is a stimulant drug. It releaves from hunger, tiredness and ease communication. On the other hand, consummer has comedowns effect such as irritability and turmoil.

You can become an addict if you consume higher dose of this drug.
As any addiction, the path of redemption is long, harsh and full of despairs.

### 4.2 Risks

There is an increasing risk of using *bath salts* cathinone and being or not infected with HIV.

Synthetic cathinone are psychoactive substances who are use during sex parties, especially by men who have sex with men (MSM). It increases sexual peformance and are entactogen. Needless to say that in this atmosphere, alertness is a fact.

> What is an entactogen effect ?
>
> More informations [here](https://en.wikipedia.org/wiki/Empathogen%E2%80%93entactogen).

Therefore, condoms are less use and the injection materials or the sniffing tubes are shared by consumers. Increasing the risks of sexually transmitted infections (STIs), that's a major public health concern.

Some non-governmental organizations (NGO) like **Sidaction** or **Aides** are working hard on prevention campaigns to improve awaraness.

## 5. Cured of HIV

The bbc reports an interesting article about the first women to be cure from HIV. In the same way as Timothy Ray Brown in 2007, she has received a stem cell transplant from someone with natural resistance to HIV.

You can find this article at the end of the bibliographies note.

> ### Bibliographies
>
> - Manuel de poche de microbiologie médicale, 2nd édition, Lavoisier Médecine: [lavoisier website](https://www.lavoisier.fr/livre/sciences-de-la-vie/atlas-de-poche-de-microbiologie-medicale-2-ed/kayser/descriptif-9782257206367).
> - Data Chart: [unaids org](https://www.unaids.org/en/resources/fact-sheet).
> - Khat history: [khat history](https://leschroniquesduvegetal.wordpress.com/2020/05/04/le-khat-un-arbuste-africain-stupefiant/).
> - Khat drug profil: [khat drug profil](https://www.emcdda.europa.eu/publications/drug-profiles/khat_fr).
> - Pubchem: [cathinone profile](https://pubchem.ncbi.nlm.nih.gov/compound/62258).
> - NGO: [sidaction](https://www.sidaction.org/), [aides](https://www.aides.org/).
> - Psychostimulant Abuse and HIV Infection: [first ncbi article](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4582446/).
> - Recent Human Immunodeficiency Virus Outbreak: [second ncbi article](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7314588/).
> - Sexual practice: [about slam](https://www.frontiersin.org/articles/10.3389/fpsyt.2020.00705/full).
> - Health article: [bbc news](https://www.bbc.com/news/health-60394306).
