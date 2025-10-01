# NumPy and ML Cheat Sheet

## Table of Contents

* [Installation](#installation)
* [Data Types](#data-types)
* [Creating Arrays](#creating-arrays)
* [Inspecting Your Array](#inspecting-your-array)
* [Array Operations](#array-operations)
* [Compression](#compression)
* [Aggregate Functions](#aggregate-functions)
* [Copying Arrays](#copying-arrays)
* [Sorting Arrays](#sorting-arrays)
* [Indexing and Slicing](#indexing-and-slicing)
* [Linear Algebra](#linear-algebra)
* [Array Manipulation](#array-manipulation)
* [References](#references)

## Installation

```bash
pip install numpy
```

```python
import numpy as np
```

## Data Types

```python
np.int64  # Signed 64-bit integer type
np.float32  # Standard double-precision floating point
np.complex  # Complex numbers represented by 128 floats
np.bool  # Boolean type storing TRUE and FALSE values
np.object  # Python object type
np.string_  # Fixed-length string type
np.unicode_  # Fixed-length Unicode type

```

## Creating Arrays

```python
np.array([1, 2, 3]) # From a list
np.zeros(shape=(3, 3)) # Zeros array
np.ones(shape=(2, 4)) # Ones array
np.full(shape=(2,2), 10) # Constatnt array ([[10,10], [10, 10]])
np.eye(3) # Identity matrix

# Evenly spaced values (step value)
np.arange(10, 25, step=5) 
# Evenly spaced values (number of samples)
np.linspace(0, 9, num=100)

np.random.rand(3, 2) # Random array (with given shape)
# p.s: random numbers are in [0,1) range
np.random.randint(0, 10, size=(2, 3)) # Random integers array
```

## Inspecting Your Array

```python
a.shape # Shape of the array
len(a) # Length of the array
b.ndim # Number of dimensions of the array
e.size # Size of the array (total number of elements)
b.dtype # Data type of the array elements
b.dtype.name # Name of the data type
b.astype(int) # Convert the array to a different type
```

## Array Operations

```python
# Element-wise addition
arr + 2
arr1 + arr2
np.add(arr1, arr2) # Faster with Numpy function

# Element-wise subtraction
result = arr - 2
result = arr1 - arr2
np.subtract(arr1, arr2) # Faster with Numpy function

# Element-wise multiplication
result = arr * 2
result = arr1 * arr2
np.multiply(arr1, arr2) # Faster with Numpy function

# Element-wise division
result = arr / 2
result = arr1 / arr2
np.divide(arr1, arr2) # Faster with Numpy function

np.exp(arr)  # Exponential of each element in array
np.sqrt(arr)  # Square root of each element in array
np.sin(arr)  # Sine of each element in array
np.cos(arr)  # Cosine of each element in array
np.log(arr)  # Natural logarithm of each element in array
```

## Compression

```python
# Element-wise comparisons

# Equality
arr1 == arr2
np.equal(arr1, arr2)

# Inequality
arr1 != arr2
np.not_equal(arr1, arr2)

# Less-than
arr1 < arr2
np.less(arr1, arr2)

# Less-than or equal
arr1 <= arr2
np.less_equal(arr1, arr2)

# Closeness (useful for floating point comparisons)
np.isclose(arr1, arr2)
```

## Aggregate Functions

```python
np.sum(arr1)  # Sum of all elements
np.prod(arr1)  # Product of all elements in arr1
np.mean(arr1)  # Mean (average) of all elements
np.median(arr1)  # Median of all elements
np.min(arr1)  # Minimum value
np.max(arr1)  # Maximum value
np.argmin(arr1)  # Index of the minimum value
np.argmax(arr1)  # Index of the maximum value
np.std(arr1)  # Standard deviation of elements
np.var(arr1)  # Variance of elements

np.sum(arr1, axis=0)  # Sum (column-wise sum for 2D arrays)
np.sum(arr1, axis=1)  # Sum (row-wise sum for 2D arrays)

np.cumsum(arr1)  # Cumulative sum of elements
np.cumprod(arr1)  # Cumulative product of elements
np.percentile(arr1, 50)  # 50th percentile (median)
np.percentile(arr1, [25, 75])  # 25th and 75th percentiles

```

## Copying Arrays

```python
# deep copy
arr.copy()
np.copy(arr)

# shallow copy (view)
arr.view()
```

## Sorting Arrays

```python
np.sort(arr) # Sort elements in ascending order

# Sort along axis 0 (column-wise sort for 2D arrays)
np.sort(arr, axis=0)
# Sort along axis 1 (row-wise sort for 2D arrays)
np.sort(arr, axis=1)

# Returns the indices that would sort arr
np.argsort(arr)
# Perform an indirect sort using multiple arrays
# (arr2 is sorted first)
np.lexsort([arr1, arr2])
```

## Indexing and Slicing

```python
# Subsetting (Accessing an element)

arr[0]
arr[0,0]
```

```python
# Slicing

arr[start:end]  # (end is exclusive)
arr[:end]
arr[start:]

arr[start:end:step]

arr[::]  # (same as a full copy of the array)

arr[0, :]  # Entire first row of a 2D array
arr[:, 0]  # Entire first column of a 2D array

arr[1:4, 2:5]  # 1 to 4 (row), and 2 to 5 (column)
arr[:, 1:3]  # all rows but columns 1 to 3

arr[::2]  # All element (step size of 2)
arr[1::2]  # All element starting from index 1

arr[::-1]  # Reverse the array
```

```python
# Boolean indexing

arr[arr > 2]
```

```python
# np.where

np.where(arr > 2, a, 0) # set 0 to all bellow 2 values
```

## Linear Algebra

```python
# Dot product
np.dot(arr1, arr2)

# Matrix multiplication
np.matmul(arr1, arr2)

# Transpose
arr.T
np.transpose(arr)

# Unique elements
np.unique(arr)
```

## Array Manipulation

```python
# Change Array Shape

arr.reshape((2, 3)) # Reshape into 1 row and 3 columns

# -1 means determine columns automatically
np.reshape(arr, (2, -1))

arr.ravel() # Flatten
```

```python
# Adding / Removing Elements

np.append(arr1, arr2) # Append
np.insert(a, 1, 5) # Insert a
np.delete(arr, [index]) # Delete
```

```python
# Combine Arrays

np.concatenate((arr1, arr2), axis=0) # Concatenate

# Stack arrays vertically (row-wise)
np.vstack((arr1, arr2))
# Stack arrays horizontally (column-wise)
np.hstack((arr1, arr2))

# Stack arrays column-wise
# (columns form pairs of corresponding elements)
np.column_stack((arr1, arr2))

np.r_[arr1, arr2]  # (similar to np.concatenate)
np.c_[arr1, arr2]  # (similar to np.column_stack)
```

```python
# Splitting

# Split horizontally at the 3rd index
np.hsplit(arr, 3)
# Split vertically at the 2nd index
np.vsplit(arr, 2)
```

## References

* [NumPy Documentation](https://numpy.org/doc/)
* [NumPy Tutorial](https://www.w3schools.com/python/numpy_intro.asp)
* [NumPy Cheat Sheet](https://www.datacamp.com/community/blog/python-numpy-cheat-sheet)
