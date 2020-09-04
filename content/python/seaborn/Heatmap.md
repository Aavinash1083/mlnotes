---
title: "Heatmap"
author: "Aavinash"
date: 2020-09-04
description: "-"
type: technical_note
draft: false
---

```python
import numpy as np 
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline

```


```python
data = pd.read_csv('Whatsapp_chat.csv', index_col=0)
data
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hours</th>
      <th>days</th>
      <th>months</th>
      <th>names</th>
      <th>timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>19</td>
      <td>May</td>
      <td>Person4</td>
      <td>2020-05-19</td>
    </tr>
    <tr>
      <th>1</th>
      <td>22</td>
      <td>19</td>
      <td>May</td>
      <td>Person3</td>
      <td>2020-05-19</td>
    </tr>
    <tr>
      <th>2</th>
      <td>22</td>
      <td>19</td>
      <td>May</td>
      <td>Person3</td>
      <td>2020-05-19</td>
    </tr>
    <tr>
      <th>3</th>
      <td>22</td>
      <td>19</td>
      <td>May</td>
      <td>Person1</td>
      <td>2020-05-19</td>
    </tr>
    <tr>
      <th>4</th>
      <td>22</td>
      <td>19</td>
      <td>May</td>
      <td>Person3</td>
      <td>2020-05-19</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>51570</th>
      <td>19</td>
      <td>12</td>
      <td>August</td>
      <td>Person3</td>
      <td>2020-08-12</td>
    </tr>
    <tr>
      <th>51571</th>
      <td>19</td>
      <td>12</td>
      <td>August</td>
      <td>Person1</td>
      <td>2020-08-12</td>
    </tr>
    <tr>
      <th>51572</th>
      <td>20</td>
      <td>12</td>
      <td>August</td>
      <td>Person3</td>
      <td>2020-08-12</td>
    </tr>
    <tr>
      <th>51573</th>
      <td>21</td>
      <td>12</td>
      <td>August</td>
      <td>Person1</td>
      <td>2020-08-12</td>
    </tr>
    <tr>
      <th>51574</th>
      <td>21</td>
      <td>12</td>
      <td>August</td>
      <td>Person1</td>
      <td>2020-08-12</td>
    </tr>
  </tbody>
</table>
<p>51575 rows × 5 columns</p>
</div>




```python
data.groupby('names').count()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>hours</th>
      <th>days</th>
      <th>months</th>
      <th>timestamp</th>
    </tr>
    <tr>
      <th>names</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Person1</th>
      <td>17543</td>
      <td>17543</td>
      <td>17543</td>
      <td>17543</td>
    </tr>
    <tr>
      <th>Person2</th>
      <td>3835</td>
      <td>3835</td>
      <td>3835</td>
      <td>3835</td>
    </tr>
    <tr>
      <th>Person3</th>
      <td>13514</td>
      <td>13514</td>
      <td>13514</td>
      <td>13514</td>
    </tr>
    <tr>
      <th>Person4</th>
      <td>16683</td>
      <td>16683</td>
      <td>16683</td>
      <td>16683</td>
    </tr>
  </tbody>
</table>
</div>




```python
from matplotlib import ticker
formatter = ticker.ScalarFormatter(useMathText=True)
formatter.set_scientific(True) 
formatter.set_powerlimits((3,3))
```


```python
plt.figure(figsize=(10,5))
sns.countplot(x='hours', data=data).yaxis.set_major_formatter(formatter) 
```


![png](Heatmap_5_0.png)



```python
data_by_date = data.groupby(['months', 'days']).count()
data_by_date
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>hours</th>
      <th>names</th>
      <th>timestamp</th>
    </tr>
    <tr>
      <th>months</th>
      <th>days</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="5" valign="top">August</th>
      <th>1</th>
      <td>1299</td>
      <td>1299</td>
      <td>1299</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1334</td>
      <td>1334</td>
      <td>1334</td>
    </tr>
    <tr>
      <th>3</th>
      <td>398</td>
      <td>398</td>
      <td>398</td>
    </tr>
    <tr>
      <th>4</th>
      <td>576</td>
      <td>576</td>
      <td>576</td>
    </tr>
    <tr>
      <th>5</th>
      <td>358</td>
      <td>358</td>
      <td>358</td>
    </tr>
    <tr>
      <th>...</th>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th rowspan="5" valign="top">May</th>
      <th>27</th>
      <td>423</td>
      <td>423</td>
      <td>423</td>
    </tr>
    <tr>
      <th>28</th>
      <td>541</td>
      <td>541</td>
      <td>541</td>
    </tr>
    <tr>
      <th>29</th>
      <td>175</td>
      <td>175</td>
      <td>175</td>
    </tr>
    <tr>
      <th>30</th>
      <td>1418</td>
      <td>1418</td>
      <td>1418</td>
    </tr>
    <tr>
      <th>31</th>
      <td>434</td>
      <td>434</td>
      <td>434</td>
    </tr>
  </tbody>
</table>
<p>83 rows × 3 columns</p>
</div>




```python
data_heat = data_by_date.pivot_table(values='hours', index='months', columns='days')
plt.figure(figsize=(30,4))
sns.heatmap(data_heat, cmap='rainbow').set(title='Message Density of Each Day')
```




    [Text(0.5, 1.0, 'Message Density of Each Day')]




![png](Heatmap_7_1.png)



```python

```
