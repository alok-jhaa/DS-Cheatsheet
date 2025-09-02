NumPy is the foundation of scientific computing in Python, providing support for fast arrays, matrices, and numerical operations.

## Import
import numpy as np


## Array Creation
# From list
a = np.array([1, 2, 3])

# 2D array
b = np.array([[1, 2], [3, 4]])

# Zeros, Ones, Identity
np.zeros((2, 3))         # 2x3 zero matrix
np.ones((3, 3))          # 3x3 ones
np.eye(3)                # Identity matrix

# Ranges
np.arange(0, 10, 2)      # [0,2,4,6,8]
np.linspace(0, 1, 5)     # [0., 0.25, 0.5, 0.75, 1.]

# Random
np.random.rand(2, 3)     # uniform [0,1)
np.random.randn(2, 3)    # normal dist (mean=0, std=1)
np.random.randint(0, 10, (3, 3))  # ints


## Array Info
a.shape        # dimensions (rows, cols)
a.ndim         # number of dimensions
a.size         # total elements
a.dtype        # data type
a.itemsize     # size in bytes


## Indexing & Slicing
arr = np.array([10, 20, 30, 40, 50])

arr[0]        # first element
arr[-1]       # last element
arr[1:4]      # slice [20,30,40]
arr[:3]       # first 3
arr[::2]      # every 2nd element

# 2D
m = np.array([[1,2,3],[4,5,6],[7,8,9]])
m[0, 1]       # row0 col1 → 2
m[:, 0]       # first column
m[1, :]       # second row
m[0:2, 1:3]   # submatrix


## Operations
x = np.array([1,2,3])
y = np.array([4,5,6])

# Element-wise
x + y         # [5,7,9]
x * y         # [4,10,18]
x ** 2        # [1,4,9]

# Scalar
x + 10        # [11,12,13]
x * 2         # [2,4,6]

# Matrix
m1 @ m2       # matrix multiplication


## Useful Functions
np.sum(x)         # sum
np.mean(x)        # mean
np.median(x)      # median
np.std(x)         # standard deviation
np.var(x)         # variance
np.min(x), np.max(x)
np.argmin(x), np.argmax(x)  # index of min/max


## Reshape & Transpose
a = np.arange(12)        # [0..11]
a.reshape(3, 4)          # 3x4 matrix
a.ravel()                # flatten
a.T                      # transpose


## Stacking & Splitting
a = np.array([1,2])
b = np.array([3,4])

np.hstack([a,b])   # [1,2,3,4]
np.vstack([a,b])   # [[1,2],[3,4]]

m = np.arange(16).reshape(4,4)
np.hsplit(m, 2)    # split into 2 cols
np.vsplit(m, 2)    # split into 2 rows


## Boolean Indexing
arr = np.array([1,2,3,4,5])
mask = arr > 3
arr[mask]          # [4,5]

arr[arr % 2 == 0]  # even numbers


## Broadcasting
a = np.array([[1,2,3],[4,5,6]])
b = np.array([10,20,30])

a + b
# [[11,22,33],
#  [14,25,36]]


## Linear Algebra
from numpy.linalg import inv, eig, det

A = np.array([[1,2],[3,4]])

det(A)         # determinant
inv(A)         # inverse
eig(A)         # eigenvalues & vectors


## Saving & Loading
np.save("arr.npy", a)          # save binary
np.load("arr.npy")             # load binary

np.savetxt("arr.csv", a, delimiter=",")
np.loadtxt("arr.csv", delimiter=",")





