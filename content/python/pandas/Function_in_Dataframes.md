---
title: "Function_in_Dataframes"
author: "Aavinash"
date: 2020-08-12
description: "-"
type: technical_note
draft: false
---

```python
# Import pandas package 
import pandas as pd 

# Function to add 
def add(a, b, c): 
	return a + b + c 

def main(): 
	
	# create a dictionary with 
	# three fields each 
	data = { 
			'A':[1, 2, 3], 
			'B':[4, 5, 6], 
			'C':[7, 8, 9] } 
	
	# Convert the dictionary into DataFrame 
	df = pd.DataFrame(data) 
	print("Original DataFrame:\n", df) 
	
	df['add'] = df.apply(lambda row : add(row['A'], 
					row['B'], row['C']), axis = 1) 

	print('\nAfter Applying Function: ') 
	# printing the new dataframe 
	print(df) 

if __name__ == '__main__': 
	main() 

```

    Original DataFrame:
        A  B  C
    0  1  4  7
    1  2  5  8
    2  3  6  9
    
    After Applying Function: 
       A  B  C  add
    0  1  4  7   12
    1  2  5  8   15
    2  3  6  9   18



```python
# Import pandas package 
import pandas as pd 

def normalize(x, y): 
	x_new = ((x - np.mean([x, y])) /
			(max(x, y) - min(x, y))) 
	
	# print(x_new) 
	return x_new 

def main(): 
	
	# create a dictionary with three fields each 
	data = { 
		'X':[1, 2, 3], 
		'Y':[45, 65, 89] } 
	
	# Convert the dictionary into DataFrame 
	df = pd.DataFrame(data) 
	print("Original DataFrame:\n", df) 
	
	df['X'] = df.apply(lambda row : normalize(row['X'], 
								row['Y']), axis = 1) 

	print('\nNormalized:') 
	print(df) 

if __name__ == '__main__': 
	main() 

```

    Original DataFrame:
        X   Y
    0  1  45
    1  2  65
    2  3  89
    
    Normalized:
         X   Y
    0 -0.5  45
    1 -0.5  65
    2 -0.5  89



```python
import pandas as pd 
import numpy as np 

pd.options.mode.chained_assignment = None

# Function to generate range 
def generate_range(n): 
	
	# printing the range for eg: 
	# input is 67 output is 60-70 
	n = int(n) 
	
	lower_limit = n//10 * 10
	upper_limit = lower_limit + 10
	
	return str(str(lower_limit) + '-' + str(upper_limit)) 
	
def replace(row): 
	for i, item in enumerate(row): 
		
		# updating the value of the row 
		row[i] = generate_range(item) 
	return row 
		

def main(): 
	# create a dictionary with 
	# three fields each 
	data = { 
			'A':[0, 2, 3], 
			'B':[4, 15, 6], 
			'C':[47, 8, 19] } 
	
	# Convert the dictionary into DataFrame 
	df = pd.DataFrame(data) 

	print('Before applying function: ') 
	print(df) 
	
	# applying function to each row in 
	# dataframe and storing result in a new coloumn 
	df = df.apply(lambda row : replace(row)) 
	

	print('After Applying Function: ') 
	# printing the new dataframe 
	print(df) 

if __name__ == '__main__': 
	main() 

```

    Before applying function: 
       A   B   C
    0  0   4  47
    1  2  15   8
    2  3   6  19
    After Applying Function: 
          A      B      C
    0  0-10   0-10  40-50
    1  0-10  10-20   0-10
    2  0-10   0-10  10-20



```python

```
