---
title: "Date_Time_Functions"
author: "Aavinash"
date: 2020-08-12
description: "-"
type: technical_note
draft: false
---

```python
import pandas as pd 
  
# Create dates dataframe with frequency   
data = pd.date_range('1/1/2011', periods = 10, freq ='H') 
  
data 
```




    DatetimeIndex(['2011-01-01 00:00:00', '2011-01-01 01:00:00',
                   '2011-01-01 02:00:00', '2011-01-01 03:00:00',
                   '2011-01-01 04:00:00', '2011-01-01 05:00:00',
                   '2011-01-01 06:00:00', '2011-01-01 07:00:00',
                   '2011-01-01 08:00:00', '2011-01-01 09:00:00'],
                  dtype='datetime64[ns]', freq='H')




```python
# Create date and time with dataframe 
rng = pd.DataFrame() 
rng['date'] = pd.date_range('1/1/2011', periods = 72, freq ='H') 
  
# Print the dates in dd-mm-yy format 
rng[:5] 
  
# Create features for year, month, day, hour, and minute 
rng['year'] = rng['date'].dt.year 
rng['month'] = rng['date'].dt.month 
rng['day'] = rng['date'].dt.day 
rng['hour'] = rng['date'].dt.hour 
rng['minute'] = rng['date'].dt.minute 
  
# Print the dates divided into features 
rng.head(3)
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
      <th>date</th>
      <th>year</th>
      <th>month</th>
      <th>day</th>
      <th>hour</th>
      <th>minute</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2011-01-01 00:00:00</td>
      <td>2011</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2011-01-01 01:00:00</td>
      <td>2011</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2011-01-01 02:00:00</td>
      <td>2011</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
import pandas as pd 
  
url = 'http://bit.ly/uforeports'
  
# read csv file 
df = pd.read_csv(url)            
df.head() 
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
      <th>City</th>
      <th>Colors Reported</th>
      <th>Shape Reported</th>
      <th>State</th>
      <th>Time</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Ithaca</td>
      <td>NaN</td>
      <td>TRIANGLE</td>
      <td>NY</td>
      <td>6/1/1930 22:00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Willingboro</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>NJ</td>
      <td>6/30/1930 20:00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Holyoke</td>
      <td>NaN</td>
      <td>OVAL</td>
      <td>CO</td>
      <td>2/15/1931 14:00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abilene</td>
      <td>NaN</td>
      <td>DISK</td>
      <td>KS</td>
      <td>6/1/1931 13:00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>New York Worlds Fair</td>
      <td>NaN</td>
      <td>LIGHT</td>
      <td>NY</td>
      <td>4/18/1933 19:00</td>
    </tr>
  </tbody>
</table>
</div>




```python

# Convert the Time column to datatime format 
df['Time'] = pd.to_datetime(df.Time) 
  
df.head() 
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
      <th>City</th>
      <th>Colors Reported</th>
      <th>Shape Reported</th>
      <th>State</th>
      <th>Time</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Ithaca</td>
      <td>NaN</td>
      <td>TRIANGLE</td>
      <td>NY</td>
      <td>1930-06-01 22:00:00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Willingboro</td>
      <td>NaN</td>
      <td>OTHER</td>
      <td>NJ</td>
      <td>1930-06-30 20:00:00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Holyoke</td>
      <td>NaN</td>
      <td>OVAL</td>
      <td>CO</td>
      <td>1931-02-15 14:00:00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Abilene</td>
      <td>NaN</td>
      <td>DISK</td>
      <td>KS</td>
      <td>1931-06-01 13:00:00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>New York Worlds Fair</td>
      <td>NaN</td>
      <td>LIGHT</td>
      <td>NY</td>
      <td>1933-04-18 19:00:00</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
