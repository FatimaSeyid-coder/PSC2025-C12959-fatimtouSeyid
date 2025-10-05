# Summary of book **Scientific Computing with Python**

## Chapter 4: Linear Algebra - Arrays 

This chapter of the book introduces Linear Algebra or arrays, which are essential for working with vectors and matrices. The package **NumPy** gives the necessary tools to build and manipulate the arrays.  

###
1. **Introduction**
To manipulate the arrays, calling the package **NumPy** using this following way in all the python files is recommanded:

```python

from numpy import *

```
2. **NumPy Arrays**
NumPy's `arrays` are used to build and manipulate the vectors and matrices.

- **Creating vectors and matrices**
```python

from numpy import *

v = array([1, 2])
#a vector with 2 components

M = array([[1.,2],[0.,1]])
#a matrix has a similar way in creation as a vector but with a list of lists

```

- **Basic array operations**
```python

from numpy import *

# two vectors with three components
v1 = array([1., 2., 3.])
v2 = array([2, 0, 1.])

# scalar multiplications/divisions
2*v1 # array([2., 4., 6.])
v1/2 # array([0.5, 1., 1.5])

# linear combinations
3*v1 # array([ 3., 6., 9.])
3*v1 + 2*v2 # array([ 7., 6., 11.])

# elementwise operations:
v1 * v2 # array([2., 0., 3.])
v2 / v1 # array([2.,0.,.333333])
v1 - v2 # array([-1., 2., 2.])/
v1 + v2 # array([ 3., 2., 4.])

# scalar product
dot(v1, v2) # 5.
v1 @ v2 # 5

# norm
from numpy.linalg import norm

norm(v1) # 3.7416573867739413

```
the `norm` function (from `numpy.linalg`) computes the Euclidean norm of a vector.

$$
\|v_1\| = \sqrt{x_1^2 + x_2^2 + \dots + x_n^2}
$$

- **Shape and number of dimensions**
`shape()` and `reshape()` are ones of the most important functions in arrays for the vectors and marices.
Note that `n` vector, `n x 1` vector and `1 x n` matrix are three different objects even if they contains same data.
```python

from numpy import *

v = array([1., 2., 1.])
v array([1., 2., 1.])
shape(v) #(3,) this is a vector


R = v.reshape((1,3))
R #array([[1., 2., 1.]])
shape(R) #(1, 3) this is a row matrix

C = v.reshape((3, 1))
C #array([[1.],
   #      [2.],
  #       [1.]])
shape(C) #(3, 1) this is a column matrix

```

- **Indexing and slicing**
To index and to to slice an array is similar to in lists.
```python

from numpy import *

v = array([1., 2., 3])
M = array([[1., 2],[3., 4]])

v[0] #1.0
v[1:] # array([2., 3.])
v[0] = 10 #array([10.,  2.,  1.])
v[:2] #array([10.,  2.])
v[:2] = [0, 1] #array([0., 1., 1.])
v[:2] = [1, 2, 3] #error! because the v[:2] has the shape (2,) not (3,)

M[0] # array([1., 2.]) 
M[0, 0] #1.0
M[1:] # the matrice array([[3., 4]])
M[1] # the vector array([3., 4.])

```

- **Linear algebra operations**

    - The scalar product is an essential operator in linear algebra. It is used in matrix-vector multiplications, vector-vector products, and matrix-matrix products. In Python, the `dot()` function or the `@` operator can be used for these operations.

    ```python
    from numpy import *

    # vector-vector scalar product
    v = array([1, 2])
    w = array([3, 4])
    dot(v, w)    # 1*3 + 2*4 = 11
    v @ w        # also returns 11
    # result : scalar

    # matrix-vector multiplication
    M = array([[1, 0],
                [0, 1]])
        v = array([5, 10])
    dot(M, v)    # array([5, 10])
    M @ v        # same: array([5, 10])
    # result : vector

    # matrix-matrix multiplication
    A = array([[1, 2],
                [3, 4]])
    B = array([[2, 0],
                [1, 2]])
    dot(A, B)    # array([[ 4,  4],
                    #        [10,  8]])
    A @ B        # same result
    # result : matrix

    ```

    - The function `solve()` from `numpy.linalg` is used to solve system equations in linear algebra.
    - The function `allclose()` checks if the computed result is close enough to the expected result
    For example for the system **Ax = b** where `A` is a matrix and `b` is a vector, so `x` should be a vector  because matrix-vector multiplication gives a vector result:

    ```python
    from numpy import *
    from numpy.linalg import solve, allclose

    A = array([[1., 2.],
                [3., 4.]])
    b = array([1., 4.])

    x = solve(A, b)  # Solves the system A @ x = b 
    x # array([ 2. , -0.5])
    # Check if the solution is correct
    allclose(dot(A, x), b)  # returns True
    allclose(A @ x, b)      # also returns True
    ```
3. **Arrays as mathmatical functions**
Think of arrays like mathematical functions:

- A **scalar** is like a function with no arguments.

- A **vector** is like a function with one argument.

- A **matrix** is a function with two arguments.

- A **tensor** (higher-order array) is a function with more than two arguments.

4. **Array properties**
Arrays are essentially characterized by three properties:
- `shape`: Describes the dimensions of the array (e.g. **1D vector**, **2D matrix**). It tells how the data is structured and accessed. 
- `dtype`: Specifies the type of data stored in the array (e.g. `int`, `float64`, `complex`, etc). Ensures efficient storage and computation.
- `strides`: Defines **how many bytes** to skip in memory to move to the next row or column. It controls memory layout and enables fast views or reshaping without copying data.
```python
    from numpy import *

    A = array([[1, 2, 3], [3, 4, 6]])
    A.shape # (2, 3)
    A.dtype # dtype('int64')
    A.strides # (24, 8)

```
5. **Data Types in Array creation**
When creating arrays, **NumPy** chooses a `dtype` based on input values unless you specify one explicitly.

- The chosen `dtype` is **fixed** — you can’t change it later by assigning different types.

- NumPy will **silently cast values** if needed.

```python
    from numpy import *

    A = array([1., 2.], dtype=complex) # complex128
                  
    # Type inference
    array([1, 2])          # int
    array([1., 2])         # mix float/integer -> float
    array([1.+0j, 2.])     # mix float/complex -> complex

    # Type casting example
    B = array([1, 2, 3])   # dtype = int
    B[0] = 0.5
    B               # array([0, 2, 3])
```
- When creating an array from a list, you can specify the dtype explicitly. 

```python
    from numpy import *

    # Inferred dtype from list
    V = array([1., 2., 1.])
    V.dtype           # dtype('float64')

    # Explicitly specifying dtype
    V = array([1., 2., 1.], dtype=complex)
    V.dtype           # dtype('complex128')
```

6. **Accessing and Modifying Array Entries**
NumPy allows flexible and powerful access to individual elements and subarrays using indexing and slicing.

- Accessing Arrays Elements
Use `M[i, j]` to access the element of an array at row `i` and column `j`.

```python
    from numpy import *

    M = array([[1., 2.],
                [3., 4.]])

    M[0, 0]     # 1.0 → first row, first column
    M[-1, 0]    # 3.0 → last row, first column

```
- Slicing Arrays
    - `M[i, :]` all columns of the i-th row (returns a row vector)
    - `M[:, j]` all rows of the j-th column (returns a column vector)
    - `M[2:4, :]` rows 2 to 3 (slice of rows only)
    - `M[2:4, 1:4]` rows 2 to 3 and columns 1 to 3 (submatrix)

```python
    from numpy import *

    M = array([[ 0,  1,  2,  3],
                [ 4,  5,  6,  7],
                [ 8,  9, 10, 11]])
                # dtype('complex128')

    M[1, :]        # array([4, 5, 6, 7])
    M[:, 1]        # array([1, 5, 9])
    M[1:2, 1:2]    # array([[5]])
    M[:2, 1:-1]    # array([[1, 2], [5, 6]])     

```
- Array Attributes 
    - `M.shape` dimensions of the array (rows, columns)

    - `M.ndim` number of dimensions

    - `M.size` total number of elements

- Altering Arrays USing Slices
```python
    from numpy import *

    M[1, :] = [10, 11, 12, 13]    # Replaces the entire 2nd row
    M[:, 0] = 99                  # Replaces the 1st column with 99
    M[0:2, 1:3] = [[1, 2], [3, 4]]  # Replaces 2x2 block
   
```  
7. **Functions to construct arrays**
`NumPy` provides several convenient functions to create arrays with specific shapes and contents.
```python
    from numpy import *

    zeros((n, m))        # Creates an n×m array filled with 0.0
    ones((n, m))         # Creates an n×m array filled with 1.0
    full((n, m), q)      # Creates an n×m array filled with value q
    diag(v, k=0)         # Constructs a diagonal matrix from vector v
    random.rand(n, m)    # Array of shape (n, m) with random floats in [0, 1)
    arange(n)            # Array with values [0, 1, ..., n-1]
    linspace(a, b, n)    # n values linearly spaced from a to b (inclusive)

```  
There are also `*_like()` variants that construct arrays with the same shape and dtype as an existing array
```python
    from numpy import *

    A = array([[1, 2], [3, 4]])
    zeros_like(A)   # array([[0, 0], [0, 0]])
    ones_like(A)    # array([[1, 1], [1, 1]])
 
```  
8. **Accessing and Changing the Shape of Arrays**
`NumPy` arrays have flexible shape and dimension manipulation tools.
- The function `shape()`
```python
    from numpy import *

    A = array([[1, 2, 3],
           [4, 5, 6]])

    shape(A)     # (2, 3) -> 2 rows, 3 columns

    A.shape   # (2, 3) it can be used as an attribute

``` 
So the different between using `shape` as a function of an attribute is that using it as a function if 
###