# starbucks capstone![image](https://user-images.githubusercontent.com/53383608/110219998-5f769580-7ecb-11eb-8ddc-08a4b392c09b.png)


## Project Overviewn
This is an in-depth data analysis and simulates data of how mobile app users respond to offers sent out by Starbucks. With a better understanding of customer behavior, Starbucks would be able to improve by promotional offers.

## Problem Statement
- What is the predict for event when have gender, age group, income group and offer type will complet offer or not in 20018 year ?
- What is the predict for most offer type in 20018 year ?
 
## Main Files: Project Structure
```
├── data          
|   ├── portfolio.json
|   ├── profile.json
|   └── transcript.zip >> transcript.json
|
├── README.md
├── Starbucks_Capstone_notebook.ipynb 

```

## Data sets

portfolio.json (10 offers x 6 fields) - metadata for each offer (duration, type, etc.)

    id (str) - offer ID
    offer_type (str) - type of offer (BOGO, discount, informational)
    difficulty (int) - minimum required spend to complete an offer
    reward (int) - reward given for completing an offer
    duration (int) - time for offer to be open, in days
    channels (list[str]) - web, email, mobile, social

profile.json (17,000 users x 5 fields) - demographic data for each user

    age (int) - age of the customer (missing values are encoded as 118)
    became_member_on (int) - date when customer created an app account
    gender (str) - gender of the customer (some entries contain 'O' for other rather than 'M' or 'F')
    id (str) - customer ID
    income (float) - customer's income

transcript.json (306,534 transactions x 4 fields)- records for events (transactions, offers received, offers viewed, and offers completed)

    event (str) - record description (transaction, offer received, offer viewed, etc.)
    person (str) - customer ID
    time (int) - time in hours since start of test (the data begins at time t = 0)
    value - (dict) - either an offer ID or transaction amount depending on the record

## Problem Statement and Metrics
-What is the most gender and age ?
-What is the most registration members year ?
-What is the most event in gender and age ?
-What is the most viewed offer count in difficulty, duration, offer_type and reward ?
-What is the most complet offer count in difficulty, duration, offer_type and reward ?
-What is the most transcript in gender ,age and registration members for each year ?
-What is the most offer type each age ?
After Predict
-What is the most gender and age in 2018 year ?
-What is the most offer type of gender in 2018 year ?
-What is the most offer type age in 2018 year ?

## Table of Contents:

    Introduction:
        Data Viewing & Exploration
        Data Cleaning
    EDA Visualization
    Data Preprcessing
    Data Modeling

## Introduction

 ### Data Preprocessing and Cleaning
Portfolio

-extract data into new columns from channels,offer_type column with iterable values

-add offer name cloumn

-rename id to offer_id
profile

-extract age is equal 118

-division age 10

-remove age up 90 years old

-remve gender type 'O'

-convert gender F to 0 and M To 1 and convert to int

-convert became_member_on to date ,get year from date ,rename to reg_year and convert to int

-division income 10000 and convert to int

-rename id to person_id
transcript

-extract data into new columns from event

-extract data into new columns from value to amount,offer_id and reward

-time is hours division 24 to convert dates

-rename person to person_id

-rename value_offer_id to offer_id
general

-convert all number to int

-join all datasets

-rename some columns

-drop some columns
 
 ### Data Modeling

    After pre-processing the dataset and after visualization the next part is to make a model that figure out whether the customer complet to offer or not.

    Here I used different types of models that will predict whether the customer complet to offer or not.

    To make a model we will split the data into  training and testing data.
 
    Target is the event predict complet offer or not and most offer type in 20018 year

The *data* folder contains the 3 datasets provided by Udacity.

The *Starbucks_Capstone_notebook.ipynb* is where all the analysis is.

## Tech Stack
- **Python3** is the main language.
- **Numpy**, **Pandas**, **matplotlib**, **seaborn**, and **sklearn** are the main packages that were used.
- **Jupyter Notebook** is where the code is hosted.

## Author and Acknowledgement

- [Udacity](https://www.udacity.com/) provided this Data Science Nanodegree Program and the access to this dataset.

- [medium](https://karimsoft.medium.com/karimsoft-starbucks-capstone-58821de875ac)
