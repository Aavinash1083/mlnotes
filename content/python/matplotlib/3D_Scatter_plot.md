---
title: "3D_Scatter_plot"
author: "Aavinash"
date: 2020-09-04
description: "-"
type: technical_note
draft: false
---

```python
import matplotlib.pyplot as plt
_ = plt.hist(data, bins=10, color='lightblue',
             label=lbl, density=True, ec='white')
plt.legend()
plt.title("Target variable distribution", fontdict={'fontsize': 19,
          'fontweight':0.5 }, pad=15)
plt.xlabel("Target Bins")
plt.ylabel("Probability");
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-5-27fcb3254561> in <module>
          1 import matplotlib.pyplot as plt
    ----> 2 _ = plt.hist(data, bins=10, color='lightblue',
          3              label=lbl, density=True, ec='white')
          4 plt.legend()
          5 plt.title("Target variable distribution", fontdict={'fontsize': 19,


    NameError: name 'data' is not defined



```python
import matplotlib.pyplot as plt
from SWMat.SWMat import SWMat
swm = SWMat(plt) # Initialize your plot
swm.hist(data, bins=10, highlight=[2, 9])
swm.title("Carefully looking at the dependent variable revealed some problems that might occur!")
swm.text("Target is a bi-model dependent feature.\nIt can be <prop fontsize='18' color='blue'> hard to predict.<\prop>");
# Thats all! And look at your plot!!
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-6-f0938510cd94> in <module>
          2 from SWMat.SWMat import SWMat
          3 swm = SWMat(plt) # Initialize your plot
    ----> 4 swm.hist(data, bins=10, highlight=[2, 9])
          5 swm.title("Carefully looking at the dependent variable revealed some problems that might occur!")
          6 swm.text("Target is a bi-model dependent feature.\nIt can be <prop fontsize='18' color='blue'> hard to predict.<\prop>");


    NameError: name 'data' is not defined



![png](3D_Scatter_plot_2_1.png)



```python

```
