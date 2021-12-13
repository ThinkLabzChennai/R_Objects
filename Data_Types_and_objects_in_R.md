---
title: 
        Introduction to Data Types and    
         Structures in R   
author:    
    -  "RSN_Thinklabz_Chennai"
output:
  html_document:
    keep_md: true
    toc: true

---



# Introduction
   
   The main aim of this notes is to provide an introduction to data types and structures in R.
   We shall try to understand each one of them with an example.
 
   
## Data Types
Generally, while doing programming, we need to use variables to store various information. Variables are reserved memory locations to store values i.e when we create a variable we allocate some memory space. In R the variable is an object. An object is a data structure having few attributes and methods which are applied to its attributes.   
   
   Variables can be broadly divided in to two types such as Numerical and Character.
   
   Character variables are called Factors and divided in to two types. Factor variable is considered nominal if it represents a name(e.g names of persons) and ordered factors are called ordinal variable (e.g satisfactory level of user from extremly poor to extremely good). Numeric variables are either Interval or Ratio.
Let us look at the data types in R.

### Double
Doubles are used to represent continuous variables. Some examples are Time taken by all the athletes for completing a single lap in a race, height of boxers participatig in a tournament.
 To know a particular variable's data type we can use **`typeof()`**


```r
numeric_var=22.9
typeof(numeric_var)
```

```
[1] "double"
```

### Integer
Integers are natural numbers. They can be used to represent counting variables, for example the number of pins in a box.

```r
pins=as.integer(100)
typeof(pins)
```

```
[1] "integer"
```

### Complex
To represent complex numbers object of type complex is used. For creating object of type complex use **`as.complex()`** or **`complex`** functions.


```r
comp1=as.complex(35+7i)
comp2=complex(real=2,im=1)
typeof(comp1)
```

```
[1] "complex"
```

```r
typeof(comp2)
```

```
[1] "complex"
```

### Logical
An object of data type logical can have the value TRUE or FALSE and is used to indicate if a condition is true or false. Such objects are usually the result of logical expressions.


```r
num1=12
num2=23
num1>num2
```

```
[1] FALSE
```

### Character
A character object is represented by a collection of Alphabets,numbers and some symbols between double quotes (" ").


```r
char="string"
typeof(char)
```

```
[1] "character"
```

### Factor
The factor data type is used to represent categorical data (i.e. data of which the value range is a collection of codes.). In factor variables mostly few possible values will be seen. These values are called LEVELS. For example: variable 'Gender' with values male and female.

```r
Gender=factor(c("male","male","female","male","female"))
# We can look at levels using
levels(Gender)
```

```
[1] "female" "male"  
```

Ordered factor

```r
satisfaction=as.factor(c("Extremely poor","bad",'moderate',"good","Extremely good","Extremely poor","good","moderate"))
levels(satisfaction)
```

```
[1] "bad"            "Extremely good" "Extremely poor" "good"          
[5] "moderate"      
```



## Data Structures
  R has a wide variety of data Structures including vectors, matrices, arrays, data frames, tables and lists. 


### Vectors
The simplest data structure in R is the vector. A vector is an object that consists of a number of elements of the same type, all doubles or all logical. Vector can be constructed using **`c()`**

```r
# numeric vector
a <- c(11,25,15.43,-.6,-2,4) 
# character vector
b <- c("first","second","third") 
#logical vector
c <- c(TRUE,TRUE,FALSE,TRUE,TRUE) 
```

We can also create a vector using operators. 

```r
#Addition operator
x=43+2
#Sequence operator
z=1:100
```

### Matrices
A matrix can be regarded as a generalization of a vector. As with vectors, all the elements of a matrix must be of the same data type. A matrix can be generated in several ways

   
   1)Using **`dim()`**

```r
m=1:21
dim(m)=c(7,3)
m
```

```
     [,1] [,2] [,3]
[1,]    1    8   15
[2,]    2    9   16
[3,]    3   10   17
[4,]    4   11   18
[5,]    5   12   19
[6,]    6   13   20
[7,]    7   14   21
```
   
   2) Using **`matrix()`**

```r
m=matrix(1:20,5,4)
m
```

```
     [,1] [,2] [,3] [,4]
[1,]    1    6   11   16
[2,]    2    7   12   17
[3,]    3    8   13   18
[4,]    4    9   14   19
[5,]    5   10   15   20
```

### Arrays
Arrays are generalizations of vectors and matrices. A vector is a one-dimensional array and a matrix is a two dimensional array. As with vectors and matrices, all the elements of an array must be of the same data type. One can create an array easily with the array() function, where one give the data as the first argument and a vector with the sizes of the dimensions as the second argument. The number of dimension sizes in that argument gives you the number of dimensions. For example, an array with four columns, two rows, and two "tables" like this

```r
s=array(1:16,dim=c(4,2,2))
s
```

```
, , 1

     [,1] [,2]
[1,]    1    5
[2,]    2    6
[3,]    3    7
[4,]    4    8

, , 2

     [,1] [,2]
[1,]    9   13
[2,]   10   14
[3,]   11   15
[4,]   12   16
```

### Data Frames
Data frames can also be regarded as an extension to matrices. Data frames can have columns of different data types and are the most convenient data structure for data analysis in R. In fact, most statistical modeling routines in R require a data frame as input.   
R has many built in Data Frames, For example let us look at iris data 

```r
head(iris)
```

```
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa
```
A data frame can have the attribute names and row.names. The attribute names contain the column names of the data frame and the attribute row.names contains the row names of the data frame. Data frames are always in rectangular form and must have equal number of elements.
   
   Data frame can be created using 
**`data.frame()`**

```r
name=c("statistics","data sciene","mathematics")
Academy=c("a","b","c")
da=data.frame(name,Academy)
da
```

```
         name Academy
1  statistics       a
2 data sciene       b
3 mathematics       c
```

### Tables
Another common way to store information is in a table. First let us see how to create one way table. One way to create a table is using the table command. The argument it takes is a vector of factors, and it calculates the frequency that each factor occurs

```r
a=factor(c("1","a","b","2","a","1","1","2","1","2"))
Ta=table(a)
Ta
```

```
a
1 2 a b 
4 3 2 1 
```

Another way to create table is

```r
a=matrix(1:9,3,3)
colnames(a)=c("A","B","C")
rownames(a)=c("good","better","best")
as.table(a)
```

```
       A B C
good   1 4 7
better 2 5 8
best   3 6 9
```

### Lists
A list is like a vector. However, an element of a list can be an object of any type and structure. Consequently, a list can contain another list and therefore it can be used to construct arbitrary data structures.   
A list can also be constructed by using the function **`list()`**. The names of the list components and the contents of list components can be specified as arguments of the list function by using the '=' character.

```r
a1=c(22,34,21,22,45,123,1454,23)
b1=c("maths","physics","computer scicence",'statistics')
y=list(marks=a1,subject=b1)
```

Here marks and subjects are tags of list elements, we can access the tags using '$' 

```r
y$marks
```

```
[1]   22   34   21   22   45  123 1454   23
```

Accessing elements using position

```r
# getting as vector
x1=y[[2]]
typeof(x1)
```

```
[1] "character"
```

```r
# getting as list
x2=y[1];x2
```

```
$marks
[1]   22   34   21   22   45  123 1454   23
```

```r
typeof(x2)
```

```
[1] "list"
```



# Final Note
In the notes we have seen various data types such as   

+ double   
+ integer   
+ complex   
+ logical   
+ character   
+ factor 
   
   and data structures like   
   
   + vector   
   + matrix   
   + array   
   + dataframe    
   + list 
