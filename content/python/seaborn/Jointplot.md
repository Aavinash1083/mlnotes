---
title: "Jointplot"
author: "Aavinash"
date: 2020-09-04
description: "-"
type: technical_note
draft: false
---

```python
import seaborn as sns
import matplotlib.pyplot as plt
plt.style.use('classic')
%matplotlib inline
import numpy as np
import pandas as pd
```


```python
rng = np.random.RandomState(0)
x = np.linspace(0, 10, 500)
y = np.cumsum(rng.randn(500, 6), 0)

```


```python
data = np.random.multivariate_normal([0, 0], [[5, 2], [2, 2]], size=2000)
data = pd.DataFrame(data, columns=['x', 'y'])
```


```python
with sns.axes_style('white'):
    sns.jointplot("x", "y", data, kind='kde');
```


![png](Jointplot_4_0.png)



```python
with sns.axes_style('white'):
    sns.jointplot("x", "y", data, kind='hex')
```


![png](Jointplot_5_0.png)



```python

```
