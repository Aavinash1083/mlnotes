---
title: "Visualisations"
author: "Aavinash"
date: 2020-08-12
description: "-"
type: technical_note
draft: false
---

```python
import numpy as np 
import pandas as pd 
df1 = pd.read_csv('glass.csv', index_col = 0) 


```


```python
df1['Type'].hist() 

```




    <AxesSubplot:>




![png](Visualisations_2_1.png)



```python
import matplotlib.pyplot as plt 
plt.style.use('ggplot') 
df1['Type'].hist() 

```




    <AxesSubplot:>




![png](Visualisations_3_1.png)



```python
df1.plot.area(alpha = 0.4) 

```




    <AxesSubplot:xlabel='RI'>




![png](Visualisations_4_1.png)



```python
df1.plot.scatter(x ='Na', y ='Type') 

```




    <AxesSubplot:xlabel='Na', ylabel='Type'>




![png](Visualisations_5_1.png)



```python

```
