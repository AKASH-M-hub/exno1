
# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
from google.colab import drive

drive.mount("/content/drive")
![image](https://github.com/user-attachments/assets/c146260c-c0bf-4439-9346-516773c93a9f)

ls drive/MyDrive/'Colab Notebooks'/Data_set.csv

![image](https://github.com/user-attachments/assets/fc1afdbc-50de-4fed-b189-ed4ba172d243)

import pandas as pd

df=pd.read_csv('drive/MyDrive/Colab Notebooks/Data_set.csv')

df

![image](https://github.com/user-attachments/assets/03398556-f839-4595-91d2-f30d09969ccd)

df.isnull().sum()

![image](https://github.com/user-attachments/assets/22bdecbb-3203-4aa9-be09-f6bcb3f52362)

df.isnull().dropna()

![image](https://github.com/user-attachments/assets/d0bf410a-d8b6-4e2a-9535-15a843849b01)

df.fillna(0)

![image](https://github.com/user-attachments/assets/61d047c9-d942-49c5-aa8f-95b32b67c8da)

df.ffill()

![image](https://github.com/user-attachments/assets/12a272a3-e819-41ea-97e6-7729fc98525f)

df.bfill()

![image](https://github.com/user-attachments/assets/d4c0dcf7-1bf2-47cd-851b-cc1eaea17069)

df_mean1=df['num_episodes'].fillna(df['num_episodes'].mean())

df_mean1

![image](https://github.com/user-attachments/assets/9a329ec0-b506-42c8-925b-e4c811b7a350)

df_mean2=df['rating'].fillna(df['rating'].mean())

df_mean2

![image](https://github.com/user-attachments/assets/426e7355-4113-41d2-af55-e02ba4a09ab1)

df_mean3=df['current_overall_rank'].fillna(df['current_overall_rank'].mean())

df_mean3

![image](https://github.com/user-attachments/assets/df35f527-0b38-4f59-ac17-108d1393a3a4)

df_mean4=df['lifetime_popularity_rank'].fillna(df['lifetime_popularity_rank'].mean())

df_mean4

![image](https://github.com/user-attachments/assets/edabbbda-d182-412f-853b-bc08f3cf6f97)

df_mean5=df['watchers'].fillna(df['watchers'].mean())

df_mean5

![image](https://github.com/user-attachments/assets/fe22b4b6-1d2e-42f1-9d11-e46e8f663211)

df_dropna=df.dropna()

df_dropna

![image](https://github.com/user-attachments/assets/6b1f15c4-79a4-47d7-85e1-ce774b083e8d)

import pandas as pd

import seaborn as sns

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]

af=pd.DataFrame(age)

af

![image](https://github.com/user-attachments/assets/60cc3a10-6af0-43e1-9dcc-2447b7b0f0dd)

sns.boxplot(af)

![image](https://github.com/user-attachments/assets/5acbe488-2108-4f8f-8e58-089ee5573b66)

sns.scatterplot(af)

![image](https://github.com/user-attachments/assets/b8adc663-8503-4369-9d37-8215757abf67)

q1=af.quantile(0.25)

q2=af.quantile(0.5)

q3=af.quantile(0.75)

iqr=q3-q1

iqr

![image](https://github.com/user-attachments/assets/5d424861-70eb-4ff5-a2a4-879afa781b0a)

import numpy as np

Q1=np.percentile(af,25)

Q2=np.percentile(af,50)

Q3=np.percentile(af,75)  

IQR=Q3-Q1

lower_bound=Q1-1.5*IQR

upper_bound=Q3+1.5*IQR

outliers = [x for x in age if x < lower_bound or x > upper_bound]

print('Q1:',Q1)

print('Q3:',Q3)

print('IQR:',IQR)

print('Lower bound:',lower_bound)

print('Upper bound:',upper_bound)

print('Outliers:',outliers)

![image](https://github.com/user-attachments/assets/ff9ccec3-bb58-469e-8ee5-8ce53e2d3c97)

af=af[((af>=lower_bound)&(af<=upper_bound))]

af

![image](https://github.com/user-attachments/assets/7157eb9d-1753-4b08-b6e1-39edb56ab6cf)

af.dropna()

![image](https://github.com/user-attachments/assets/42308f51-6e1f-4a8e-aa16-c1d9366a96c8)

sns.boxplot(af)

![image](https://github.com/user-attachments/assets/51bf05f6-d97a-4d4e-8aa4-6ab3a1996886)

sns.scatterplot(af)

![image](https://github.com/user-attachments/assets/161fac5f-98da-46a3-b914-25721f599171)

from scipy import stats

import numpy as np

import pandas as pd

import seaborn as sns

data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93]

df=pd.DataFrame(data)

sns.boxplot(df)

![image](https://github.com/user-attachments/assets/027bd63d-8d97-49e2-be6f-2ef48193ef28)

mean=np.mean(data)

mean

std=np.std(data)

std

z=np.abs(stats.zscore(df))

z

![image](https://github.com/user-attachments/assets/b9f79f81-93d5-47f8-bd6e-588b1e1f4664)

threshold=3

outliers = df[abs(df) > 3]

print("Outliers:")

print(outliers)

![image](https://github.com/user-attachments/assets/3d311b9b-005c-4041-b23f-062fa99e6812)

df_cleaned = df[(z <= threshold)]

df_cleaned

![image](https://github.com/user-attachments/assets/5ce9e2a0-d780-450e-8cbe-90df9bbde033)

sns.boxplot(df_cleaned)

![image](https://github.com/user-attachments/assets/e17daf87-f9ed-416b-87ae-1a30a66b4ac8)

sns.scatterplot(df_cleaned)

![image](https://github.com/user-attachments/assets/3ddf175f-646a-4db5-8026-ab0491d2f889)


# Result
          Thus the above code is execueted successfully...
