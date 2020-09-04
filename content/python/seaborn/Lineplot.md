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
data_by_timestamp = data[['timestamp', 'names']].value_counts().unstack(level=1).fillna(0)
data_by_timestamp
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
      <th>names</th>
      <th>Person1</th>
      <th>Person2</th>
      <th>Person3</th>
      <th>Person4</th>
    </tr>
    <tr>
      <th>timestamp</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2020-05-19</th>
      <td>5.0</td>
      <td>0.0</td>
      <td>3.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2020-05-20</th>
      <td>0.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2020-05-22</th>
      <td>4.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2020-05-25</th>
      <td>128.0</td>
      <td>7.0</td>
      <td>46.0</td>
      <td>105.0</td>
    </tr>
    <tr>
      <th>2020-05-26</th>
      <td>200.0</td>
      <td>7.0</td>
      <td>145.0</td>
      <td>144.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2020-08-08</th>
      <td>125.0</td>
      <td>1.0</td>
      <td>84.0</td>
      <td>150.0</td>
    </tr>
    <tr>
      <th>2020-08-09</th>
      <td>82.0</td>
      <td>5.0</td>
      <td>129.0</td>
      <td>153.0</td>
    </tr>
    <tr>
      <th>2020-08-10</th>
      <td>309.0</td>
      <td>58.0</td>
      <td>241.0</td>
      <td>288.0</td>
    </tr>
    <tr>
      <th>2020-08-11</th>
      <td>139.0</td>
      <td>40.0</td>
      <td>108.0</td>
      <td>151.0</td>
    </tr>
    <tr>
      <th>2020-08-12</th>
      <td>235.0</td>
      <td>9.0</td>
      <td>110.0</td>
      <td>157.0</td>
    </tr>
  </tbody>
</table>
<p>83 rows × 4 columns</p>
</div>




```python
plt.figure(figsize=(20,10))
'''ax = sns.lineplot(dat
ax = sns.lineplot(data=data_by_timestamp)
ax.xaxis.set_ticks(np.arange(0, 100, 10))
ax
```
