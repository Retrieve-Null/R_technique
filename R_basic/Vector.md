## 1. Vector
```r
rep("x",times=3)  
seq(from=3,to=21,by=3)
rnorm(n=3) 
paste0(rep("x",times=3),1:3)
```

## 2.Operations on a single vector
* Assign to a variable name

```r
x = c(1,3,5,1) 
x
x <- c(1,3,5,1) 
x
```

* Assign + output at the same time

```r
x <- c(1,3,5,1);x
(x <- c(1,3,5,1))
```

* Simple math calculations

```r
x+1
log(x)
sqrt(x)
```

* Generate a logical vector based on a condition

```r
x>3
x==3
#(4) Basic statistics
max(x) # maximum value
min(x) # minimum value
mean(x) # mean
median(x) # median
var(x) # variance
sd(x) # standard deviation
sum(x) # sum
```

```r
length(x) # length
unique(x) # remove duplicates
duplicated(x) # check if each element is duplicated
table(x) # count occurrences
sort(x)
```

## 3.Operations on two vectors

```r
x = c(1,3,5,1)
y = c(3,2,5,6)
```

* Logical comparison, generating a **logical vector of the same length**

```r
x == y # are the elements of x and y equal at each position
x %in% y # does each element of x exist in y
```

* Math calculation

```r
x + y
```

* Concatenation

```r
paste(x,y,sep=",")
```

* Intersection, union, difference

```r
intersect(x,y)
union(x,y)
setdiff(x,y)
setdiff(y,x)
```

* When the two vectors have different lengths

```r
x = c(1,3,5,6,2)
y = c(3,2,5)
x == y # Ah! warning!
```

---

## 4. Vector filtering (subsetting)

```r
x <- 8:12
# Subset based on logical values
x[x==10]
x[x<12]
x[x %in% c(9,13)]
# Subset based on positions
x[4]
x[2:4]
x[c(1,5)]
x[-4] # remove the 4th element
x[-(2:4)] # remove 2nd, 3rd, 4th elements
```

## 5. Modify certain elements in a vector: subset + assignment

```r
x
# Modify one element
x[4] <- 40
x
# Modify multiple elements
x[c(1,5)] <- c(80,20)
x
```

## 6. Simple vector plotting

```r
k1 = rnorm(12); k1
k2 = rep(c("a","b","c","d"), each = 3); k2
plot(k1)
boxplot(k1 ~ k2) # Try searching what boxplot represents
```

## 7. How to reorder elements

```r
x <- c("A","B","C","D","E"); x
x[c(2, 4, 5, 1, 3)]

scores = c(100,59,73,95,45); scores
sort(scores)
scores[c(5,2,3,4,1)]
```

`scores[order(scores)]` = `sort(scores)`

## 8. What is order used for?
- Scores belong to the following kids:

```r
kids = c("jimmy","nicker","Damon","Sophie","tony")
# How to sort the kids' names by scores from low to high?
kids[order(scores)]
```

## 9. match
- Returns the indices

```r
x <- c("A","B","C","D","E"); x
x[c(2, 4, 5, 1, 3)]
y <- c("B","D","E","A","C") 
match(y,x) # How to arrange x to match y

x[match(y,x)]
```
