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
| 3   | To identify areas of customer satisfaction for marketing purposes, to improve business by 10%   | Bridget |
| 4   | To reduce negative review sentiments by 10% to improve customer satisfaction and demand.         | Vivienne|

The project plan following the CRISP-DM framework is as below:

<p align="center">
  <img width="800" alt="image" src="https://github.com/user-attachments/assets/4031a3e4-64a0-453f-920a-14434f74f39b">
</p>

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
Document your work done to accomplish the outcome

### Data Preparation
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

#### Converting fields into appropriate data types

The 'Datetime' and 'Dateflown' are not in datetime format, so they need to be converted from string to datetime format.

<p align="center">
  <img width="800" alt="image" src="https://github.com/user-attachments/assets/4410aff0-8870-4ddc-baef-b6854e4fb755">
</p>

#### Removal of missing values

Missing values were detected in several fields:
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



#### Text-preprocessing

### Modelling
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce bibendum neque eget nunc mattis eu sollicitudin enim tincidunt. Vestibulum lacus tortor, ultricies id dignissim ac, bibendum in velit. Proin convallis mi ac felis pharetra aliquam. Curabitur dignissim accumsan rutrum. In arcu magna, aliquet vel pretium et, molestie et arcu. Mauris lobortis nulla et felis ullamcorper bibendum. Phasellus et hendrerit mauris. Proin eget nibh a massa vestibulum pretium. Suspendisse eu nisl a ante aliquet bibendum quis a nunc. Praesent varius interdum vehicula. Aenean risus libero, placerat at vestibulum eget, ultricies eu enim. Praesent nulla tortor, malesuada adipiscing adipiscing sollicitudin, adipiscing eget est.

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
