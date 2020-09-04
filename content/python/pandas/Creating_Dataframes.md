---
title: "Creating_Dataframes"
author: "Aavinash"
date: 2020-08-12
description: "-"
type: technical_note
draft: false
---

```python
import pandas as pd
```


```python
lst = ['Geeks', 'For', 'Geeks', 'is', 
            'portal', 'for', 'Geeks']
 
```


```python
df = pd.DataFrame(lst)
```


```python
df
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
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Geeks</td>
    </tr>
    <tr>
      <th>1</th>
      <td>For</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Geeks</td>
    </tr>
    <tr>
      <th>3</th>
      <td>is</td>
    </tr>
    <tr>
      <th>4</th>
      <td>portal</td>
    </tr>
    <tr>
      <th>5</th>
      <td>for</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Geeks</td>
    </tr>
  </tbody>
</table>
</div>




```python
data = {'Name':['Tom', 'nick', 'krish', 'jack'],
        'Age':[20, 21, 19, 18]}
```


```python

df = pd.DataFrame(data)
 
```


```python
df
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
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Tom</td>
      <td>20</td>
    </tr>
    <tr>
      <th>1</th>
      <td>nick</td>
      <td>21</td>
    </tr>
    <tr>
      <th>2</th>
      <td>krish</td>
      <td>19</td>
    </tr>
    <tr>
      <th>3</th>
      <td>jack</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>




```python
data = {'Name':['Jai', 'Princi', 'Gaurav', 'Anuj'],
        'Age':[27, 24, 22, 32],
        'Address':['Delhi', 'Kanpur', 'Allahabad', 'Kannauj'],
        'Qualification':['Msc', 'MA', 'MCA', 'Phd']}
```


```python
df = pd.DataFrame(data)
```


```python
print(df[['Name', 'Qualification']])
```

         Name Qualification
    0     Jai           Msc
    1  Princi            MA
    2  Gaurav           MCA
    3    Anuj           Phd



```python

```
