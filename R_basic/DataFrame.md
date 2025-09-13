## Data frame

```r
df <- data.frame(gene    = paste0("gene",1:4),
                 change  = rep(c("up","down"),each = 2),
                 score   = c(5,3,-2,-4))
df
```

```r
df2 <- read.csv("gene.csv")
df2
```

##### 1. Data frame attributes

```r
dim(df) # dimensions (rows, columns)
nrow(df) # number of rows
ncol(df) # number of columns
```

```r
rownames(df) # row names, column names are vectors and can be reassigned
colnames(df)
```

##### 2. Subsetting a data frame

```r
df$score  # access score, try pressing tab for autocomplete
mean(df$score)
```

##### By index

```r
df[2,2]
df[2,]
df[,2]
df[c(1,3),1:2]
```

##### By name

```r
df[,"gene"]
df[,c('gene','change')]
```

##### By condition (logical values)

```r
df[df$score>0,]
```

##### 3. Editing a data frame

- Modify a single cell

```r
df[3,3]<- 5
df
# Modify a whole column
df$score<-c(12,23,50,2)     
df
```

- Add a new column

```r
df$p.value <-c(0.01,0.02,0.07,0.05) 
df
```

- Change row names and column names

```r
rownames(df) <- c("r1","r2","r3","r4")
```

- Modify only a specific column name

```r
colnames(df)[2]="CHANGE"
```

##### 4. Advanced data frame usage

- For large data frames, view the first/last few rows

```r
iris
head(iris)
head(iris,3)
tail(iris)
```

- For large row and column numbers, view a subset

```r
iris[1:3,1:3]
```

- View the data type and structure of each column

```r
str(df) # str means structure
str(iris)
```

- Remove rows with missing values

```r
df<-data.frame(X1 = LETTERS[1:5],X2 = 1:5)
df[2,2] <- NA
df[4,1] <- NA
df

na.omit(df) # remove rows with missing values
```

##### 5. Merging two data frames

```r
test1 <- data.frame(name = c('jimmy','nicker','Damon','Sophie'), 
                    blood_type = c("A","B","O","AB"))

test2 <- data.frame(name = c('Damon','jimmy','nicker','tony'),
                    group = c("group1","group1","group2","group2"),
                    vision = c(4.2,4.3,4.9,4.5))


test3 <- data.frame(NAME = c('Damon','jimmy','nicker','tony'),
                    weight = c(140,145,110,138))
merge(test1,test2,by="name") 
merge(test1,test3,by.x = "name",by.y = "NAME")
```
