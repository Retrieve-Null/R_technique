## Plotting

##### ggplot2

|    Attribute | Parameter |
| -----------: | --------: |
|        Color |     color |
|         Size |      size |
|        Shape |     shape |
| Transparency |     alpha |
|         Fill |      fill |

```r
library(ggplot2)
test = iris
```

##### 1. Basic plotting template: data, x and y axis

```r
ggplot(data = test)+
  geom_point(mapping = aes(x = Sepal.Length,
                           y = Petal.Length))
```

##### 1.1 Manual settings

```r
ggplot(data = test) + 
  geom_point(mapping = aes(x = Sepal.Length,
                           y = Petal.Length), 
             color = "blue")

ggplot(data = test) + 
  geom_point(mapping = aes(x = Sepal.Length, y = Petal.Length), 
             size = 5,     # point size
             alpha = 0.5,  # transparency
             shape = 8)    # point shape
```

##### 1.2 Mapping attributes

```r
ggplot(data = test)+
  geom_point(mapping = aes(x = Sepal.Length,
                           y = Petal.Length,
                           color = Species))
```

##### Q1: Custom colors for mapping?

```r
ggplot(data = test)+
  geom_point(mapping = aes(x = Sepal.Length,
                           y = Petal.Length,
                           color = Species))+
  scale_color_manual(values = c("blue","grey","red"))
```

##### Q2-1 Hollow vs solid shapes (color controls both)

```r
ggplot(data = test)+
  geom_point(mapping = aes(x = Sepal.Length,
                           y = Petal.Length,
                           color = Species),
             shape = 17) # solid

ggplot(data = test)+
  geom_point(mapping = aes(x = Sepal.Length,
                           y = Petal.Length,
                           color = Species),
             shape = 2)  # hollow
```

##### Q2-2 Shapes with border and fill

```r
ggplot(data = test)+
  geom_point(mapping = aes(x = Sepal.Length,
                           y = Petal.Length,
                           color = Species),
             shape = 24,
             fill = "black")
```

##### 2. Facets

```r
ggplot(data = test) + 
  geom_point(mapping = aes(x = Sepal.Length, y = Petal.Length)) + 
  facet_wrap(~ Species)
```

##### Double facet

```r
test$Group = sample(letters[1:5],150,replace = TRUE)
ggplot(data = test) + 
  geom_point(mapping = aes(x = Sepal.Length, y = Petal.Length)) + 
  facet_grid(Group ~ Species)
```

##### Geoms and layering

```r
ggplot(data = test) + 
  geom_smooth(mapping = aes(x = Sepal.Length, 
                          y = Petal.Length))+ 
  geom_point(mapping = aes(x = Sepal.Length, 
                           y = Petal.Length))

ggplot(data = test,mapping = aes(x = Sepal.Length, y = Petal.Length))+ 
  geom_smooth()+
  geom_point()
```

##### Statistical transformations - histogram/bar

```r
View(diamonds)
table(diamonds$cut)

ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut))

ggplot(data = diamonds) + 
  stat_count(mapping = aes(x = cut))
```

##### Transformations use cases

###### 1. Plot raw frequency

```r
fre = as.data.frame(table(diamonds$cut))
fre

ggplot(data = fre) +
  geom_bar(mapping = aes(x = Var1, y = Freq), stat = "identity")
```

###### 2. Count → proportion

```r
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, y = ..prop.., group = 1))
```

##### Position adjustments

###### Jittered scatter plot

```r
ggplot(data = mpg,mapping = aes(x = class, y = hwy)) + 
  geom_boxplot()+
  geom_point()

ggplot(data = mpg,mapping = aes(x = class, y = hwy)) + 
  geom_boxplot()+
  geom_jitter()
```

###### Dotplot (points not overlapping)

```r
ggplot(data = mpg,mapping = aes(x = class, y = hwy)) + 
  geom_boxplot()+
  geom_dotplot(binaxis = "y", binwidth = .5, stackdir = "center")
```

###### Stacked bar plot

```r
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, fill=clarity))
```

###### Side-by-side bar plot

```r
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, fill = clarity), position = "dodge")
```

##### Coordinate systems

* Flip: `coord_flip()`

```r
ggplot(data = mpg, mapping = aes(x = class, y = hwy)) + 
  geom_boxplot() +
  coord_flip()
```

* Polar coordinates: `coord_polar()`

```r
bar <- ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, fill = cut), width = 1) + 
  theme(aspect.ratio = 1) +
  labs(x = NULL, y = NULL)
bar
bar + coord_flip()
bar + coord_polar()
```

##### Saving plots

###### 1. Base plotting save

```r
pdf("iris_box_ggpubr.pdf")
boxplot(iris[,1]~iris[,5])
text(6.5,4, labels = 'hello')
dev.off()
```

###### 2. Save ggplot with ggsave

```r
p <- ggboxplot(iris, x = "Species", 
               y = "Sepal.Length",
               color = "Species", 
               shape = "Species",
               add = "jitter")
ggsave(p, filename = "iris_box_ggpubr.png")
```

###### 3. Save to PowerPoint (editable elements)

```r
library(eoffice)
topptx(p, "iris_box_ggpubr.pptx")
```
