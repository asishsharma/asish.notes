---
tags: ML, wqu
---


# WQU DS lab
## WQU textbook
### Python: Getting Started

#### Simple Calculations

In addition to all the more complex things you can do in Python, it is also useful for completing simple mathematical operations.

**Addition and Subtraction**

Add numbers together like this:
```python
1 + 1
```

Notice that you don't need to include `=` in order to make the operation work.

Subtract numbers like this:
```python
2 - 1
```

**Division**

Divide numbers like this:
```python
4 / 2
```
Remember that Python will return an error if you try to divide by 0!

**Modulo Division**

Perform modulo division like this:
```python
5 % 2
```
**Multiplication**

Multiply numbers like this: 
```python
4 * 2
```
Add **exponents** to numbers like this:
```python
4 ** 2
```
#### Order of Operations
Just like everywhere else, Python works on a specific order of operations. That order is:

> [!Note] Parentheses Exponents Multiplication Addition Subtraction

If you remember being taught PEMDAS, then this is the same thing! All the operations in Python work with levels of parentheses, so if you wanted to add two numbers together, and then add another number to the result, the code would look like this:
```python
(6 + 4) + 4
```
Things get more complicated when we add more terms to the equation, but the principle remains the same: if you open a set of parentheses, make sure you close it too. Here's an example that uses all the PEMDAS possibilities:
```python
(((5 ** 3 + 7) * 4) / 16 + 9 - 2)
```
#### Data Types


There are lots of different types of data in the world, and Python groups that data into several categories.

**Boolean** (`bool`)**:** 
- Any data which can be expressed as either `True` or `False`.
- Used when comparing two values. For example, if you enter `10 > 9`, Python will return `True`.

**String** (`str`)**:**

- Data that involves text — either letters, numbers, or special characters. 
- Strings are enclosed in either single- or double-quotation marks: `"string-1"` or `'string-2'`.

**Numeric** (`int`, `float`, `complex`)**:**

- Data that can be expressed numerically.
- An integer, or `int`, is a whole number, positive or negative, without decimals, of unlimited length:  `123`.
- A floating-point number, or `float`, is a number, positive or negative, containing one or more decimals: `123.01`.
- A complex number, or `complex`, are imaginary numbers, designated by a `j`: `(3 + 6j)`.

**Sequence** (`list`, `tuple`, `set`)**:**

- Data that is a collection of discrete items.
- A `list` is collection that is ordered and changeable. It's designated using square brackets `[]`, and items can be of different data types: `["red", 1, 1.03, 1]`.
- A `tuple` is a collection which is ordered and unchangeable. It's designated using parentheses `()`: `("red", 1, 1.03, 1)`.
- A `set` is a collection which is unordered, unchangeable, and does not permit duplicate items. It's designated using curly brackets `{}`: `{"red", 1, 1.03}`.

**Mapping** (`dict`)**:** 
- Dictionaries store data in *key-value* pairs. They're designated using curly brackets `{}`, like a `set`, but notice that keys and values are associated with each other using a colon `:`. Each pair is separated from the next using a comma `,`.

```python
dict1 = {
    "department": "quindio", 
    "property_type": "house", 
    "price_usd": 330899.98
}
```

**Binary** (`bytes`, `bytearray`, `memoryview`)**:**
- Used to manipulate and display binary data. That is, data that can be expressed with integers represented with base 2.
- Unlike the other data types described above, `binary` types are not human-readable.

#### Lists

In Python, a **list** is a collection of data that stores multiple items in a single variable. These items must be ordered, able to be changed, and can be duplicated. A list can store data of multiple types; not all the items in the list need to be the same type.

##### Creating Lists
Lists can be as long or as short as you like. Let's create a short list based on data from the Colombian real estate market to give us something to work with.

Lists are written with square brackets. Code for a short list that shows the price of houses in US dollars looks like this:

```python
price_usd = [97919.38, 300511.20, 293758.14]
print(price_usd)
```

##### Working with Lists
After you've created a list, you can **access** any item on the list by referring to the item's index number. Keep in mind that in Python, the first item in a list is always 0. 

Let's access the second item of our `price_usd` list.
```python
print(price_usd[1])
```
<font size="+1">Practice</font>

Try it yourself! Create and print a list that shows the area of the houses, called `area_m2`. Include the items `187.0`, `82.0`, and `235.0`.
```python
area_m2 = ... 
# fill in the function here
print(area_m2)
```
If we want to access the an item at the end of the list, we can use **negative indexing**. In negative indexing, -1 refers to the last item, -2 to the second to last, and so on. 

Let's access the last item in our `department` list.
```python
print(price_usd[-1])
```
<font size="+1">Practice</font>

Try accessing the second item in your `area_m2` list.
```python
```


Try accessing the last item in the same list.
```python
```


###### Appending Items
It's also possible to add an item to a list that already exists using the  `append` method like this:
```python
price_usd.append(540244.86)
```
<font size="+1">Practice</font>

Add the item `195.0` to your `area_m2` list.

```python
print(area_m2)
```
###### Aggregating Items

We can also **aggregate** items on a list to make analyzing the list more useful. For example, if we wanted to know the total value in US dollars of the houses on our `price_usd` list, we could use the `sum` method.
```python
total_usd = sum(price_usd)
```
We might also be interested in the average value in US dollars of the houses on the same list. To find the average, we add the `len` method to the `sum` method.
```python
average_usd = sum(price_usd) / len(price_usd)
```
<font size="+1">Practice</font>

Try it yourself! Calculate the total area of the houses on your `area_m2` list, and find the average area of all the houses on the list. 
```python
total_area_m2 = ...
print(total_area_m2)
```
```python
average_area_m2 = ...
print(average_area_m2)
```
###### Zipping Items

Finally, it might be useful to combine -- or **zip** -- two lists together. For example, we might want to create a new list that pairs the values in our `price_usd` list with our `area_m2` list. To do that, we use the `zip` method. The code looks like this:

You might have noticed that the above code involving putting one list (in this case, `new_list`) inside another list (in this case, `list`). This approach is called a **generator**, and we'll come back to what that is and how it works later in the course. 

```python
new_list = zip(price_usd, area_m2)
zipped_list = list(new_list)
```
You might have noticed that the above code involving putting one list (in this case, `new_list`) inside another list (in this case, `list`). This approach is called a **generator**, and we'll come back to what that is and how it works later in the course. 

<font size="+1">Practice</font>

Try it yourself! Create a list called `area_m2` that includes the terms `235.0`, `130.0`, and `137.0`, then create another list called `price_cop` that includes the terms `400000000.0`, `850000000.0`, and `475000000.0`. Then zip them together to create a new list called `area_price`, and `print` the result.

```python
area_m2 = ...
```

#### Python `for` Loops

A `for` Loop is used for executing a set of statements for each item in a list.

##### Working with `for` Loops

There can be as many statements as there are items in the list, but to keep things manageable, let's use our list of real estate values in Colombia.
```python
price_usd = [97919.38, 300511.20, 293758.14, 540244.86]
print(price_usd)
```
We might want to see each of the values in the list, so we insert a `for` Loop:
```python
price_usd = [97919.38, 300511.20, 293758.14, 540244.86]
for x in price_usd:
    print(x)
```
Note that the `print` command is indented.

<font size="+1">Practice</font>

Try it yourself using the `area_m2` list:
```python
area_m2 = ...
```



#### Python Dictionaries

In Python, a **dictionary** is a collection of data that occurs in an order, is able to be changed, and does not allow duplicates. Data in a dictionary are always presented as **keys** and **values**, and those key-value pairs cannot be duplicated in the dataset.

##### Creating Dictionaries

Dictionaries can be as big or as small as you like. Let's create a small dictionary based on data from the Colombian real estate market to give us something to work with. 

Dictionaries are written with curly brackets, with key-value pairs inside. Code for a small dictionary looks like this:
```python
colomdict = {
    "property_type": "house",
    "department": "quindio",
    "area": 235.0,
}
```
<font size="+1">Practice</font>

Try it yourself! Create and `print` a dictionary called `bogota` with the key-value pairs `"price_usd": 121,555.09`, `"area_m2": 82.0`, and `"property_type": "house"`
```python
bogota = ...
print(bogota)
```
##### Working with Dictionaries 

After you've created a dictionary, you can **access** any item by using its key name inside square brackets.

Going back to our example dictionary, let's access the value for "department".
```python
x = colomdict["department"]
print(x)
```
<font size="+1">Practice</font>

Try accessing the value for `price_usd` in the Bogotá dictionary you created above.
```python
x = ...
```

You can also use `get` to retrieve a value. That looks like this:
```python
x = colomdict.get("department")
```
<font size="+1">Practice</font>

Now try accessing the value for `area_m2` using the `get` method, and print the result.
```python
x = ...
```

#### JSON

JSON stands for Java Script Object Notation, and it's a text format for storing and transporting data.

##### Working with JSON

JSON works by creating **key-value pairs**, where the key is data that can be represented by letters (called a **string**). JSON values can be strings, numbers, objects, arrays, boolean data, or null. JSON usually comes as a list of dictionaries, which look like this:

Here's an example from our `colombia-real-estate-1` dataset with two key-value pairs that both include string values:
```python
[
    {"property_type": "house", "department": "bogota"},
    {"property_type": "house", "department": "bogota"},
    {"property_type": "house", "department": "bogota"},
]
```
Here's an simplified example from our `colombia-real-estate-1` dataset with two key-value pairs that both include string values:
```python
{"property_type": "house", "department": "bogota"}
```
JSON pairs with numbers look like this:
```python
{"area_m2": 187.0, "price_usd": 330899.98}
```
When you mix more than one type of value, it looks like this:
```python
{"property_type": "house", "price_usd": 330899.98}
```
#### References & Further Reading

- [A guide to basic math operations in Python](https://codingexplained.com/coding/python/basic-math-operators-in-python)
- [Python documentation on built-in data types](https://docs.python.org/3/library/stdtypes.html)
- [Summary of Python data types](https://www.w3schools.com/python/python_datatypes.asp)
- [Tutorial on type conversion in Python](https://www.datacamp.com/community/tutorials/python-data-type-conversion)
- [A description of how dictionaries work in Python](https://www.w3schools.com/python/python_dictionaries.asp)
- [An introduction to JSON](https://www.w3schools.com/js/js_json_syntax.asp)
- [An introduction to lists in Python](https://www.w3schools.com/python/python_lists.asp)
- [How to zip lists](https://www.kite.com/python/answers/how-to-zip-two-lists-in-python)
- [Calculating mean, median, and mode in Python](https://stackabuse.com/calculating-mean-median-and-mode-in-python/)
- [A brief tutorial of For Loops](https://www.w3schools.com/python/python_for_loops.asp)

### Python: Advanced

#### Strings

##### What's a string? 

Recall that a `string` is any kind of information that can be represented with letters.

##### Working with strings

When working with data, often files and directories have names that fit a pattern. For example, data on property prices in Colombia and Mexico might be stored in files named:

1. `colombia-real-estate-1.csv`
2. `colombia-real-estate-2.csv`
3. `colombia-real-estate-3.csv`
4. `mexico-city-real-estate-1.csv`
5. `mexico-city-real-estate-2.csv`
6. `mexico-city-real-estate-3.csv`
7. `mexico-city-real-estate-4.csv`
8. `mexico-city-real-estate-5.csv`
9. `mexico-city-test-features.csv`
10. `mexico-city-test-labels.csv`

When the list of files is short like this one, it's not difficult to find the ones we want, but if the list were longer, we might need some help. If we're only interested in finding files that deal with Mexico, we could search the files for files beginning with `mexico-city-real-estate-`. To do this, we'll use the `.glob` function. The code looks like this:

```python
import glob

glob.glob("./data/mexico-city-real-estate-[0-9].csv")
```

The `.glob` function allows for pattern matching. In this example `[0-9]` allows for any digit between 0 and 9, but there are lots of other patterns that `.glob` can find. Here are a few of the more common ones:
- `*` Match any number of characters
- `?` Match a single character of any kind
- `[a-z]` Match any lower case alphabetical character in the current locale
- `[A-Z]` Match any upper case alphabetical character in the current locale
- `[!a-z]` Do not match any lower case alphabetical character in the current locale

So, if we wanted to find all the files from Mexico City, we would use code like this:

```python
glob.glob("./data/mexico-city*")
```

> [!Note] Practice 
> Try it yourself! Find only the data files containing the word `test`.



So far, you have only searched for files in one specific directory. It's also possible to search for files in sub directories. To get a listing of all notebook files starting from the directory above this one and all others below it, you can use:

```python
glob.glob("../**/*.ipynb", recursive=True)
```

##### Working with f-strings

We usually use `print` to examine output in Python, but most of the examples we've been printing have been relatively short. Formatted strings are helpful for all sorts of reasons, but when we're assembling and formatting a long string, using the `print` function can be difficult and time-consuming. Along the same lines, it's also useful to directly evaluate variables and expressions within strings. To do those things, we create `f""` strings. The code looks like this:

```python
Home = "Mexico City"
f"My home is {Home}"
```

```python
import datetime

python_birthday = datetime.datetime(year=1991, month=2, day=20)
print(f"Python first appeared on {python_birthday:%B %d} in the year {python_birthday:%Y}."
)


now = datetime.datetime.now()
print(f"Python is {now.year - python_birthday.year} years old.")
```
> [!Note] Practice
> Mexico-Tenochtitlan was established on 13 March 1325; use f-strings to indicate how long ago that was.
```python
mexico_founding = ...
now = datetime.datetime.now()


f"Mexico-Tenochtitlan was established {... - ...} years ago."
```

*Sources and further reading* 
- [Online tutorial on finding list lengths in Python](https://www.w3schools.com/python/gloss_python_list_length.asp)
- [Official python documentation on the `len` function](https://docs.python.org/3/library/functions.html?#len)

#### Iterators and Iterables 

A list is a container with a countable number of values. Because that's true, a list is an **iterable**, meaning that we can **iterate** through it one item at a time. In other words, iterators retrieve these values only when we ask for them. If we try to bring in a large database — over a million values, for example — asking for every action to be applied to every value will take up a huge amount of memory. Iterators are helpful because they allow us to free up memory to use for other tasks. We'll spend more time working with databases later on, but for now, let's take a look at some code:

from pymongo import MongoClient

client = MongoClient(host="localhost", port=27017)

(list(client.list_databases()))

Setting aside the first two lines of code, we have a method which has returned a list of four databases. If we want to examine each database by itself, we can create a variable called `results`, and then try to print it.

results = client.list_databases()
print((results))

That doesn't seem like much of anything, but if we add the **iterator** `next()`, we'll get back something more useful.

print(next(results))

That makes much more sense! As you can see, this returns the first row. If we do it again, we'll get the second row:

print(next(results))

We can keep doing this until we get to the end of the list, at which point we'll get an error telling us that there's nothing left to print. Every time we use the `next()` method, we're using it as an iterator to iterate through our iterable.

##### List Comprehension 

List comprehension is used to iterate through lists without explicitly writing loops, which is especially useful for filtering data according to a specific condition.

Let's take a look at a list that shows property prices in Mexican pesos.

price_mexican_pesos = [
    35000000.0,
    2000000.0,
    2700000.0,
    6347000.0,
    6994543.16,
    6617835.61,
    670000.0,
]

But maybe we're interested in comparing these prices to property values in Colombia. To do that, we'll need to figure out how to express the data on our list in Colombian pesos. We can use a `for` loop to make the conversion based on an exchange rate of 1 Mexican peso to 190 Colombian pesos. The code looks like this:

price_colombian_pesos = []
for price in price_mexican_pesos:
    price_colombian_pesos.append(price * 190)

print(price_colombian_pesos)

But what if we could do the same thing, but using fewer lines? That's what `list comprehension` is for. The code looks like this:

price_colombian_pesos = [price * 190 for price in price_mexican_pesos]

print(price_colombian_pesos)

We can use list comprehension to find all the `house` entries in this list of properties, like this:
```
records = [
    'sell,apartment,|México|Distrito Federal|Benito Juárez|,"19.384467,-99.135872",1860000.0,MXN,1843173.75,97996.85,,70.0,,26571.42857142857',
    'sell,apartment,|México|Distrito Federal|Iztapalapa|Cerro de La Estrella|,"19.324123,-99.074132",700000.0,MXN,693667.44,36880.53,,50.0,,14000.0',
    'sell,house,|México|Distrito Federal|La Magdalena Contreras|San Jerónimo Lídice|,"19.317653,-99.236291",3350000.0,MXN,3319694.98,176499.72,,350.0,,9571.42857142857',
    'sell,apartment,|México|Distrito Federal|Cuauhtémoc|,"19.446313,-99.14006",405108.0,MXN,401443.16,21343.71,,50.0,,8102.16',
    'sell,house,|México|Distrito Federal|Coyoacán|,"19.303906,-99.107812",7200000.0,MXN,7134866.79,379342.68,,250.0,,28800.0',
    'sell,apartment,|México|Distrito Federal|Benito Juárez|,"19.374171,-99.181264",2425000.0,MXN,2403062.73,127764.72,,96.0,,25260.416666666668',
    'sell,apartment,|México|Distrito Federal|Tlalpan|,"19.287428,-99.122283",1250000.0,MXN,1238692.07,65858.1,,65.0,,19230.76923076923',
    'sell,house,|México|Distrito Federal|Venustiano Carranza|,"19.436436,-99.117256",1362000.0,MXN,1349678.96,71758.99,,98.0,,13897.959183673467',
    'sell,apartment,|México|Distrito Federal|Benito Juárez|,"19.382429,-99.160199",2250000.0,MXN,2229645.73,118544.58,,90.0,,25000.0',
    'sell,house,|México|Distrito Federal|Tlalpan|Granjas Coapa|,"19.300456,-99.115741",3900000.0,MXN,3864719.42,205477.28,,153.0,,25490.19607843137',
    'sell,apartment,|México|Distrito Federal|Álvaro Obregón|,"19.363167,-99.276028",9000000.0,MXN,8918583.49,474178.35,,188.0,,47872.34042553192',
    'sell,house,|México|Distrito Federal|Coyoacán|Villa Coyoacán|,"19.348694,-99.16291",1150000.0,USD,21629775.0,1150000.0,,555.0,,2072.072072072072',
    'sell,house,|México|Distrito Federal|Tlalpan|,"19.300963,-99.144237",7500000.0,MXN,7432152.81,395148.62,,385.0,,19480.51948051948',
    'sell,house,|México|Distrito Federal|Coyoacán|Paseos de Taxqueña|,"19.343979,-99.124863",6310000.0,MXN,6252917.98,332451.71,,183.0,,34480.87431693989',
    'sell,apartment,|México|Distrito Federal|Coyoacán|San Diego Churubusco|,"19.354509,-99.149765",10000000.0,MXN,9909537.15,526864.83,,293.0,,34129.69283276451',
]
```
```
[row for row in records if "house" in row]
```
> [!Note] Practice
> Explore the list records in the list, and find all entries located in `Tlalpan`



#### Functions

When we code in Python, we want to create **readable** programs. One of the easiest ways to make a program readable is by not repeating sections of code that do the same thing. We do that by using `functions`. For example, you might have surface area of a property in square meters, but you want to see it in square feet. Keeping in mind that one square meter = 10.76391 square feet, you can write a function that starts with the area in square meters, and gives as output the area in square feet. The code looks like this:

```python
def m2toft2(area_meter2):
    area_feet2 = 10.76391 * area_meter2
    return area_feet2
```

The code above defines a function called `m2toft2` that takes in a single input, called `area_meters`, and returns a single output, called `area_feet`. Let's try another one:

```python
m2toft2(4)
```

A function by itself can be difficult to understand, so let's add some comments describing what the function does.

```python
def m2toft2(area_meter2):
    """
    This function takes in as input the area in meters squared
    and returns as an output the area in square feet

    input: area_meter2, the area in square meters
    output: area_feet2, the area in square feet
    """
    area_feet2 = 10.76391 * area_meter2
    return area_feet2
```

This way, if you forget what `m2toft2` does, Python will be able to remind you, like this:

```python
help(m2toft2)
```

This can be especially useful for large programs with lots of functions, some of which might have multiple arguments. For example, a function might take a list of areas of properties in square meters and a list of prices per square meter, and return lists with area in square feet and price per square foot. That function would look like this:

```python
def convert_area(area_meters2):
    """
    This function takes in a list of area in square meters and
    returns area in square feet

    input: area_meters2, area in square meters
    output: area_feet, area in square feet
    """
    area_feet2 = [item * 10.76391 for item in area_meters2]
    return area_feet2
```

Let's try it and see what happens:

```python
surface_total_in_m2 = [1860000.0, 700000.0, 3350000.0]
```
```python
surface_total_in_ft2 = convert_area(surface_total_in_m2)
```
```python
print(surface_total_in_ft2)
```

> [!Note] Practice
> 
Python comes with many predefined functions. Try this one: `help(max)`
Now write a function that returns the greatest per unit area property price for a list of property prices per unit area, and then use your function for the list `price_usd_per_m2`.

```python
price_usd_per_m2 = [97996.85, 36880.53, 176499.72]
```

```python
def find_max_price_per_area(price_per_meter2):
    """
    Given a list with price per unit area, this function
    returns the most expensive price per unit area

    input: price_per_meter, list with price per unit area of each property
    output: the price of the most expensive property per unit area
    """
    
    return ...
```


```python
find_max_price_per_area(price_usd_per_m2)
```

> [!Note] Practice
> 

The previous example does not extend the max function that is in Python.  Keeping in mind that list comprehensions can be used to iterate through lists, use list comprehension or loops to write a function which, given a list of property areas and a corresponding list of property prices per unit area, returns the total price of the most expensive property.

```python
def find_max_price(area_meter2, price_per_meter2):
    """
    Given two lists, the first with areas of properties
    and the second with price per unit area, this function
    returns the most expensive property using list comprehension

    input: area_meter2, list with the total area of each property
    input: price_per_meter2, list with price per unit area of each property
    output: the price of the most expensive property
    """
    
    return ...

find_max_price(surface_total_in_m2, price_usd_per_m2)
```

##### Lambda Functions 

The function definitions we've been working with so far are fine for most purposes, but they can easily become a little bit long. When that happens, you might want to use a shorter method to expressing a function; that's what `lambda` functions are for. Here's code for a function which adds 3 to a number.

```python
add_three = lambda a: a + 3  # noqa: E731
```

Now that we've defined our function, let's try it out. If we wanted the function to add 3 to 5, the code would look like this: 

```python
add_three(5)
```

> [!Note] Practice
> 

Try it yourself! Write a lambda function called `sub_4` which will subtract 4 from a given number, and then try it out with the number 7.

```python
sub_4 = lambda a: a - 4  # noqa: E731
```


#### Files

###### Create files using Context Manager

A **context manager** allows you to allocate and release resources precisely when you want to. The most widely used example of context managers is the `with` statement. Suppose you have two related operations which you would like to execute as a pair, with a block of code in between. Context managers allow you to do specifically that. For example:

```python
with open("data/example.txt", "w") as f:
    f.write("Hello")
```

The code above will create a file called `example.txt` inside the data directory, with only one line: `"Hello"`. We can add multiple lines to the file by adding the `/n` to separate the line.

```python
with open("data/example.txt", "w") as f:
    f.write("Hello")
    f.write("\n")
    f.write("Hola")
```

<font size="+1">Practice</font>

Create a `txt` file named `practice.txt` inside the `data` directory with three lines using context manager.
```python
# test yourself

```


#### References and Further Reading

- [Context Manager](https://book.pythontips.com/en/latest/context_managers.html)




### Pandas: Getting started

**Pandas** is a Python library used for working with datasets. It does that by helping us make sense of **DataFrames**, which are a form of two-dimensional **structured data**, like a table with columns and rows. But before we can do anything else, we need to start with data in a CSV file.

#### Importing Data

##### CSV Files

CSV stands for Comma Separated Values, and it's a file type that allows data to be saved in a table. Data presented in a table is called **structured data**, because it adheres to the idea that there is a meaningful relationship between the columns and rows. A CSV might also show **panel data**, which is data that shows observations of the same behavior at various different times. The datasets we're using in this part of the course are all structured tables, but you'll see other arrangements of data as you move through your projects.

If you're familiar with the way data tables look in spreadsheet applications like Excel, you might be surprised to see that raw CSV files don't look like that. If you came across a CSV file and opened it to see what it looked like, you'd see something like this:

```python
property_type,department,lat,lon,area_m2,price_usd
house,Bogotá D.C,4.69,-74.048,187.0,"$330,899.98"
house,Bogotá D.C,4.695,-74.082,82.0,"$121,555.09"
house,Quindío,4.535,-75.676,235.0,"$219,474.47"
house,Bogotá D.C,4.62,-74.129,195.0,"$97,919.38"
```

##### Dictionaries

You can create a DataFrame from a Python dictionary using `from_dict` function.

```python
import pandas as pd

data = {"col_1": [3, 2, 1, 0], "col_2": ["a", "b", "c", "d"]}
pd.DataFrame.from_dict(data)
```

By default, DataFrame will be created using keys as columns. Note the length of the values should be equal for each key for the code to work. We can also let keys to be index instead of the columns:

```python
pd.DataFrame.from_dict(data, orient="index")
```

We can also specify column names:

```python
pd.DataFrame.from_dict(data, orient="index", columns=["A", "B", "C", "D"])
```

<font size="+1">Practice</font>

Try it yourself! Create a DataFrame called using the dictionary `clothes` and make the keys as index, and put column names as ['color','size']

```python
clothes = {"shirt": ["red", "M"], "sweater": ["yellow", "L"], "jacket": ["black", "L"]}
```



##### JSON Files

JSON is short for JavaScript Object Notation. It is another widely used data format to store and transfer the data. It is light-weight and very human readable. In Python, we can use the `json` library to read JSON files. Here is an example of a JSON string.

```python
info = """{
    "firstName": "Jane",
    "lastName": "Doe",
    "hobby": "running",
    "age": 35
}"""
print(info)
```

Use `json` library to load the json string into a Python dictionary:

```python
import json

data = json.loads(info)
data
```

We can load a json string or file into a dictionary because they are organized in the same way: key-value pairs.

```python
data["firstName"]
```

A dictionary may not be as convenient as a `DataFrame` in terms of data manipulation and cleaning. But once we've turned our json string into a dictionary, we can transform it into a `DataFrame` using the `from_dict` method.

```python
df = pd.DataFrame.from_dict(data, orient="index", columns=["subject 1"])
df
```

<font size="+1">Practice</font>

Try it yourself! Load the JSON file `clothes` and then transform it to `DataFrame`, name column properly.

```python
clothes = """{"shirt": ["red","M"], "sweater": ["yellow","L"]}"""
```


```python
data = ...
df = ...
df
```

#### Load Compressed file in Python

In the big data era, it is very likely that we'll need to read data from compressed files. One way to unzip the data is to use gzip. We can load the `poland-bankruptcy-data-2008.json.gz` file from the data folder using the following code:

```python
import gzip
import json
```

```python
with gzip.open("data/poland-bankruptcy-data-2008.json.gz", "r") as f:
    poland_data_gz = json.load(f)
```

`poland_data_gz` is a dictionary, and we only need the `data` portion of it.

```python
poland_data_gz.keys()
```

We can use the `from_dict` function from pandas to read the data:

```python
df = pd.DataFrame().from_dict(poland_data_gz["data"])
```

```python
df.head()
```

> [!Note] Practice
> 
 
Read `poland-bankruptcy-data-2007.json.gz` into a DataFrame.

#### Load file into dictionary


#### Transform dictionary into DataFrame
```python
df = ...
df.head()
```

##### Pickle Files

Pickle in Python is primarily used in `serializing` and `deserializing` a Python object structure. `Serialization` is the process of turning an object in memory into a stream of bytes so you can store it on disk or send it over a network. `Deserialization` is the reverse process: turning a stream of bytes back into an object in memory.

According to the pickle module documentation, the following types can be pickled:

* `None`
* Booleans
* Integers, long integers, floating point numbers, complex numbers
* Normal and Unicode strings
* Tuples, lists, sets, and dictionaries containing only objects that can be pickled
* Functions defined at the top level of a module
* Built-in functions defined at the top level of a module
* Classes that are defined at the top level of a module

Let's demonstrate using a python dictionary as an example.

```python
clothes = {"shirt": ["red", "M"], "sweater": ["yellow", "L"], "jacket": ["black", "L"]}
clothes
```

```python
import pickle

pickle.dump(clothes, open("./data/clothes.pkl", "wb"))
```

Now in the data folder, there will be a file named `clothes.pkl`. We can read the pickled file using the following code:

```python
with open("./data/clothes.pkl", "rb") as f:
    unpickled = pickle.load(f)
```

```python
unpickled
```

Note first we are using `wb` inside the `open` function because we are creating this file, while `deserializing` the file, we are using `rb` to read the file

<font size="+1">Practice</font>

Store the sample list into a pickle file, and load the pickle file back to a list.

```python
sample_list = [1, 2, 3, 4, 5]

# write unfinished code

unpickled
```

#### Working with DataFrames

The first thing we need to do is import pandas; we'll use `pd` as an *alias* when we include it in our code.

Pandas is just a library; to get anything done, we need a dataset too. We'll use the `read_csv` method to create a DataFrame from a CSV file.

```python
import pandas as pd

df = pd.read_csv("data/colombia-real-estate-1.csv")
df.head()
```

<font size="+1">Practice</font>

Try it yourself! Create a DataFrame called `df2` using the `colombia-real-estate-2` CSV file.

```python
df2 = ...
df2.head()
```

#### Working with DataFrame Indices

A DataFrame stores data in a row-and-column format. The DataFrame Index is a special kind of column that helps identify the location of each row. The default Index uses integers starting at zero, but you can also set up customized indices like `"name"`, `"location"`, etc. For example, in the following real estate data set, the default index are the integer counts. 

```python
import pandas as pd

df = ...
df.head()
```

We can call the index column through `.index`:

```python
df.index[:5]
```

Use the `set_index` method, we can set the column `department` as the index instead. Note index column cannot have duplicate rows, like here we cannot set `property_type` as the index column.

```python
df.set_index("department", inplace=True)
df.head()
```

Now you can see the index column has changed:

```python
df.index[:5]
```

Using the `reset_index()` function, we can reset index back to default integer counts, and `department` will become a column again.

```python
df.reset_index(inplace=True)
df.head()
```

<font size="+1">Practice</font>

Try it yourself! Set `letter` as the index, then call the index. Then reset the index.

```python
data = {
    "letter": ["a", "b", "c", "d"],
    "number": [3, 2, 1, 0],
    "location": ["east", "east", "east", "west"],
}
df = pd.DataFrame.from_dict(data)
```

#### set index 'numbers'

```
df
```

#### reset index

```
df
```

#### Inspecting DataFrames
Once we've created a DataFrame, we need to **inspect** it in order to see what's there. Pandas has many ways to inspect a DataFrame, but we're only going to look at three of them: `shape`, `info`, and `head`.

If we're interested in understanding the **dimensionality** of the DataFrame, we can use the `df.shape` method. The code looks like this:

```
df.shape
```

The `shape` output tells us that the `colombia-real-estate-1` DataFrame -- which we called `df1` -- has 3066 rows and 6 columns. 

If we're trying to get a **general idea** of what the DataFrame contained, we can use the `info` method. The code looks like this:

```
df.info()
```

The `info` output tells us all sorts of things about the DataFrame: the number of columns, the names of the columns, the data type for each column, how many non-null rows are contained in the DataFrame.

<font size="+1">Practice</font>

Try it yourself! Use `info` and `shape` to explore `df2`, which you created above.




If we wanted to see all the rows in our new DataFrame, we could use the `print` method. Keep in mind that the entire dataset gets printed when you use `print`, even though it only shows you the first few lines. That's not much of a problem with this particular dataset, but once you start working with much bigger datasets, printing the whole thing will cause all sorts of problems. 

So instead of doing that, we'll just take a look at the first five rows by using the `head` method. The code looks like this:

```
df.head()
```

By default, `head` returns the first five rows of data, but you can specify as many rows as you like. Here's what the code looks like for just the first two rows:

```
print(df.head(2))
```

<font size="+1">Practice</font>

Try it yourself! Use the `head` method to return the first five and first 7 rows of the `colombia-real-estate-2` dataset.




#### Working with Columns

Sometimes, it’s handy to duplicate a column of data. It might be that you’d like to drop some data points or erase empty cells while still preserving the original column. If you’d like to do that, you’ll need to duplicate the column. We can do this by placing the name of the new column in square brackets. 

##### Adding Columns

For example, we might want to add a column of data that shows the price per square meter of each house in US dollars. To do that, we're going to need to create a new column, and include the necessary math to populate it. First, we need to import the CSV and inspect the first five rows using the `head` method, like this:

```python
df3 = pd.read_csv("data/colombia-real-estate-3.csv")
df3.head()
```

Then, we create a new column called `"price_m2"`, provide the formula to populate it, and inspect the first five rows of the dataset to make sure the new column includes the new values:

```python
df3["price_m2"] = df3["price_usd"] / df3["area_m2"]
df3.head()
```

<font size="+1">Practice</font>

Try it yourself! Add a column to the `colombia-real-estate-2` dataset that shows the price per square meter of each house in Colombian pesos.

```python
df = ...
df["price_m2"] = ...
```


##### Dropping Columns

Just like we can add columns, we can also take them away. To do this, we’ll use the `drop` method. If I wanted to drop the `“department”` column from `colombia-real-estate-1`, the code would look like this:


```python
df2 = df.drop("department", axis="columns")
df2.head()
```

Note that we specified that we wanted to drop a column by setting the `axis` argument to `"columns"`. We can drop rows from the dataset if we change the `axis` argument to `"index"`. If we wanted to drop row 2 from the `df2` data, the code would look like this:


```python
df2 = df.drop(2, axis="index")
df2.head()
```

<font size="+1">Practice</font>

Try it yourself! Drop the `"property_type"` column and row 4 in the `colombia-real-estate-2` dataset.


```python
df1 = ...
```


##### Dropping Rows

Including rows with empty cells can radically skew the results of our analysis, so we often drop them from the dataset. We can do this with the `dropna` method. If we wanted to do this with `df`, the code would look like this:

```python
print("df shape before dropping rows", df.shape)
df.dropna(inplace=True)
print("df shape after dropping rows", df.shape)
df.head()
```

By default, pandas will keep the original DataFrame, and will create a copy that reflects the changes we just made. That's perfectly fine, but if we want to make sure that copies of the DataFrame aren't clogging up the memory on our computers, then we need to intervene with the `inplace` argument. `inplace=True` means that we want the original DataFrame updated without making a copy. If we don't include `inplace=True` (or if we do include `inplace=False`), then pandas will revert to the default. 

<font size="+1">Practice</font>

Drop rows with empty cells from the `colombia-real-estate-2` dataset.

```python
df2 = ...
```



##### Splitting Strings

It might be useful to split strings into their constituent parts, and create new columns to contain them. To do this, we’ll use the `.str.split` method, and include the character we want to use as the place where the data splits apart. In the `colombia-real-estate-3` dataset, we might be interested breaking the `"lat-lon"` column into a `"lat"` column and a `"lon"` column. We’ll split it at `“,”` with code that looks like this:


```python
df3[["lat", "lon"]] = df3["lat-lon"].str.split(",", expand=True)
```

Here, `expand` is telling pandas to make the DataFrame bigger; that is, to create a new column without dropping any of the ones that already exist.

<font size="+1">Practice</font>

Try it yourself! In `df3`, split `"place_with_parent_names"` into three columns (one called `"place"`, one called `"department"`, and one called `"state"`, using the character `“|”`, and then return the new `"department"` column. 



##### Recasting Data

Depending on who formatted your dataset, the types of data assigned to each column might need to be changed. If, for example, a column containing only numbers had been mistaken for a column containing only strings, we’d need to change that through a process called *recasting*. Using the `colombia-real-estate-1` dataset, we could recast the entire dataset as strings by using the `astype` method, like this:

```python
print(df.info())
newdf = df.astype("str")
print(newdf.info())
```

This is a useful approach, but, more often than not, you’ll want to only recast individual columns. In the `colombia-real-estate-1` dataset, the `"area_m2"` column is cast as `float64`. Let's change it to `int`. We’ll still use the `astype` method, but we'll insert the name of the column. The code looks like this:


```python
df["area_m2"] = df.area_m2.astype(int)
df.info()
```

<font size="+1">Practice</font>

Try it yourself! In the `colombia-real-estate-2` dataset, recast `"price_cop"` as an object.

```python
df = ...
df2["price_cop"] = ...
df.info()
```

##### Access a substring in a Series

To access a substring from a Series, use the `.str` attribute from the Series. Then, index each string in the Series by providing the `start:stop:step`. Keep in mind that the start position is inclusive and the stop position is exclusive, meaning the value at the start index is included but the value at the stop index is not included. Also, Python is a 0-indexed language, so the first element in the substring is at index position 0. For example, using the `colombia-real-estate-1` dataset, we could the values at index position 0, 2, and 4 of the `department` column:

```python
df["department"].str[0:5:2]
```

<font size="+1">Practice: Access a substring in a Series using pandas</font>

Try it yourself! In the `colombia-real-estate-2` dataset, access the `property_type` column and return the first 5 characters from each row:



##### Replacing String Characters

Another change you might want to make is replacing the characters in a string. To do this, we’ll use the `replace` method again, being sure to specify which string should be replaced, and what new string should replace it. For example, if we wanted to replace the string `“house”` with the string `“single_family”` in the `colombia-real-estate-1` dataset, the code would look like this:

```python
df["property_type"] = df["property_type"].str.replace("house", "single_family")
df.head()
```

There are two important things to note here. The first is that the old value needs to come before the new value inside the parentheses of `str.replace`. 

The second important issue here is that, unless you specify differently, *all* instances of the old value will be replaced. If you only want to replace the first three instances, the code would look like this: `str.replace(“house”, “single_family”, 3)`


```python
df["property_type"] = df["property_type"].str.replace("house", "single_family", 3)
df.head()
```

<font size="+1">Practice</font>

Try it yourself! In the `colombia-real-estate-2` dataset, change `“apartment”` to `“multi_family”`, in the first 7 rows, and print the result.

```python
df = ...
```


###### Rename a Series

Another change you might want to make is to rename a Series in pandas. To do this, we’ll use the `rename` method, being sure to specify the mapping of old and new columns. For example, if we wanted to replace the column name `property_type` with the string `type_property` in the `colombia-real-estate-1` dataset, the code would look like this:

```python
df.rename(columns={"property_type": "type_property"})
```

<font size="+1">Practice: Rename a Series</font>

Try it yourself! In the `colombia-real-estate-2` dataset, change the column `lat` to `latitude` and print the head of DataFrame. 



###### Determine the unique values in a column

You might be interested in the unique values in a Series using pandas. To do this, we’ll use the `unique` method. For example, if we wanted to identify the unique values in the column  `property_type` in the `colombia-real-estate-1` dataset, the code would look like this:

```python
df["property_type"].unique()
```

<font size="+1">Practice: Determine the unique values in a column</font>

Try it yourself! In the `colombia-real-estate-2` dataset, identify the unique values in the column  `department`:



##### Replacing Column Values

If you want to replace a columns' values, simply use the `.replace()` function:

#### Series.rename() example
```python
df = pd.read_csv("data/colombia-real-estate-2.csv")
df.head()
```

We can replace a specific row with other values

```python
df["area_m2"].replace(235.0, 0)
```

If you want to replace multiple values at the same time, you can also define a dictionary ahead of time, with dictionary keys the originals and dictionary values the replaced values. Then pass the dictionary to the `replace()` function.

```python
replace_value = {235: 0, 130: 1, 137: 2}

df["area_m2"].replace(replace_value)
```

Or we can apply specific operations to a whole column. In the following example, we have changed the `price_cop` unit to millions.

```python
df["price_cop"] = df["price_cop"] / 1e6
df.head()
```

<font size="+1">Practice: Replace Column Values</font>

Try it yourself! Define a dictionary to replace values in `price_cop`. Replace 400 to 0, 850 to 1. 

```python
replace_value = ...
```

#### Replace values


#### Concatenating

When we **concatenate** data, we're combining two or more separate sets of data into a single large dataset.

##### Concatenating DataFrames

If we want to combine two DataFrames, we need to import Pandas and read in our data.

```python
df1 = pd.read_csv("data/colombia-real-estate-1.csv")
df2 = pd.read_csv("data/colombia-real-estate-2.csv")
print("df1 shape:", df1.shape)
print("df2 shape:", df2.shape)
```

Next, we'll use the `concat` method to put our DataFrames together, using each DataFrame's name in a list. 

```python
concat_df = pd.concat([df1, df2])
print("concat_df shape:", concat_df.shape)
concat_df.head()
```

<font size="+1">Practice</font>

Try it yourself! Create two DataFrames from `colombia-real-estate-2.csv` and `colombia-real-estate-3.csv`, and concatenate them as the DataFrame `concat_df`.

```python
df2 = ...
df3 = ...
concat_df = ...
concat_df.head()
```

##### Concatenating Series

We can also concatenate a Series using a similar set of commands. First, let's take two Series from the `df1` and `df2` respectively.

```python
df1 = pd.read_csv("data/colombia-real-estate-1.csv")
df2 = pd.read_csv("data/colombia-real-estate-2.csv")
sr1 = df1["property_type"]
sr2 = df2["property_type"]
print("len sr1:", len(sr1)),
print(sr1.head())
print()
print("len sr2:", len(sr2)),
print(sr2.head())
```

Now that we have two Series, let's put them together.

```python
concat_sr = pd.concat([sr1, sr2])
print("len concat_sr:", len(concat_sr)),
print(concat_sr.head())
```

<font size="+1">Practice</font>

Try it yourself! Use the `colombia-real-estate-2` and `colombia-rea-estate-3` datasets to create a concatenated Series for the `area_m2` column, and print the result.

```python
df1 = ...
```


#### Saving a DataFrame as a CSV
Once you’ve cleaned all your data and gotten the DataFrame to show everything you want it to show, it’s time to save the DataFrame as a new CSV file using the [`to_csv`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html?highlight=to_csv#pandas.DataFrame.to_csv) method. First, let's load up the `colombia-real-estate-1` dataset, and use `head` to see the first five rows of data:

```python
import pandas as pd

df = pd.read_csv("data/colombia-real-estate-1.csv")
df.head()
```

Maybe we're only interested in those first five rows, so let's save that as its own new CSV file using the `to_csv` method. Note that we're setting the `index` argument to `False` so that the DataFrame index isn't included in the CSV file.

```python
df = df.head()
df.to_csv("data/small-df.csv", index=False)
```

#### References & Further Reading 

- [Tutorial for `shape`](https://www.w3resource.com/pandas/dataframe/dataframe-shape.php)
- [Tutorial for `info`](https://www.w3schools.com/python/pandas/ref_df_info.asp)
- [Adding columns to a DataFrame](https://pandas.pydata.org/pandas-docs/version/1.0.5/getting_started/intro_tutorials/05_add_columns.html)
- [Creating DataFrame from dictionary](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.from_dict.html)
- [Working with JSON](https://realpython.com/python-json/)
- [Dropping columns from a DataFrame](https://www.w3schools.com/python/pandas/ref_df_drop.asp)
- [Splitting columns in a DataFrame](https://www.geeksforgeeks.org/split-a-text-column-into-two-columns-in-pandas-dataframe/)
- [Recasting values](https://www.w3schools.com/Python/pandas/ref_df_astype.asp)
- [Replacing strings](https://www.w3schools.com/python/ref_string_replace.asp)
- [Concatenating DataFrames](https://cmdlinetips.com/2020/04/how-to-concatenate-two-or-more-pandas-dataframes/)
- [From DataFrames to Series](https://datatofish.com/pandas-dataframe-to-series/)
- [Stack Overflow: What is serialization](https://stackoverflow.com/questions/633402/what-is-serialization)
- [Understand Python Pickling](https://www.synopsys.com/blogs/software-security/python-pickling/#:~:text=Pickle%20in%20Python%20is%20primarily,transport%20data%20over%20the%20network.)


### Pandas: Advanced

#### Calculate Summary Statistics for a DataFrame or Series

Many datasets are large, and it can be helpful to get a summary of information in them. Let's load a dataset and examine the first few rows:

```python
import pandas as pd

mexico_city1 = pd.read_csv("./data/mexico-city-real-estate-1.csv")
mexico_city1.head()
```

Let's get a summary description of this dataset.

```python
mexico_city1.describe()
```

Like most large datasets, this one has many values which are missing. The describe function will ignore missing values in each column. You can also remove rows and columns with missing values, and then get a summary of the data that's still there. We need to remove columns first, before removing the rows; the sequence of operations here is important. The code looks like this:

```python
mexico_city1 = mexico_city1.drop(
    ["floor", "price_usd_per_m2", "expenses", "rooms"], axis=1
)
mexico_city1 = mexico_city1.dropna(axis=0)
mexico_city1.head()
```

Let's take a look at our new, cleaner dataset.

```python
mexico_city1.describe()
```

<font size="+1">Practice</font> 

Reload the `mexico-city-real-estate-1.csv` dataset. Reverse the sequence of operations by first dropping all rows where there is a missing value, and then dropping the columns, `floor`, `price_usd_per_m2`,`expenses` and `rooms`. What is the size of the resulting DataFrame?

```python
mexico_city1 = pd.read_csv("./data/mexico-city-real-estate-1.csv")
mexico_city1 = ...
mexico_city1 = mexico_city1.drop(
    ["floor", "price_usd_per_m2", "expenses", "rooms"], axis=1
)  # REMOVERHS
print(mexico_city1.shape)
```

#### Select a Series from a DataFrame

Since the datasets we work with are so large, you might want to focus on a single column of a DataFrame. Let's load up the `mexico-city-real-estate-2` dataset, and examine the first few rows to find the column names.

```python
mexico_city2 = pd.read_csv("./data/mexico-city-real-estate-2.csv")
mexico_city2.head()
```

Maybe we're interested in the `surface_covered_in_m2` column. The code to extract just that one column looks like this:

```python
surface_covered_in_m2 = mexico_city2["surface_covered_in_m2"]
surface_covered_in_m2
```

<font size="+1">Practice</font> 

Select the `price` series from the `mexico-city-real-estate-2` dataset, and load it into the `mexico_city2` DataFrame

```python
price = ...
print(price)
```

#### Subset a DataFrame by Selecting One or More Columns

You may find it more efficient to work with a smaller portion of a dataset that's relevant to you. One way to do this is to select some columns from a DataFrame and make a new DataFrame with them. Let's load a dataset to do this and examine the first few rows to find the column headings:

```python
mexico_city4 = pd.read_csv("./data/mexico-city-real-estate-4.csv")
mexico_city4.head()
```

Let's choose `"operation"`, `"property_type"`, `"place_with_parent_names"`, and `"price"`:

```python
mexico_city4_subset = mexico_city4[
    ["operation", "property_type", "place_with_parent_names", "price"]
```


Once we've done that, we can find the resulting number of entries in the DataFrame:

```python
mexico_city4_subset.shape
```

<font size="+1">Practice</font> 

Load the `mexico-city-real-estate-1.csv` dataset and subset it to obtain the `operation`, `lat-lon` and `place_with_property_names` columns only. How many entries are in the resulting DataFrame?

```python
mexico_city1 = ...
mexico_city1_subset = mexico_city1[
    ["operation", "lat-lon", "place_with_parent_names"]
]  # REMOVERHS?? (not sure what that *means*)
print(mexico_city1_subset.shape)
```

#### Subset the Columns of a DataFrame Based on Data Types

It's helpful to be able to find specific types of entries — typically numeric ones — and put all of these in a separate DataFrame. First, let's take a look at the `mexico-city-real-estate-5` dataset.

```python
mexico_city5 = pd.read_csv("./data/mexico-city-real-estate-5.csv")
mexico_city5.head()
```

The code to subset just the numerical entries looks like this:

```python
mexico_city5_numbers = mexico_city5.select_dtypes(include="number")
mexico_city5_numbers.head()
```

<font size="+1">Practice</font> 

Create a subset of the DataFrame from `mexico-city-real-estate-5` which excludes numbers.

```python
mexico_city3 = ...
mexico_city3_no_numbers = ...
print(mexico_city3_no_numbers.shape)
```

#### Working with `value_counts` in a Series

In order to use the data in a series for other types of analysis, it might be helpful to know how often each value occurs in the Series. To do that, we use the `value_counts` method to aggregate the data. Let's take a look at the number of properties associated with each department in the `colombia-real-estate-1` dataset.

```python
df1 = pd.read_csv("data/colombia-real-estate-1.csv", usecols=["department"])
df1["department"].value_counts()
```

<font size="+1">Practice</font>

Try it yourself! Aggregate the different property types in the `colombia-real-estate-2` dataset.

```python
df2 = ...
```


#### Series and `Groupby`

Large Series often include data points that have some attribute in common, but which are nevertheless not grouped together in the dataset. Happily, pandas has a method that will bring these data points together into groups. 

Let's take a look at the `colombia-real-estate-1` dataset. The set includes properties scattered across Colombia, so it might be useful to group properties from the same department together; to do this, we'll use the `groupby` method. The code looks like this:

```python
dept_group = df1.groupby("department")
```

To make sure we got all the departments in the dataset, let's print the first occurrence of each department.

```python
dept_group.first()
```

<font size="+1">Practice</font>

Try it yourself! Group the properties in `colombia-real-estate-2` by department, and print the result.

```python
df2 = ...
dept_group = ...
dept_group.first()
```

Now that we have all the properties grouped by department, we might want to see the properties in just one of the departments. We can use the `get_group` method to do that. If we just wanted to see the properties in `"Santander"`, for example, the code would look like this: 

```python
dept_group1 = df1.groupby("department")
dept_group1.get_group("Santander")
```

We can also make groups based on more than one category by adding them to the `groupby` method. After resetting the `df1` DataFrame, here's what the code looks like if we want to group properties both by `department` and by `property_type`.

```python
df1 = pd.read_csv("data/colombia-real-estate-1.csv")
dept_group2 = df1.groupby(["department", "property_type"])
dept_group2.first()
```

<font size="+1">Practice</font>

Try it yourself! Group the properties in `colombia-real-estate-2` by department and property type, and print the result.

```python
dept_group = ...
dept_group.first()
```

Finally, it's possible to use `groupby` to calculate aggregations. For example, if we wanted to find the average property area in each department, we would use the `.mean()` method. This is what the code for that looks like:

```python
dept_group = df1.groupby("department")["area_m2"].mean()
dept_group
```

*Practice*
Try it yourself! Use the `.mean` method in the `colombia-real-estate-2` dataset to find the average price in Colombian pesos (`"price_cop"`) for properties in each `"department"`.

```python
dept_group = ...
dept_group
```

#### Subset a DataFrame's Columns Based on the Column Data Types

It's helpful to be able to find entries of a certain type, typically numerical entries, and put all of these in a separate DataFrame. Let's load a dataset to see how this works:

```python
mexico_city5 = pd.read_csv("./data/mexico-city-real-estate-5.csv")
mexico_city5.head()
```

Now let's get only numerical entries:

```python
mexico_city5_numbers = mexico_city5.select_dtypes(include="number")
mexico_city5_numbers.head()
```

Let's now find all entries which are not numerical entries:

```python
mexico_city5_no_numbers = mexico_city5.select_dtypes(exclude="number")
mexico_city5_no_numbers.head()
```

<font size="+1">Practice</font> 

Create a subset of the DataFrame from `mexico-city-real-estate-5.csv` which excludes numbers. How many entries does it have?

```python
mexico_city3 = ...
mexico_city3_no_numbers = ...
print(mexico_city3_no_numbers.shape)
```

#### Subset a DataFrame's columns based on column names

To subset a DataFrame by column names, either define a list of columns to include or define a list of columns to exclude. Once you've done that, you can retain or drop the columns accordingly. For example, let's suppose we want to modify the `mexico_city3` dataset and only retain the first three columns. Let's define two lists, one with the columns to retain and one with the columns to drop:

```python
drop_cols = [
    "lat-lon",
    "price",
    "currency",
    "price_aprox_local_currency",
    "price_aprox_usd",
    "surface_total_in_m2",
    "surface_covered_in_m2",
    "price_usd_per_m2",
    "price_per_m2",
    "floor",
    "rooms",
    "expenses",
    "properati_url",
]

keep_cols = ["operation", "property_type", "place_with_parent_names"]
```

Next, we'll explore both approaches to subset `mexico_city3`. To retain columns based on `keep_cols`:

```python
mexico_city3_subsetted = mexico_city3[keep_cols]
```

To drop columns in `drop_cols`:

```python
mexico_city3_subsetted = mexico_city3.drop(columns=drop_cols)
```

<font size="+1">Practice</font> 

Create a subset of the DataFrame from `mexico-city-real-estate-3.csv` which excludes the last two columns.



##### Pivot Tables

A pivot table allows to aggregate and summarize a DataFrame across multiple variables. For example, let's suppose we wanted to calculate the mean of the `price` column in the `mexico_city3` dataset for the different values in the `property_type` column:

import numpy as np

mexico_city3_pivot = ...
mexico_city3_pivot

#### Subsetting with Masks

Another way to to create subsets from a larger dataset is through **masking**. Masks are ways to filter out the data you're not interested in so that you can focus on the data you are. For example, we might want to look at properties in Colombia that are bigger than 200 square meters. In order to create this subset, we'll need to use a mask. 

First, we'll reset our `df1` DataFrame so that we can draw on all the data in its original form. Then we'll create a statement and then assign the result to `mask`.

df1 = pd.read_csv("data/colombia-real-estate-1.csv")
mask = df1["area_m2"] > 200
mask.head()

Notice that `mask` is a Series of Boolean values. Where properties are smaller than 200 square meters, our statement evaluates as `False`; where they're bigger than 200, it evaluates to `True`.

Once we have our mask, we can use it to select all the rows from `df1` that evaluate as `True`.

df1[mask].head()

<font size="+1">Practice</font>

Try it yourself! Read `colombia-real-estate-2` into a DataFrame named `df2`, and create a mask to select all the properties that are smaller than 100 square meters.

df2 = ...
mask = ...
df2[mask].head()

We can also create masks with multiple criteria using `&` for "and" and `|` for "or." For example, here's how we would find all properties in Atlántico that are bigger than 400 square meters.

mask = (df1["area_m2"] > 400) & (df1["department"] == "Atlántico")
df1[mask].head()

<font size="+1">Practice</font>

Try it yourself! Create a mask for `df2` to select all the properties in Tolima that are smaller than 150 square meters.

mask = ...
df2[mask].head()

##### Reshape a DataFrame based on column values

##### What's a pivot table?

A pivot table allows you to quickly aggregate and summarize a DataFrame using an aggregation function. For example, to build a pivot table that summarizes the mean of the `price_cop` column for each of the unique categories in the `property_type` column in `df2`:

import numpy as np

pivot1 = pd.pivot_table(df2, values="price_cop", index="property_type", aggfunc=np.mean)
pivot1

<font size="+1">Practice</font>

Try it yourself! build a pivot table that summarizes the mean of the `price_cop` column for each of the unique departments in the `department` column in `df2`:

```python
# REMOVE {
pivot2 = pd.pivot_table(df2, values="price_cop", index="department", aggfunc=np.mean)
# REMOVE }
pivot2
```

##### Combine multiple categories in a Series

Categorical variables can be collapsed into a fewer number of categories. One approach is to retain the values of the most frequently observed values and collapse all remaining values into a single category. For example, to retain only the values of the top 10 most frequent categories in the `department` column and then collapse the other categories together, use `value_counts` to generate the count of the values:

```
df2["department"].value_counts()
```

Next, select just the top 10 using the `head()` method, and select the column names by using the `index` attribute of the series:

```
top_10 = df2["department"].value_counts().head(10).index
```

Finally, use the apply method and a lambda function to select only the values from the `department` column and collapse the remaining values into the value `Other`:

```
df2["department"] = df2["department"].apply(lambda x: x if x in top_10 else "Other")
```

<font size="+1">Practice</font>

Try it yourself! Retain the remaining top 5 most frequent values in the `department` column and collapse the remaining values into the category `Other`. 



#### Cross Tabulation

The pandas `crosstab` function is a useful for working with grouped summary statistics for **categorical** data. It starts by picking two categorical columns, then defines one as the index and the other as the column. If the aggregate function and value column is not defined, `crosstab` will simply calculate the frequency of each combination by default. Let's see the example below from the Colombia real estate dataset.

```python
import pandas as pd

df = pd.read_csv("data/colombia-real-estate-1.csv")
df.head()
```

The following function calculates the frequency of each combination for two variables, `department` and `property_type`, in the data set.

```
pd.crosstab(index=df["department"], columns=df["property_type"])
```

From the previous example, you can see we have created a DataFrame with the index showing unique observation in variable `department`, while the columns are the unique observation for the variable `property_type`. Each cell shows how many data points there are for each combination of `department` type and `property_type`. For example, there are 8 `apartments` in department `Antioquia`. 

We can further specify a value column and an aggregate function, like in `pivot_table`, to conduct more complicated calculations for the two categorical variables. In the following example, we're looking at the average area size for different property types in the departments in Colombia.

```
import numpy as np

pd.crosstab(
    index=df["department"],
    columns=df["property_type"],
    values=df["area_m2"],
    aggfunc=np.mean,
).round(0)
```
<font size="+1">Practice</font> 

Create a cross tabulate calculating frequency of combinations from `mexico-city-real-estate-3.csv` using `currency` as the index and `property_type` as the column.

```
# Read dataset
mexico_city3 = ...

# Create `crosstab`
```


#### Applying Functions to DataFrames and Series

`apply` is a useful method for to using one function on all the rows or columns of a DataFrame efficiently. Let's take the following real estate dataset as an example:

```
# Read data, only use the numerical columns
df = pd.read_csv("data/colombia-real-estate-2.csv", usecols=["area_m2", "price_cop"])
df.head()
```

By specifying the function inside `apply()`, we can transform the whole DataFrame. For example, I am calculating the square root of each row at each column:

```
import numpy as np

df.apply(np.sqrt)
```

Note you can also specify the `"axis"` inside `apply`. By default we have `axis=0`, which means we are applying the function to each column. We can also switch to `axis=1` if we want to apply the function to each row. See the following example showing the sum of all rows for each column:

```
df.apply(np.sum, axis=0)
```

The following code will get the sum of all columns for each row:

```
df.apply(np.sum, axis=1)
```

By specifying the column name, we can also apply the function to a specific column or columns. Note that we can also specify index (row names) to only apply functions to specific rows, however, it is not common in practice.

```
df["area_m2"].apply(np.sqrt)
```

We can assign the results to a new column:

```python
df["area_sqrt"] = df["area_m2"].apply(np.sqrt)
df
```

<font size="+1">Practice</font>

Try it yourself! Create a new column named 'sum_columns', which is the sum of all numerical columns in `df`:

```python
df["sum_columns"] = ...
df.head()
```

`df.aggregate()`, or `df.agg()`, shares the same concept as `df.apply()` in terms of applying functions to a DataFrame, but `df.aggregate()` can only apply aggregate functions like `sum`, `mean`, `min`, `max`, etc. See the following example for more details:

```python
df = pd.read_csv("data/colombia-real-estate-2.csv", usecols=["area_m2", "price_cop"])
df.head()
```

We can check what's the minimum number for each column calling the `min` aggregate function:

```python
df.agg("min")
```

Like `apply()`, we can also specify the `axis` argument to switch axis:

```python
df.agg("min", axis=1)
```

We can apply aggregate function to a whole DataFrame using `df.agg()`, or specify the column name for a subset of DataFrame:

```python
df["area_m2"].agg("min")
```

We can also apply a list of aggregate functions to a DataFrame:

```python
df.agg(["sum", "max"])
```

The syntax above will calculate both `sum` and `max` for each column, and store the result as index. Besides, we can also apply different aggregate functions to different columns. In this case, we need to pass a dictionary specifying key as column names, and value as corresponding aggregate function names:

```python
df.agg({"area_m2": "sum", "price_cop": "min"})
```

<font size="+1">Practice</font>

Try it yourself! Find the minimum for column `area_m2` and the maximum for column `price_cop` using `df.agg()`:



#### References & Further Reading
- [Pandas Documentation on Dropping a Column in a DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.drop.html)
- [Pandas Documentation on Printing out the First Few Rows of a DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.head.html)
- [Pandas Documentation on Reading in a CSV File Into a DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html)
- [Getting Started with Pandas Documentation](https://pandas.pydata.org/docs/getting_started/intro_tutorials/01_table_oriented.html#min-tut-01-tableoriented)
- [Pandas Documentation on Extracting a Column to a Series](https://pandas.pydata.org/docs/getting_started/intro_tutorials/01_table_oriented.html#each-column-in-a-dataframe-is-a-series)
- [Pandas Official Indexing Guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html)
- [Series in pandas](https://www.geeksforgeeks.org/python-pandas-series/)
- [Tutorial for `value_counts`](https://www.geeksforgeeks.org/python-pandas-series-value_counts/)
- [Tutorial for `groupby`](https://pandas.pydata.org/pandas-docs/dev/reference/api/pandas.DataFrame.groupby.html)
- [pandas Documentation for `groupby`](https://pandas.pydata.org/pandas-docs/version/0.25.3/reference/api/pandas.core.groupby.GroupBy.mean.html)
- [Pandas Official Indexing Guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html)
- [Online Examples of Selecting Numeric Columns of a DataFrame](https://pythonexamples.org/pandas-dataframe-select-columns-of-numeric-datatype/)
- [Official Pandas Documentation on Data Types in a DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.select_dtypes.html)
- [Pandas documentation for Boolean indexing](https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#boolean-indexing)
- [More information on creating various kinds of subsets](https://datacarpentry.org/python-ecology-lesson/03-index-slice-subset/index.html#subsetting-data-using-criteria)
- [More on boolean indexing](https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#boolean-indexing)
- [A tutorial on using various criteria to create subsets](https://datacarpentry.org/python-ecology-lesson/03-index-slice-subset/index.html#subsetting-data-using-criteria)
- [Pandas.DataFrame.apply](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html)
- [Pandas.DataFrame.aggregate](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.aggregate.html)




## Python basics
### basics(topics only)
- simple calculations: DMAS, modulo, etc. 
- order of operations: PEMDAS: Parentheses Exponents Multiplication Addition Subtraction
- Data types:  ^118ca3
	- boolean(bool)
	- String(str): any kind of information that can be represented with letters
		- some string operations
			- `.glob` function: used for pattern matching
			- f-strings: 
			-
	- Numeric(`int`,`float`,`complex`)
	- sequence(`list`,`tuple`,`set`) : Data that is a collection of discrete items.
		-  concept: iterators and iterables
			- a list is an **iterable**, meaning that we can **iterate** through it one item at a time
			- If we try to bring in a large database — over a million values, for example — asking for every action to be applied to every value will take up a huge amount of memory
			- Iterators are helpful because they allow us to free up memory to use for other tasks
				```python
					from pymongo import MongoClient
					client = MongoClient(host="localhost", port=27017)
					(list(client.list_databases()))
				
					# if we want to examine each database by itself, we can use
					results = client.list_databases()
					print((results))
				```
		- [[list]]: collection that is ordered and changeable. It's designated using square brackets `[]`, and items can be of *different data types*: `["red", 1, 1.03, 1]`.
			- creating lists: can be done by `price_usd=[1234,1345,2345]`
			- access list item: ==Lists are indexed from 0 onwards. First item in list is indexed 0==
				- access 2nd item in above list by using `price_usd[1]`
				- access last item in list by [[negetive indexing]] `price_usd[-1]`
			- append to list using `price_usd.append(1234)`
			- Can find the sum of items in a list using `sum(price_usd)`. 
			- average of items in a list
				```python
				average_usd = sum(price_usd)/len(price_usd)
				
				```
			- **zipping lists**: pairing the values of items in 2 lists together. 
				```python
				new_list = zip(price_usd, area_m2)
				zipped_list = list(new_list)
				```
			- putting a list in a list as above is called a [[generator]].
		- A `tuple` is a collection which is ordered and unchangeable. It's designated using parentheses `()`: `("red", 1, 1.03, 1)`
		- A `set` is a collection which is unordered, unchangeable, and does not permit duplicate items. It's designated using curly brackets `{}`: `{"red", 1, 1.03}`.
	- **Binary** (`bytes`, `bytearray`, `memoryview`)**:**
		- Used to manipulate and display binary data. That is, data that can be expressed with integers represented with base 2.
		- Unlike the other data types described above, `binary` types are not human-readable.
	- Mapping (`dict`)**:** 
		- Dictionaries store data in *key-value* pairs. 
		- They're designated using curly brackets `{}`, like a `set`, but notice that keys and values are associated with each other using a colon `:`.
		- Each pair is separated from the next using a comma `,`
		- example code
		```python
		dict1 = {
					  "department": "quindio", 
					  "property_type": "house", 
					  "price_usd": 330899.98
					  } 
		```
	
- For loops
	- example code: 
		```python
		price_usd = [97919.38, 300511.20, 293758.14, 540244.86]
		for x in price_usd:
		    print(x)
		````

- Python dictionaries
	- example code: 
		```python
		# this is a dict
		colomdict = {
		    "property_type": "house",
		    "department": "quindio",
		    "area": 235.0,
		}
		
		# this is how to access an item in dict
		x = colomdict["department"]
		print(x)
		
		## i.e. you reference it by using its 'key' value(the a in a:b). note that b ia called 'value'
		
		```

- [[JSON]] is a text format for storing and transporting data. It works by creating [[key-value pairs]]. JSON can be strings, numbers, objects, arrays, boolean data, or null
	- 
		```python 
		[
		    {"property_type": "house", "department": "bogota"},
		    {"property_type": "house", "department": "bogota"},
		    {"property_type": "house", "department": "bogota"},
		]
		# there can be other entries also. You can think of it almost as a table. 
		```







## Pandas


## Visualisation with Matplotlib

## sql and mongodb

## ML basics

## time series

