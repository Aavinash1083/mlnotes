---
title: "Scatterplot"
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
x = [1,2,3,4,5,6,7,8]
y = [5,2,4,2,1,4,5,2]

plt.scatter(x,y, label='skitscat Raggedy', color='k', s=25, marker="o")

plt.xlabel('x')
plt.ylabel('y')
plt.title('Interesting Graph\nCheck it out')
plt.legend()
plt.show()
```


![png](Scatterplot_2_0.png)



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


![png](Scatterplot_3_0.png)



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
