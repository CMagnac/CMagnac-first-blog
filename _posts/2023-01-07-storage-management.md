---
layout: post
title: Storage management
date: 2023-01-07 10:00:00 +0200
categories: pharmacy
permalink: blog/:categories/:title
image: pharmacysymbol.jpg
caption: <a href="https://www.freepik.com/free-vector/hand-drawn-medical-pharmacy-symbol_29900479.htm#page=3&query=pharmacy&position=9&from_view=search&track=sph">Image by Freepik</a>
---
One of the most important skills for a pharmacist is to optimize both the back and front office in order to have the best flow of material and human resources. The technical term for this is storage management, which will be explained in this post.

I began working as a professional pharmacist almost ten years ago. At that time, there were not as many informatic tools or as much internet information available, which made it more difficult to increase productivity. The pharmacy software available did not have as many features as teams rely on today.

The North has a lot of power in terms of economy and technology, and it is growing faster than the South. This is a fact. Non-governmental organizations (NGOs) and open-source solutions can be part of the solution to this inequality.

## 1. Type of software

Some organizations provide different types of software that can be free or not.

### 1.1 LibreOffice

It's the free equivalent of Microsoft office.
It's a must have on any platforms.
You can find the official website here: [LibreOffice](https://www.libreoffice.org/).

### 1.2 Specific software

These are adapted to the management of a pharmacy.

The Management Sciences for Health (MSH) has a list of repositories related to electronic pharmaceutical management systems.

Here is the link to their repository: [MSHGithub](https://github.com/MSH).

Here is the link to the official website: [MSHWebsite](https://msh.org/).

Others are more specific for HIV patient management.
Santia is one of them. Here is the link to the website: [SantiaWebsite](https://www.santia.org/).

### 1.3 GnuHealth

GnuHealth is a free health and hospital information system.

You can find the official website here : [GnuHealthWebsite](https://www.gnuhealth.org/).

The hospital management information system is built with Python and works with Tryton. Tryton is a three-tier computer application platform on top of which an Enterprise Resource Planning (ERP) is built.

You can find the official website here : [TrytonWebsite](http://www.tryton.org/).

In addition to the necessity of installing a software management system, there are different tools available for managing stock.

## 2. Tools for storage management

<img src="{{ site.image_path }}/storage_tables.png" class="image">

You can click here [cmagnac](https://cmagnac.github.io/tables-template/) to see the tables on a webpage.

### 2.1 Product sheet

This is the main tool for managing storage.

The goals of product sheet are:

+ order preparation
+ quantification of loss
+ tracking drugs consumption

A sheet for each drug and the corresponding quantities in units is noted.
In the context, discuss the use of a paper-based approach or an electronic patient monitoring system.

### 2.2 Dispense register

Record all dispensed prescriptions.
Use a specific register for pharmacological classes such as HIV treatment.
Make a daily overview of the dispensation.

### 2.3 Inventory sheet

Make achievement easier.
Gain a global vision of the stock.

## 3. Physical inventory of storage

Validate and correct stock by using the inventory sheet.
Remove outdated drugs.
Manage the team to improve storage management.
Ideal achievement: 1 inventory per month.
Minimum achievement: twice a year.
There should not be any deliveries during the inventory, which should be completed all at once.
The stock is considered accurate when the inventory deviation does not exceed 5%.

```python
def inventory_deviation(physical_stock, theoretical_stock):
    return (physical_stock - theoretical_stock) / physical_stock
```
