---
title: "Dataframe_to_csv"
author: "Aavinash"
date: 2020-08-12
description: "-"
type: technical_note
draft: false
---

```python

import pandas as pd 

 
nme = ["aparna", "pankaj", "sudhir", "Geeku"] 
deg = ["MBA", "BCA", "M.Tech", "MBA"] 
scr = [90, 40, 80, 98] 

 
dict = {'name': nme, 'degree': deg, 'score': scr} 

df = pd.DataFrame(dict) 

 
df.to_csv('file1.csv') 

```


```python

import pandas as pd 

 
nme = ["aparna", "pankaj", "sudhir", "Geeku"] 
deg = ["MBA", "BCA", "M.Tech", "MBA"] 
scr = [90, 40, 80, 98] 
 
dict = {'name': nme, 'degree': deg, 'score': scr} 
df = pd.DataFrame(dict) 

df.to_csv('file2.csv', header=False, index=False) 

```


```python

import pandas as pd 


nme = ["aparna", "pankaj", "sudhir", "Geeku"] 
deg = ["MBA", "BCA", "M.Tech", "MBA"] 
scr = [90, 40, 80, 98] 

 
dict = {'name': nme, 'degree': deg, 'score': scr} 
df = pd.DataFrame(dict) 


df.to_csv(r'C:\Users\Admin\Home\pandas.csv', index=False) 

```


```python
import pandas as pd 
import numpy as np 
users = {'Name': ['Amit', 'Cody', 'Drew'], 
	'Age': [20,21,25]} 
df = pd.DataFrame(users, columns=['Name','Age'])#create DataFrame 
print("Original DataFrame:") 
print(df) 
print('Data from Users.csv:') 
df.to_csv('Users.csv', sep='\t', index=False,header=True) 
new_df = pd.read_csv('Users.csv') 
print(new_df) 

```

    Original DataFrame:
       Name  Age
    0  Amit   20
    1  Cody   21
    2  Drew   25
    Data from Users.csv:
      Name\tAge
    0  Amit\t20
    1  Cody\t21
    2  Drew\t25



```python

```
