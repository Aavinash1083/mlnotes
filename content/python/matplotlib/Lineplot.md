---
title: "Lineplot"
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

iris=pd.read_csv('Iris.csv')
```


```python
plt.plot(iris['PetalLengthCm'], iris['PetalWidthCm'], linestyle='none', marker='o', color='b')
plt.show()
```


![png](Lineplot_3_0.png)



```python
x = np.linspace(0, 20, 1000)
y = np.cos(x)

plt.plot(x,y, color='b', linestyle='--')
plt.show()
```


![png](Lineplot_4_0.png)



```python

```
