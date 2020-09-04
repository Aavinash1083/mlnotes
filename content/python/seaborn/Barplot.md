---
title: "Barplot"
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
names = np.array(data['names'])
hours = np.array(data['hours'])
dates = np.array(data['timestamp'])
```


```python
date_list = []
name_pair = []
time_interval = []
count = 0
name_pair_list = []
streak_list = []
time_interval_list = []
index = 0
for name in names:
    if len(name_pair) == 0:
        count += 1
        name_pair.append(name)
        date = dates[index]
        time_interval.append(hours[index])
    elif len(name_pair) == 1:
        count += 1
        if name not in name_pair:
            name_pair.append(name)
            if len(time_interval) == 2:
                time_interval[1] = hours[index]
            else:
                time_interval.append(hours[index])
    elif name in name_pair:
        time_interval[1] = hours[index]
        count += 1
    else:
        if count>49:
            streak_list.append(count)
            copy_pair = sorted(name_pair)
            name_pair_list.append((copy_pair[0], copy_pair[1]))
            time_interval_list.append((time_interval[0], time_interval[1]))
            date_list.append(date)
        count = 1
        name_pair.pop(0)
        time_interval.pop(0)
        name_pair.append(name)
        time_interval.append(hours[index])
        date = dates[index]
    index += 1
```


```python
data_streaks = pd.DataFrame({'Name Pairs':name_pair_list, 'Streak Counts':streak_list, 'Time Interval':time_interval_list, 'Timestamp':date_list})
data_streaks.sort_values(by='Streak Counts', ascending=False)
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
      <th>Name Pairs</th>
      <th>Streak Counts</th>
      <th>Time Interval</th>
      <th>Timestamp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>(Person1, Person4)</td>
      <td>493</td>
      <td>(22, 2)</td>
      <td>2020-05-31</td>
    </tr>
    <tr>
      <th>92</th>
      <td>(Person1, Person4)</td>
      <td>359</td>
      <td>(23, 0)</td>
      <td>2020-08-03</td>
    </tr>
    <tr>
      <th>5</th>
      <td>(Person1, Person4)</td>
      <td>316</td>
      <td>(18, 1)</td>
      <td>2020-05-28</td>
    </tr>
    <tr>
      <th>49</th>
      <td>(Person3, Person4)</td>
      <td>286</td>
      <td>(2, 4)</td>
      <td>2020-07-11</td>
    </tr>
    <tr>
      <th>45</th>
      <td>(Person1, Person4)</td>
      <td>213</td>
      <td>(21, 23)</td>
      <td>2020-07-08</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>48</th>
      <td>(Person1, Person4)</td>
      <td>51</td>
      <td>(23, 23)</td>
      <td>2020-07-10</td>
    </tr>
    <tr>
      <th>52</th>
      <td>(Person1, Person3)</td>
      <td>51</td>
      <td>(22, 23)</td>
      <td>2020-07-12</td>
    </tr>
    <tr>
      <th>104</th>
      <td>(Person1, Person4)</td>
      <td>51</td>
      <td>(17, 17)</td>
      <td>2020-08-12</td>
    </tr>
    <tr>
      <th>8</th>
      <td>(Person2, Person4)</td>
      <td>50</td>
      <td>(3, 10)</td>
      <td>2020-06-02</td>
    </tr>
    <tr>
      <th>36</th>
      <td>(Person1, Person3)</td>
      <td>50</td>
      <td>(11, 12)</td>
      <td>2020-06-29</td>
    </tr>
  </tbody>
</table>
<p>106 rows × 4 columns</p>
</div>




```python
plt.figure(figsize=(10,5))
axes = sns.barplot(x='Name Pairs', y ='Streak Counts', data=data_streaks, estimator=np.sum)
axes.set(ylabel='Sum of Streak Numbers')
axes.yaxis.set_major_formatter(formatter)
```


![png](Barplot_8_0.png)



```python

```
