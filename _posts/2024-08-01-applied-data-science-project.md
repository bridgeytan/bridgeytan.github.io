---
layout: post
author: Bridget Tan
title: "Applied Data Science Project Documentation"
categories: ITD214
---
## Project Background
Provide an overview of your team's project business goals and objectives and state the objective that you are working on. 

### British Airways: Improving Customer Experience


![image](https://github.com/user-attachments/assets/99ea3085-5a67-4cda-b1bc-c8f256039960)


Our team focuses on how we can improve British Airway's business via enhancing customer satisfaction and experience based on past customer reviews. We aim to improve business by 10%, by focusing on the following 4 elements:

| S/N | Objective                                                                                       | Member  |
|-----|-------------------------------------------------------------------------------------------------|---------|
| 1   | To reduce response time by 10% by identifying significant areas of concern through topic modelling and association rule mining for automation of replies | Yan     |
| 2   | To analyse review topics for the four different seat types for a more targeted marketing approach, improving business by 10% | Carlin  |
| **3**   | **To identify areas of customer satisfaction for marketing purposes, to improve business by 10%**   | **Bridget** |
| 4   | To reduce negative review sentiments by 10% to improve customer satisfaction and demand.         | Vivienne|

We will focus on (3) identifying areas of customer satisfaction for marketing purposes to improve business by 10%.

<br>
The project plan following the CRISP-DM framework is as below:  

<p align="center">
  <img width="800" alt="image" src="https://github.com/user-attachments/assets/4031a3e4-64a0-453f-920a-14434f74f39b">
</p>

<br>
      
### Dataset
The dataset is retrieved from Kaggle, which contained 3700 rows and 20 columns of customer reviews of British Airways, scraped from airlinequality.com from 2015 to 2023. Columns as such:  

<p align="center">
  <img width="1000" alt="image" src="https://github.com/user-attachments/assets/fe6573ae-1d0b-4bf9-8bf3-dd388a89ed7f">
</p>

**OverallRating:** The overall rating given by the customer.  
**ReviewHeader:** The header or title of the customer's review.  
**Name:** The name of the customer providing the feedback.  
**Datetime:** The date and time when the feedback was posted.  
**VerifiedReview:** Indicates whether the review is verified or not.  
**ReviewBody:** The detailed body of the customer's review.  
**TypeOfTraveller:** The type of traveler (e.g., Business, Leisure).  
**SeatType:** Class of the traveler (e.g., Business, Economy).  
**Route:** The flight route taken by the customer.  
**DateFlown:** The date when the flight was taken.  
**SeatComfort:** Rating for seat comfort.  
**CabinStaffService:** Rating for cabin staff service.  
**GroundService:** Rating for ground service.  
**ValueForMoney:** Rating for the value for money.  
**Recommended:** Whether the customer recommends British Airways.  
**Aircraft:** The aircraft used for the flight.  
**Food&Beverages:** Rating for food and beverages.  
**InflightEntertainment:** Rating for inflight entertainment.  
**Wifi&Connectivity:** Rating for onboard wifi and connectivity.  



## Work Accomplished

### Data Preparation
  
#### Converting fields into appropriate data types

The 'Datetime' and 'Dateflown' are not in datetime format, so they need to be converted from string to datetime format.

<p align="center">
  <img width="800" alt="image" src="https://github.com/user-attachments/assets/4410aff0-8870-4ddc-baef-b6854e4fb755">
</p>

#### Removal of missing values

Missing values were detected these fields:
**Datetime:** (~20.5%)  
**TypeOfTraveller:** (~20.8%)  
**Route:** (~20.9%)  
**DateFlown:** (~21%)  
**SeatComfort:** (~3.1%)  
**CabinStaffService:** (~3.4%)  
**GroundService:** (~22.9%)  
**Aircraft:** (~48.1%)  
**Food&Beverages:** (~10.4%)  
**InflightEntertainment:** (~31.1%)  
**Wifi&Connectivity:** (~83.5%)  

For columns where missing values make up less than 10% of the dataset (OverallRating, CabinStaffService, SeatComfort), missing values were removed. 

#### Text Pre-processing 
<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/d4e387a2-9be3-4e97-84c2-297b901bc660">
</p>

#### Normalise all to lowercase

All text within the ReviewBody column was normalised into lowercase.

#### Removal of punctuation and special characters

Presence of non-alphabetical characters (e.g. Couldnâ€™t, KeflavÃ­k) and punctuation in text dataset (e.g. !()-[]{};:'"\,<>./?@#$%^&*_~) were removed.

#### Removal of dates, prices and flight numbers

Figures that might represent dates, prices or flight numbers (e.g. 747-400, BA12) were removed as they are specific and may not necessarily provide additional information on the broad topic. Numbers were also removed.

#### Tokenisation

<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/615c2c61-c5c9-4e8e-85d5-1f3db859d9cd">
</p>
Words in the Reviewbody column were tokenised. 

#### Stopword removal
<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/74018eca-5e9e-40f0-b90d-b5890a84332f">
</p>

Stopwords were removed using the NLTK corpus. After looking through the remaining most frequent tokens, domain stopwords were also determined and removed. The words are 'airline', 'british', 'airway', 'airways', 'aircraft', 'airlines', 'plane','flight','flights','ba'.

#### Removal of short characters
<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/7f161740-66d9-476e-96e6-1baae1ca8716">
</p>
Words like 'us', 'on' and 'h' were removed.

#### Lemmatization, stemming and POS tagging and removal
<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/7dc66948-1b0e-4670-bdfb-a9366f4e9257">
</p>

Lemmatization was conducted to normalise the tokens into a single base form e.g. flying to fly. Map POS tags to WordNet POS Tags was used to facilitate lemmatization e.g. conjunctions, prepositions, determiners, verbs etc. Certain POS such as coordinating conjunction, preposition, determiner, personal pronouns were removed as they do not add meaningful information for subsequent clustering/topic modelling. 
Stemming was not performed to retain context-specific terms for further analysis.

#### Filtering for data where OverallRating >= 7

As this business goal looks into good reviews, only data where the OverallRating of 7 and more are included. There is a total of 1323 rows within this filtered dataset.
<br>

### Modelling

We will compare two models, Latent Dirichlet Allocation (LDA) and Bidirectional Encoder Representations from Transformers (BERT).

#### LDA

LDA is a widely used topic modelling technique that provides interpretable results and can be scaled efficiently. To determine the ideal number of topics, the LDA model was run assuming the number of topics 1 to 21, and the perplexity score subsequently charted. Based on the graph below, the higher the number of topics, the worse the perplexity score. This suggests that the number of topics were small. 
<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/10a2ca1a-cf69-4e57-bd18-2d0db1960213">
</p>

To further help analysing the optimal number of topics, the intertopic distance map was used. There are 3 clear clusters that can be seen (circles that are not overlapping, with great distance between each cluster).
<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/54c25dce-404b-4f01-804b-30b6671b2059">
</p>

The parameters were then tuned for 3 topics, and these are the most prominent terms per topic. 

**Topic 1:** 0.012*"heathrow" + 0.009*"crew" + 0.008*"seat" + 0.008*"cabin" + 0.008*"time" + 0.008*"board" + 0.007*"service" + 0.007*"staff" + 0.007*"food" + 0.007*"first"  
**Topic 2:** 0.021*"seat" + 0.018*"good" + 0.014*"crew" + 0.013*"food" + 0.012*"service" + 0.012*"time" + 0.011*"cabin" + 0.008*"london" + 0.007*"economy" + 0.007*"well"  
**Topic 3:** 0.017*"good" + 0.013*"seat" + 0.010*"service" + 0.008*"staff" + 0.008*"get" + 0.008*"time" + 0.007*"lounge" + 0.007*"crew" + 0.006*"food" + 0.006*"london"  

For ease of interpretation, these can be transformed into word clouds. The bigger the word, the more important.  The number of words per topic were increased to have better context.
#### Topic 1
<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/482b88bb-1d3c-4f71-8be2-3bbadd8390db">
</p>

The most prominent keyword is "Heathrow", suggesting that the 1st topic focuses on the experience in Heathrow airport, in particular the good service provided by the cabin crew.  

Some reviews under this topic includes reviews such as “The ground staff at London Heathrow are very polite and helpful” and " Flew Zurich to London Heathrow. Very friendly staff, great choice of complimentary drinks” which help to cement this idea.

#### Topic 2
<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/b6ef3396-47b8-4920-a11e-08c1628b6a4e">
</p>

Common words such as “Lounge”, “class”, “business” and “first” suggests that the topic is about the first and business class, likely focusing on the comfort of the seats. Some reviews under this topic includes reviews such as “First Class felt exclusive, the dedicated crew were … proactive, friendly, very respectful … The seat… spacious, well designed and very comfortable.”

#### Topic 3
<p align="center">
  <img width="600" alt="image" src="https://github.com/user-attachments/assets/915295cb-d502-4a4a-92c8-1e9a7930a53c">
</p>

This topic most likely focuses on timeliness of the flights, and also general experience overall. Reviews under this topic include “Due to delayed take off I risked missing my connecting flight. Thanks to the excellent premium host service… I managed to be on time!”


### Evaluation
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Recommendation and Analysis
Explain the analysis and recommendations

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## AI Ethics
Discuss the potential data science ethics issues (privacy, fairness, accuracy, accountability, transparency) in your project. 

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

## Source Codes and Datasets
Upload your model files and dataset into a GitHub repo and add the link here. 
