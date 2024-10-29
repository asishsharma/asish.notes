

# Arrays
## What is it? 
arrays is a user defined variable which can hold multiple values of a single type. It is especially useful for iterating through values in the array. It is similar to lists, though list can store non-homogenious values as well. An array also can handle direct arithematic operations efficiently, making it useful for long sequence of values. an array can also be 2D.

## working with arrays
## creating arrays
an array can be created by first importing Numpy package, before using the function in the package for creating an array. The array package can also be used, but Numpy is ubiquitous for our usecase.
```python
import numpy as np  
  
arr = np.array([1, 2, 3, 4, 5])  
```

### subsetting arrays
an array can be subset using the index(which starts with 0). A 2d array can be subset using 1 or 2 indexes depending on granularity of subset needed. 
```python
import numpy as np
a = np.array([10, 14, 8, 34, 23, 67, 47, 22])

# referencing 1st value in array using a[0]
print(a[0]) #prints the first value in the array which is 10

print(a[2:4]) # prints the 3rd,4th and 5th value in the array. 

```
```python
# subsetting 2d array to get data starting with particular values
import numpy as np
data = np.array([
        [100002, 2006, 1.1, 0.01, 6352],
        [100002, 2006, 1.2, 0.84, 304518],
        [100002, 2006, 2,   1.52, 148219],
        [100002, 2007, 1.1, 0.01, 6292],
        [10002,  2006, 1.1, 0.01, 5968],
        [10002,  2006, 1.2, 0.25, 104318],
        [10002,  2007, 1.1, 0.01, 6800],
        [10002,  2007, 4,   2.03, 25446],
        [10002,  2008, 1.1, 0.01, 6408]    ])

subset1 = data[data[:,0] == 100002]
# we are asking for an array of all lists that start with '100002'
```
output: Subset 1
```python
array([[  1.00002e+05,   2.006e+03,   1.10e+00, 1.00e-02,   6.352e+03],
       [  1.00002e+05,   2.006e+03,   1.20e+00, 8.40e-01,   3.04518e+05],
       [  1.00002e+05,   2.006e+03,   2.00e+00, 1.52e+00,   1.48219e+05],
       [  1.00002e+05,   2.007e+03,   1.10e+00, 1.00e-02,   6.292e+03]])
```

### modifying arrays
we can append one or multiple values to an array. We can also remove values from array. 

We can modify one single element of an array without changing the other values

## Advantges and Disadvantages
advantages: 
- it is computationally efficient
- It is efficient memorywise
- Can perform arithematic operations directly 
- working on 2D arrays is simple

 Disadvantages:
 
## Best practices

# List

In Python, a **list** is a collection of data that stores multiple items in a single variable. These items must be ordered, able to be changed, and can be duplicated. A list can store non-homogenious data

Creating Lists: Lists are written with square brackets. an example is shown below. 

```python
price_usd = [20,30,40]
print(price_usd)
```

##### Working with Lists
You can access an item in the list using index number of the item. Note: first item starts with 0

Let's access the second item of our `price_usd` list.
```python
print(price_usd[1])
```
We can also access the last item of our `price_usd` using negetive indexing
```python
print(price_usd[-1])
```
append to the list using .append function
```python
price_usd.append(1234)
price_usd
```
Some arithematic operations: 
```python 
# sum of items in a list
sum(price_usd)

# length of items in a list
len(price_usd)

#average of items in a list
average_usd = sum(price_usd)/len(price_usd)
```

**zipping lists**: pairing the values of items in 2 lists together. 
```python
area = [1,2,3,4]
new_list = zip(price_usd, area_m2)
zipped_list = list(new_list)
zipped_list
```
 
 Slicing lists, or selecting part of the list can be done as below: 
```python
 price_usd[1:3]
```
