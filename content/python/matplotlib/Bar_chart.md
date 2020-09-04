---
title: "Bar_chart"
author: "Aavinash"
date: 2020-09-04
description: "-"
type: technical_note
draft: false
---

```python
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

```


```python
plt.bar([1,3,5,7,9],[5,2,7,8,2], label="Example one")
plt.bar([2,4,6,8,10],[8,6,2,5,6], label="Example two", color='g')
plt.legend()
plt.xlabel('bar number')
plt.ylabel('bar height')

plt.title('Epic Graph\nAnother Line! Whoa')

plt.show()
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
      <th>names</th>
      <th>jan_ir</th>
      <th>feb_ir</th>
      <th>march_ir</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Nick</td>
      <td>123</td>
      <td>23</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Sani</td>
      <td>124</td>
      <td>24</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>John</td>
      <td>125</td>
      <td>25</td>
      <td>7</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Rubi</td>
      <td>126</td>
      <td>27</td>
      <td>6</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Maya</td>
      <td>128</td>
      <td>29</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python
korea_scores=(554,536,538)
canada_scores=(518,523,525)
china_scores=(413,570,580)
franch_scores=(495,505,499)
index=np.arange(3)
bar_width=.2
k1=plt.bar(index,korea_scores,bar_width,alpha=.9,label="Korea")
c1=plt.bar(index+bar_width,canada_scores,bar_width,alpha=.9,label="Canada")
ch1=plt.bar(index+bar_width*2,china_scores,bar_width,alpha=.9,label="China")
f1=plt.bar(index+bar_width*3,franch_scores,bar_width,alpha=.9,label="Franch")
plt.xticks(index+.6/2,('Mathematics','Reading','Science'))
plt.ylabel('Mean score in PISA in 2012')
plt.xlabel('Subjects')
plt.title('Test scores by Country')
plt.grid(True)
plt.legend()
plt.show()
```


![png](Bar_chart_3_0.png)



```python

```


```python

```


```python

```


```python

```


```python

```


```python


```


```python

```


```python


```
