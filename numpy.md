# NumPy Cheat Sheet for AI Development

### Table of Contents
1. [Getting Started with NumPy Arrays](#getting-started-with-numpy-arrays)
2. [Array Indexing and Slicing](#array-indexing-and-slicing)
3. [Basic Operations and Broadcasting](#basic-operations-and-broadcasting)
4. [Mathematical Functions](#mathematical-functions)
5. [Linear Algebra with NumPy](#linear-algebra-with-numpy)
6. [Random Numbers and Data Simulation](#random-numbers-and-data-simulation)
7. [Reshaping and Resizing](#reshaping-and-resizing)
8. [Practical Applications in AI](#practical-applications-in-ai)

---

## 1. Getting Started with NumPy Arrays

```python
import numpy as np

# Create arrays
a = np.array([1, 2, 3])
zeros = np.zeros((2, 3))
ones = np.ones((3, 2))
full = np.full((3, 3), 7)
range_array = np.arange(0, 20, 2)
linspace_array = np.linspace(0, 1, 5)
```

## 2. Array Indexing and Slicing

```python
array = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

# Accessing elements
element = array[0, 1]  # 2
last_element = array[-1, -1]  # 9

# Slicing
submatrix = array[0:2, 0:2]  # [[1, 2], [4, 5]]
conditional = array[array > 4]  # [5, 6, 7, 8, 9]
```

## 3. Basic Operations and Broadcasting

```python
matrix1 = np.array([[1, 2, 3], [4, 5, 6]])
matrix2 = np.array([[10, 20, 30], [40, 50, 60]])

# Element-wise operations
add = matrix1 + matrix2
subtract = matrix1 - matrix2
multiply = matrix1 * matrix2
divide = matrix1 / matrix2

# Broadcasting
matrix3 = np.array([[1, 2, 3], [4, 5, 6]])
array1 = np.array([10, 20, 30])
broadcasted_add = matrix3 + array1
scalar_multiplication = matrix3 * 2
```

## 4. Mathematical Functions

```python
a = np.array([1, 2, 3, 4, 5])

# Exponentials and logarithms
exp = np.exp(a)
log = np.log(a)

# Square root and powers
sqrt = np.sqrt(a)
power = np.power(a, 3)

# Trigonometric functions
angles = np.array([0, np.pi/2, np.pi, 3*np.pi/2, 2*np.pi])
sin = np.sin(angles)
cos = np.cos(angles)
tan = np.tan(angles)
```

## 5. Linear Algebra with NumPy

```python
A = np.array([[1, 2], [3, 4]])
B = np.array([[2, 0], [1, 3]])

# Matrix multiplication
dot_product = np.dot(A, B)  # or A @ B

# Transpose
transpose = A.T

# Inverse and determinant
determinant = np.linalg.det(A)
inverse = np.linalg.inv(A)

# Eigenvalues and eigenvectors
eigenvalues, eigenvectors = np.linalg.eig(A)
```

## 6. Random Numbers and Data Simulation

```python
# Random numbers
random_floats = np.random.rand(3, 3)  # Uniform [0, 1)
random_integers = np.random.randint(1, 10, size=(3, 3))
normal_distribution = np.random.randn(3, 3)  # Mean 0, std 1

# Setting seed for reproducibility
np.random.seed(42)
```

## 7. Reshaping and Resizing

```python
a = np.arange(1, 13)  # [1, 2, ..., 12]

# Reshape to 3x4
reshaped = a.reshape(3, 4)

# Flatten
flattened = reshaped.flatten()

# Resize (in-place)
reshaped.resize((2, 6))  # Modifies reshaped to 2x6 shape
```

## 8. Practical Applications in AI

```python
# Normalizing data (scaling between 0 and 1)
data = np.array([[1, 2], [3, 4], [5, 6]])
normalized = (data - np.min(data)) / (np.max(data) - np.min(data))

# Generating mini-batches
batch_size = 2
for i in range(0, len(data), batch_size):
    batch = data[i:i + batch_size]
    # Process each batch independently
```
"""
