# Numpy - Cheats 🧮

Axis: 0 = rows, 1 = columns (in 2D)

---
### Import
```python
import numpy as np

# Arrays
np.array([1,2,3])             # 1D-Array
np.array([(1,2,3),(4,5,6)])   # 2D-Array

# Generate Arrays
np.zeros((1,2))       # Array of '0's, also with ones
np.ones()

# Defined Space
np.arange(3,7,2)      # Range-Array
np.linspace(0,2,9)    # Evenly distributed

# Random elements
np.random.rand(4, 6)  # 4 rows, 6 columns

# Load data
X, Y = np.loadtxt("pizza.txt", skiprows=1, delimiter=',', unpack=True)

# Load Numpy-Array
np.load("./data.npy")
```

---
### Shape and Type
```python
# Size
a.size    # Number of Array Elements
a.shape   # Check Dimensions (Rows,Columns)
a.ndim    # Check Number of Dimensions

type(a)   # Type of array
len(a)    # Length of Array

# Typecasting
a.astype(type)  # Tranform into new datatype
a.dtype   # Data Type

# Shaping
a.flatten               # Collapse into one dimension
a.reshape(-1,)			# Change dimensions, size remains; -1 = "Take given dimension"
a.resize(2,3)			# resize an array in-place, filling with 0

a[None, :]				  # Add trivial dimension with single Row
a[:, None]				  # Add trivial dimension with single Column

np.expand_dims(a, axis=0) # Same as above
```

---
### Slicing
```python
a = np.random.rand(4, 6) 	# 4 rows, 6 columns

# Selecting
a[2][3]   	# Value at Row 2, Column 3 
a[2, :]	 	# Row 2
a[:, 3]		# Column 3
a[2, 3:]	# 
a[2, :3]

# Manipulating
a[2] = 0          # 3. Zeile alles 0
a[:, 3] += 10     # 4. Spalte alle + 10
```

---
### Filtering
```python
a = a < 4               # Normal Filter
a [a < 3]               # Boolean Index --> Returns elements

np.where(condition, a)  # Return List with markings
np.argwhere()           # Return indices of values
```

---
### Manipulate

##### Basic Operations
```python
# Sorting
a.sort()        # Sort values in array
np.flip(a)    	# Flip order in 1-D Array
bp.random.shuffle(a)

# Changing Elements
np.append(a, values)      # Append values a, b
np.insert(a, 1, 2, axis)  # Insert in a position
np.delete(a,1,axis)       # Delete from a position

# Copy an array
np.copy(a)      	# Copy array
other = a.copy()  	# Deep-Copy of Array

# Concatenate / Split an Array
np.vstack((a,b))                # Stack row-wise
np.hstack((a,b))                # Stack column-wise
np.column_stack((a,b))          

np.concatenate((a,b),axis=0)  #  End to End
```

##### Custom Functions
```python
np.apply_along_axis(np.sum, axis=0, arr=arr)
np.apply_over_axes(np.sum, arr, axes=(0, 1))
```

```python
# Fit a polynomial of degree 3 to the data
coeffs = np.polyfit(x, y, deg=3)

# Evaluate the polynomial at new points
x_new = np.linspace(-5, 5, 101)
y_new = np.polyval(coeffs, x_new)
```

##### Set Operations
```python
np.intersect1d(ar1,ar2)		# Retrieve common elements
np.setdiff1d(a, b)			# Difference of sets
np.setxor1d(a,b)			# Extract unique elements from both arrays
np.union1d(a,b)				# Union of sets
```

##### Mathematics & Statistics
```python
# One Array
np.sqrt(x)
np.sin(x)
np.cos(x)
np.log(x)

arr.sum()            # Sum of values in array
arr.sum(axis=0)      # Sum columns
arr.cumsum(axis=1)   # Cumulative sum of rows

# Two Arrays
np.add(x,y)
np.substract(x,y)
np.divide(x,y)
np.multiply(x,y)

np.dot(x,y) # Skalarprodukt / Dot-Product

# Basic Statistics
np.mean(data)           # Mean
np.median(data)         # Median
np.percentile(data, 25) # 25th percentile (median)
np.percentile(data, 50) # 50th percentile (median)
np.percentile(data, 75) # 75th percentile (median)
np.std(data)            # Standard-Deviation
np.var(data)            # Variance
a.corrcoef()        	# Correlation Coefficient
```

---
### Matrix Operations
```python
a.T					# Transpose

a.linalg.inv(a)		# Inverse Matrix
a.linalg.det(a)		# Determinante
a.linalg.norm(a)	# Determinante

# Multiplication
a * a	# Element-wise multiplication

# -- Skalar-Produkt
np.dot(a,a)		
v @ v 	# Vector-multiplication
a @ a	# Matrix multiplication 

# -- Kreuprodukt
np.cross(a,a)	
```

---
#### Vectorisation
- Use Vector-Operations instead of for-loops on single elements to save much time!!
```python
# Unvectorized
def gram(v):
	n = v.shape[0]
	g = np.empty((n, n))
	for i in range(n):
		for j in range(n):
			g[i, j] = v[i] @ v[j]   # inner product
	return g

# Vectorized
def fast_gram(v):
	return v @ v.transpose()   # matrix product
```

---
#### Broadcasting
- Defines how arithmetic operations are to be performed on arrays of unequal size
- Perform Operation on all elements of a vector
    - General Rule: *Compatible, if dim are equal or one of them is "1"*
```python
a = np.random.rand(4, 6)
a += np.ones(6)
a += np.ones((1, 6))

a += np.ones(4)			# Fehlermeldung
a += np.ones((4, 1))	# Korrekt

# Triviale Dimension hinzufügen
a = np.ones(5)
print(a)
print(a[None, :])
print(a[:, None])
```

---
### Export
```python
# Save as Binary Array
np.save("data.npy", X)
np.savez("data.npy", X,Y,Z)

# Save as Text
np.savetxt("data.txt", X, delimiter=",", fmt='%d') # To text
```

---
### Resources
- [Cheat Sheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Numpy_Python_Cheat_Sheet.pdf)
- [Visual Introduction](https://jalammar.github.io/visual-numpy/)
- [Another Visual Introduction](https://betterprogramming.pub/numpy-illustrated-the-visual-guide-to-numpy-3b1d4976de1d)
- [Broadcasting — NumPy v1.24 Manual](https://numpy.org/doc/stable/user/basics.broadcasting.html)

---