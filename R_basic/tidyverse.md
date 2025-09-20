## Common Functions and tidyverse

##### 1. arrange() for sorting data

```r
arrange(mtcars, cyl, disp) # multiple columns
arrange(mtcars, desc(disp)) # descending order
```

##### 2. Wide to long format

* Combine multiple columns into one

```r
pdat = dat %>% 
  pivot_longer(cols = starts_with("gene"), # columns to merge
               names_to = "gene",           # merged into column "gene"
               values_to = "count")         # values into column "count"
```

##### 3. Handling NA values

###### Original data

```r
X <- data.frame(X1 = LETTERS[1:5], X2 = 1:5)
X[2,2] <- NA
X[4,1] <- NA
X
```

* Remove rows with NA (can specify column)

```r
drop_na(X)
drop_na(X, X1)
drop_na(X, X2)
```

* Replace NA

```r
replace_na(X, list(X2 = 0)) # replace NA with 0
```

* Fill NA with previous row value

```r
X
fill(X, X2)
```

##### 4. Joining two datasets

```r
test1 <- data.frame(name = c('jimmy','nicker','Damon','Sophie'), 
                    blood_type = c("A","B","O","AB"))
test1
test2 <- data.frame(name = c('Damon','jimmy','nicker','tony'),
                    group = c("group1","group1","group2","group2"),
                    vision = c(4.2,4.3,4.9,4.5))
test2
```

```r
library(dplyr)
inner_join(test1,test2,by="name")
right_join(test1,test2,by="name")
full_join(test1,test2,by="name")
semi_join(test1,test2,by="name") # rows of test1 where name %in% test2
anti_join(test1,test2,by="name") # rows of test1 where name !%in% test2
```

##### 5. String operations (stringr)

```r
x <- "The birch canoe slid on the smooth planks."
```

* String length

```r
str_length(x)
length(x)
```

* Split and combine

```r
str_split(x, " ")
x2 = str_split(x, " ")[[1]]; x2

y = c("jimmy 150","nicker 140","tony 152")
str_split(y, " ")
str_split(y, " ", simplify = TRUE)

x2
str_c(x2, collapse = " ")
str_c(x2, 1234, sep = "+")
```

* Extract substring

```r
str_sub(x, 5, 9)
```

* Locate substring

```r
str_locate(x2, "th")
str_locate(x2, "h")
```

* Detect substring

```r
str_detect(x2, "h")
```

With `sum` and `mean`, count matches and compute proportion:

```r
sum(str_detect(x2, "h"))
mean(str_detect(x2, "h"))
```

* Replace substrings

```r
str_replace(x2, "o", "A")
str_replace_all(x2, "o", "A")
```

* Extract matches

```r
str_extract(x2, "o|e")
str_extract_all(x2, "o|e")
str_extract_all(x2, "o|e", simplify = TRUE)
```

* Remove characters

```r
str_remove(x, " ")
str_remove_all(x, " ")
```
