# R Basics: if, for, and apply

## if and for

### if
```r
i = -1
if (i < 0) print('up')
if (i > 0) print('up')
```

### if-else
```r
i = 1
if (i > 0){
  print('+')
} else {
  print("-")
}

ifelse(i > 0, "+", "-")
```

### multiple conditions
```r
i = 0
if (i > 0){
  print('+')
} else if (i == 0) {
  print('0')
} else if (i < 0){
  print('-')
}

ifelse(i > 0, "+", ifelse((i < 0), "-", "0"))
```

---

### for loop
```r
x <- c(5,6,0,3)
s = 0
for (i in x){
  s = s + i
  print(c(i,s))
}

s = 0
result = list()
for(i in 1:length(x)){
  s = s + x[[i]]
  result[[i]] = c(x[[i]], s)
}
do.call(cbind, result)
```

---

## Implicit loops: apply

### apply
```r
test <- iris[1:6,1:4]
apply(test, 2, mean)
apply(test, 1, sum)
```

### lapply
```r
test <- list(x = 36:33, y = 32:35, z = 30:27)
lapply(test, mean)
lapply(test, fivenum)
```

### sapply
```r
sapply(test, mean)
sapply(test, fivenum)
class(sapply(test, fivenum))
```
