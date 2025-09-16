## Installing R packages

##### Three main methods

```r
install.packages("tidyr")

BiocManager::install("ggplot2")

devtools::install_github("jmzeng1314/idmap1") # inside parentheses: username + package name
```

##### Install only if not already installed

```r
if(!require(stringr)) install.packages("stringr") # require() checks if installed
```

| Symbol |                                         Meaning |
| -----: | ----------------------------------------------: |
|     () |                                        function |
|    \[] |                 subset for vector or data frame |
| \[\[]] |                       extract element from list |
|     \$ | select column from data frame, subset from list |
|     {} |                          multiple lines of code |
