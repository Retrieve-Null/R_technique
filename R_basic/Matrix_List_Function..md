## 1. Matrix and List

```r
m <- matrix(1:9, nrow = 3)
colnames(m) <- c("a","b","c") # column names

m[2,]
m[,1]
m[2,3]
m[2:3,1:2]

t(m) # transpose
as.data.frame(m) # convert matrix to data frame
```

##### List

```r
l <- list(m=matrix(1:9, nrow = 3),
          df=data.frame(gene  = paste0("gene",1:3),
                        sam   = paste0("sample",1:3),
                        exp   = c(32,34,45)),
          x=c(1,3,5))
l

l[[2]] # use double brackets or $ to extract an element, single bracket returns a list containing the element
l$df
```

##### Extra: names of elements

```r
scores = c(100,59,73,95,45)
names(scores) = c("jimmy","nicker","Damon","Sophie","tony")
scores
scores["jimmy"]
scores[c("jimmy","nicker")]

names(scores)[scores>60]
```

##### Deletion

```r
rm(l)
rm(df,m)
rm(list = ls()) # clear all variables
```

## 2. Functions

##### Basic structure

```r
x <- function(parameters){[content]}
```

##### Fibonacci sequence

```r
fibo <- function(n) {
  if(n %in% c(1,2)){print(1)}
    else { a1=1
           a2=1
           for (i in 3:n) {
                           a3=a1+a2
                           a1=a2
                           a2=a3
                          }
           print(a3)
         }
}
```

##### When a piece of code needs to be copy-pasted three times, it should be written as a function or loop

```r
jimmy <- function(i){
  plot(iris[,i],col=iris[,5])
}

jimmy(1)
jimmy(2)
jimmy(3)
jimmy(4)
```
