---
title: "Piechart"
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
data_temp = data['names'].value_counts()
data_temp
```




    Person1    17543
    Person4    16683
    Person3    13514
    Person2     3835
    Name: names, dtype: int64




```python

data_temp.plot.pie(figsize=(12,12), legend=False, autopct='%1.1f%%', shadow=True, explode=(0.05, 0, 0, 0)).set(ylabel='message ratios')
```




    [Text(0, 0.5, 'message ratios')]




![png](Piechart_5_1.png)



```python

```
