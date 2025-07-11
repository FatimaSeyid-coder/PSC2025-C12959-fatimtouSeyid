# Summary of book **Scientific Computing with Python**

## Chapter 1: Getting Started 

This chapter of the book introduces foundational Python concepts for basic syntax of pyton.

### Key Sections:
1. **Introduction**

The book recommande the use of **python 3.7 (or later version)** and **Anaconda**, an open-source **Python distribution** .

2. **Installation and Configuration**

After explaining the installation of the **Anaconda** distribution, whitch incluses **Python**, **IPython**(The Python shell) **Spyder**(A Python-related editor), **Jupyter Notebooks** and key libratries(e.g: **SciPy** with **NumPy** for scientific computing and **matplotlib** for the graphical representationof mathmatical results). They also explain how to call the librairis and recommande the use of the following header in all of the Python files:

```python

from numpy import *
from matplotlib.pyplot import *

```
3. **Python Basic Syntax**
Key elements of Python basic syntax are introduced: 
- Comments: everything following this symbol `#` is considered as a comment.
```python

# This is a comment

```
- Data types in Python: 
    - Number: it can be an integer, a real number, or a complex number. The usual operations for numbers are like: `+` for Addition, `-` for Subtraction, `*` for Multiplication, `\` for Division and `**` for power.
    ```python

    2 ** (2 + 2) # 16
    1j ** 2 # -1
    1. + 3.0j 
    # the symbol j here is a complex number not a variable

    ```    
    - String: it is a sequence of characters, it can declared by single or double quotes
    ```python

    'valid string with single quote'
    "valid string with double quotes"

    ```  
    - Variable: it is a reference to an object, the assignment operator `=` is used to assign a value to a variable.
    ```python

    x = 3
    y = 'hello word!'
    z = x # the object z now is = 3
    l = [1,2,3] # l is a list object 
    print(l) # we can get the variable on the screen by the operation print()
    ```  
    - Liste: it is a very useful construction in basic data types of Python, it is defined by  square brackets, and to access to the elements of a list zero-based indexes inside square brackets is used:
    ```python

    L1 = [1, 2, 3, 4, 5]
    L1[0] #1
    L1[2] #3
    L1[-1] #5
    L1[-3] #3

    #a list can contain any data type inside its elements
    L2 = ['a', 'b', 4, [5,0]]
    L2[-1] # [5,0]
    L2[4] [1] #0

    #len() is a function that gives the length of a list
    len(L2) #returns 4
    len(L1) #returns 5

    #append() is used to add an element to a list
    L2.append('y') 
    L2 # L2 is now like L2 = ['a', 'b', 4, [5,0], 'y']
    L2[-1] # 'y'

    #to conactenate two lists the operator + is used
    L3 = [1, 2]
    L4 = [3, 4]
    L = L3 + L4 # [1, 2, 3, 4]

    #to concatenate a list by itself n times, multiplying it by the integer n is used
    4 * L3 #[1, 2, 1, 2, 1, 2, 1, 2]
    ```  
    - Boolean expressions: it is an expression with `True` or `False` value. The operations in the boolean expressions are: `==` for equal, `!=` for not equal, `<` for strict less, `<=` foe less or equal, `>` for strict greater and `>=` foe greater or equal. For combinate different boolean values `or` and `and` are used.
    ```python

    2 >= 4 # False
    2 < 3 < 4 # True
    2 < 3 and 3 < 2 # False
    2 != 3 < 4 or False # True
    2 <= 2 and 2 >= 2 # True

    # The keyword 'not' gives the logical negation of the expression that follows.
    not 2 == 3 # True 
    ```  

- Repeating statements with loops(for, break, else)
    Loops are used to repeat a task for a sequence of statements in many iterations.

    ```python

     L = [1, 2, 10]
    for s in L:
        print(s * 2)  # returns 2, 4, 20

    ```  
    - Iteration

    ```python
    n = 30
    for iteration in range(n):
        ... # a statement here gets executed n times
    
    ```   
    - `break`, it stops the loop early when a condition is met.

    ```python
    x_values=[0.5, 0.7, 1.2]
    threshold = 0.75
    for x in x_values:
        if x > threshold:
            break
    print(x)
    
    # returns 0.5 0.7 the values below the threshold <0,75
    ``` 
    - `else`, it runs only if the loop wasn’t broken.
    ```python
    x_values=[0.5, 0.7]
    threshold = 0.75
    for x in x_values:
        if x > threshold:
            break
    print(x)
    else:
    print("All values are below threshold")

    # returns 0.5 0.7 All values are below threshold
    ``` 

- Conditional statements(if, else) branch the code based on a condition.
    ```python
    
    x = -3
    if x >= 0:
        print(x)
    else:
        print(-x)
    # returns 3


    ``` 

- Functions group reusable code. Defined using `def`, with input parameters and a return value. Functions are useful for organize the code.
    ```python
    
    def f(x):
    return 2 * x + 1

    print(f(2))  # returns 5

    ``` 

- Scripts & modules
    - A script is a Python file (.py) containing code you can run.
    - A module is a script that stores functions and variables to be reused.

    ```python
    
    # smartfunctions.py
    def f(x):
        return 2 * x + 1

    # In another script or IPython:
    import smartfunctions
    from smartfunctions import f
    print(f(2))  # returns 5

    ``` 

- Python Interpreter
    - Before running, it checks the syntax.
    - Then, Python executes the code line by line.
    - The code inside a def is not executed until the function is called.
    ```python
    
    def f(x):
        return y**2  # No error yet

    a = 3  # Still no error
    # Both a and f are defined
    f(2)   # Error happens here (y is not defined)

    ``` 
###    

## Chapter 2: Variables and Basic Types

This chapter of the book explores the most important basic data types, including  variables, numeric types, booleans, and strings. It also introduces thpse data types representation and all possible operations on them.

### Key Sections:
1. **Variables**
- A variable is a name that refers to a Python object. It is created using assignment `=`.
```python
    
    x = 3        # integer
    y = 'hello'  # string
    L = [1, 2, 3, 4] #list

``` 
- Variable names in python are case-sensitive. It consists of any combination of capital or/and small letters, underscoer `_` and numbers, and must not begin with a number.
- You can assign the same value to multiple variables.
```python
    
    a = b = c = 1 # a, b and c get the same value 1

``` 
- Variable can updated afterits definition easly with the operations
```python
    
    a = 1
    a = a + 1 # a gets the value 2
    a = 3 * a # a gets the value 6

    a += 1 # same as a = a + 1
    a *= 3 # same as a = 3 * a

``` 
2. **Numeric types**
In Python, there are many number types: Integers, float and complex.
- **Integers**: whole the numbers of the entire `Z`.
```python
    
    7 // 2  # 3 // returns an integer
    7 / 2   # 3.5 /can return a float

``` 
- **Float numbers**: The numbers of the entire `R` and `Q`.
```python
    
    a = 3.0
    print(type(a)) # returns <class 'float'>
     
    b = 30.e-1 # a= 30.0 x 10^(-1)

    0.4 - 0.3 # returns 0.10000000000000003

    0.4 - 0.3 == 0.1 # returns False 0.1 != 0.10000000000000003


``` 
- **Complex Numbers**: The numbers of the entire `C`.

3. **Booleans**
- Boolean variables can take only: `True` or `False`.
```python
    
    x = 5
    print(x > 0)  # True

``` 
- Common logical operators in boolean variables are: `and`, `or` and `not`.
```python
    
    True and False # False
    False or True # True
    (30 > 45) or (27 < 30) # True
    not True # False
    not (3 > 4) # True

``` 
4. **Strings**
- Sequences of characters inside `' '`, `" "` or `""" """`.
```python
    
    name = 'Johan Carlsson'
    child = "Åsa is Johan Carlsson's daughter"
    book = """Aunt Julia
            and the Scriptwriter"""

    book[-1] # returns 'r'
    book[-12:] # returns 'Scriptwriter'

``` 
- Strings are immutable, so the value it can't change after it's created. 
```python
    
    book = "hello"
    print(book[1])     # returns 'e' (you can access the character)

    book[1] = 'a'      # ERROR: TypeError: 'str' object does not support item assignment (you can not updated it)

``` 

- Common operations on strings:
    - Concatenation:
    ```python
    
    last_name = 'Carlsson'
    first_name = 'Johanna'
    full_name = first_name + ' ' + last_name
    # returns 'Johanna Carlsson'

    ``` 
    - Repetition:
    ```python
    
    game = 2 * 'Yo' # returns 'YoYo'

    ``` 
    - Comparison:
    ```python
    
    'Anna' > 'Arvi' # returns false
    'ANNA' < 'anna' # returns true
    '10B' < '11A' # returns true because '0' < '1'

    ``` 
 ###

## Chapter 3: Container Types

This chapter of the book introduces the container types: lists, arrays, tuples, dictionaries and sets. These structures allow you to store and manipulate groups of values efficiently.

### Key Sections:
1. **Listes**: the most used container datatype in python, a list is a collection of elements of any kind.
```python
    
    numbers = [100, 300, 500]
    fruits = ['apple', 'banana', 'watermellon']
    mixed = [1, 3.0, 'text', [1,2], [a, b, c]]

    L = ['a', 20.0, 5]
    M = [3,['a', -3.0, 5]]

    #access item of a list
    L[1] # returns 20.0
    L[0] # returns 'a'
    M[1] # returns ['a',-3.0,5]
    M[1][2] # returns 5

    # Creating lists using range()
    L1=list(range(4)) # [0, 1, 2, 3]
    
    L2=list(range(17,29,4)) # [17, 21, 25]

    len(L2) # returns 3 (length of the list)

    # Slicing
    L7 = ['a', 'b', 'c', 'd', 'e']
    L7[1:4]                      # ['b', 'c', 'd'] (from index 1 to 3)
    L7[:3]                       # ['a', 'b', 'c']
    L7[-2:]                      # ['d', 'e'] (step = 2)
    L7[::-1]                     # ['e', 'd', 'c', 'b', 'a'] (reversed list)

    #Altering lists
    L = [10, 20, 30, 40]
    L[2] = 99     # L becomes [10, 20, 99, 40]
    L[1:3] = [7]  # Replace two elements with one → [10, 7, 40]
    
    # List comprehension
    squares = [x**2 for x in range(5)]  # [0, 1, 4, 9, 16]

``` 
- Common list operations
```python
    
    L = [3, 1, 2]

    L.append(4)       # adds 4 at the end  [3, 1, 2, 4]
    L.extend([5, 6])  # adds elements of another list [3, 1, 2, 4, 5, 6]
    L.insert(1, 9)    # inserts 9 at index 1  [3, 9, 1, 2, 4, 5, 6]
    L.remove(1)       # removes first occurrence of 1 [3, 9, 2, 4, 5, 6]
    L.pop()           # removes and returns last element returns: 6 and [3, 9, 2, 4, 5]
    L.sort()          # sorts the list  [2, 3, 4, 5, 9]
    L.reverse()       # reverses the list [9, 5, 4, 3, 2]
    L.count(3)        # returns number of times 3 appears returns:1
    new_list = L.copy() # [9, 5, 4, 3, 2] 

    ind = [0,1,2,3]
    color = ["red", "green"]
    list(zip(color,ind))
    # gives [('red', 0), ('green', 1)]

``` 
2. **Arrays**(Previw)
`NumPy` package provides arrays for efficient numerical computing. Arrays are constructed from lists by the function `array`.
```python
    
    from numpy import array
    v = array([1.,2.,3.])
    A = array([[1.,2.,3.],[4.,5.,6.]])

    v[2] # returns 3.0
    A[1,2] # returns 6.0

```
- Arrays are different to the lists, they store elements of the same numeric type (e.g., float, int, complex).
- `len()` gives the number of elements in a vector (or rows in a matrix) (same as list).
- The arithmetic operations `(+, *, /, -)` work all element-wise.
- The `dot()` function (or `@` operation) performs a dot product or matrix multiplication, depending on the shape of the arrays.
```python
    
    from numpy import *

    v1 = array([1, 2, 3])
    v2 = array([4, 5, 6])

    # Dot product: 1*4 + 2*5 + 3*6 = 4 + 10 + 18 = 32
    print(dot(v1, v2))  # 32
    print(v1 @ v2)      # Also 32 (same thing)

```
- The arrays do not support `append()` like lists, and their size cannot be changed by slicing.

3. **Tuples**
A tuple is like a list, but immutable (cannot be changed). It defined with or without parentheses as a comma-separated sequence of object.
```python
    
    my_tuple = 1, 2, 3 # our first tuple
    my_tuple = (1, 2, 3) # the same
    my_tuple = 1, 2, 3, # again the same
    len(my_tuple) # 3, same as for lists
    my_tuple[0] # 1
    my_tuple[0] = 'a' # error! tuples are immutable

```
4. **Dictionaries**
Different to the lists, tuples and arrays, the dictionarie deosn't according to their place in the sets of objects, its data are accessing by their keys. The key must be unique and immutable.
```python
    
    student = {'name': 'Alice', 'age': 22}
    print(student['name'])      # 'Alice'
    student['grade'] = 'A'      # add a new key

```
5. **Sets**
A set is an unordered collection of unique elements. It  shares properties and operations with sets in mathematics.
```python
    
    A = {1, 2, 3} # this is a set
    B = {2, 3, 4}

```
- Basic set operations
```python
    
    # Define two sets
    A = {1, 2, 3, 4}
    B = {3, 4, 5, 6}

    # Union: combines all unique elements from both sets
    print(A.union(B))           # {1, 2, 3, 4, 5, 6}

    # Intersection: elements common to both sets
    print(A.intersection(B))    # {3, 4}

    # Difference: elements in A but not in B
    print(A.difference(B))      # {1, 2}
    print(B.difference(A))      # {5, 6}

    # Membership test
    print(3 in A)               # True
    print(5 in A)               # False

    # Subset: checks if all elements of one set are in another
    C = {2, 3}
    print(C.issubset(A))        # True

    # Superset: checks if the set contains all elements of another set
    print(A.issuperset(C))      # True

    # Equality (order doesn't matter)
    D = {4, 3, 2, 1}
    print(A == D)               # True

    # Empty set
    empty = set()
    print(empty)                # set()
    print(type(empty))          # <class 'set'>

```
###