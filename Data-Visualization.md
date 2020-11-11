Data Visualization
================
Curtis Donovan
8/21/2020

# Data Visualization

### 3.1 Introduction

``` r
# we must load the tidyverse library every session
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.3     ✓ dplyr   1.0.2
    ## ✓ tidyr   1.1.1     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.5.0

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

### 3.2 First Steps

Question: Do cars with big engines use more gas then cars with small
engines?

##### 3.2.1 The mpg data frame

``` r
mpg
```

    ## # A tibble: 234 x 11
    ##    manufacturer model    displ  year   cyl trans   drv     cty   hwy fl    class
    ##    <chr>        <chr>    <dbl> <int> <int> <chr>   <chr> <int> <int> <chr> <chr>
    ##  1 audi         a4         1.8  1999     4 auto(l… f        18    29 p     comp…
    ##  2 audi         a4         1.8  1999     4 manual… f        21    29 p     comp…
    ##  3 audi         a4         2    2008     4 manual… f        20    31 p     comp…
    ##  4 audi         a4         2    2008     4 auto(a… f        21    30 p     comp…
    ##  5 audi         a4         2.8  1999     6 auto(l… f        16    26 p     comp…
    ##  6 audi         a4         2.8  1999     6 manual… f        18    26 p     comp…
    ##  7 audi         a4         3.1  2008     6 auto(a… f        18    27 p     comp…
    ##  8 audi         a4 quat…   1.8  1999     4 manual… 4        18    26 p     comp…
    ##  9 audi         a4 quat…   1.8  1999     4 auto(l… 4        16    25 p     comp…
    ## 10 audi         a4 quat…   2    2008     4 manual… 4        20    28 p     comp…
    ## # … with 224 more rows

### 3.2.2 creating a ggplot

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

##### Exercises

1.  Run ggplot(data = mpg). What do you see?

<!-- end list -->

``` r
ggplot(data = mpg)
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-4-1.png)<!-- --> A
grey rectangle, empty canvas.

2.  How many rows are in mpg? How many columns?

<!-- end list -->

``` r
?mpg
```

234 rows and 11 columns

3.  What does the drv variable describe? Read the help for ?mpg to find
    out.

<!-- end list -->

``` r
?mpg
```

The drv variable desribes the type of drive that each car can be,
front-wheel, four-wheel, or rear-wheel.

4.  Make a scatterplot of hwy vs cyl.

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = hwy, y = cyl))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

5.  What happens if you make a scatterplot of class vs drv? Why is the
    plot not useful?

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = class, y = drv))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

``` r
#Because it is just showing you the data again
```

Both variables are categorical.

### 3.3 Aestetic Mappings

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, color = class))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, size = class))
```

    ## Warning: Using size for a discrete variable is not advised.

![](Data-Visualization_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, alpha = class))
```

    ## Warning: Using alpha for a discrete variable is not advised.

![](Data-Visualization_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, shape = class))
```

    ## Warning: The shape palette can deal with a maximum of 6 discrete values because
    ## more than 6 becomes difficult to discriminate; you have 7. Consider
    ## specifying shapes manually if you must have them.

    ## Warning: Removed 62 rows containing missing values (geom_point).

![](Data-Visualization_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy), color = "blue")
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

### 3.3.1 Exercises

1.  What’s gone wrong with this code? Why are the points not blue?

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x =displ, y = hwy, color = "blue"))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

Because the blue is supposed to be outside of the parentheses in this
case to make the points blue.

2.Which variables in mpg are categorical? Which variables are
continuous? (Hint: type ?mpg to read the documentation for the dataset).
How can you see this information when you run mpg?

``` r
?mpg
```

Categorical are the non numerical variables with a limit of items in the
variable. You can see which values are numerical.

3.  Map a continuous variable to color, size, and shape. How do these
    aesthetics behave differently for categorical vs. continuous
    variables?

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x =displ, y = hwy, color = cty))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, size = cty))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

The shape aesthetic can’t handle continuous variables because continious
variables need a much broader range.

4.  What happens if you map the same variable to multiple aesthetics?

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x =displ, y = hwy, color = class, shape = class))
```

    ## Warning: The shape palette can deal with a maximum of 6 discrete values because
    ## more than 6 becomes difficult to discriminate; you have 7. Consider
    ## specifying shapes manually if you must have them.

    ## Warning: Removed 62 rows containing missing values (geom_point).

![](Data-Visualization_files/figure-gfm/unnamed-chunk-18-1.png)<!-- -->

Both aesthetics are done to the same variable.

6.  What happens if you map an aesthetic to something other than a
    variable name, like aes(colour = displ \< 5)? Note, you’ll also need
    to specify x and y.

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x =displ, y = hwy, colour = displ < 5))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-19-1.png)<!-- -->
It makes a true vs false comparison.

### 3.5 Facets

``` r
ggplot(data = mpg) + geom_point(aes(x = displ, y = hwy)) + facet_wrap(~ class, nrow = 2)
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-20-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(aes(x = displ, y = hwy)) + facet_grid(drv ~ cyl)
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-21-1.png)<!-- -->

### 3.5.1 Exercises

1.What happens if you facet on a continuous variable?

``` r
ggplot(data = mpg) + geom_point(aes(x = displ, y = hwy)) + facet_wrap(~ cty, nrow = 2)
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-22-1.png)<!-- -->

It attempts to make the variable categorical.

2.  What do the empty cells in plot with facet\_grid(drv \~ cyl) mean?
    How do they relate to this plot?

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(aes(x = displ, y = hwy)) + facet_grid(drv ~ cyl)
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-23-1.png)<!-- -->
That means at that amount of cylinders there is no cars of those types
of drives

3.  What plots does the following code make? What does . do?

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) +facet_grid(drv ~ .)
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-24-1.png)<!-- -->
Ignores dimension.

4.  Take the first faceted plot in this section: What are the advantages
    to using faceting instead of the colour aesthetic? What are the
    disadvantages? How might the balance change if you had a larger
    dataset?

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) + facet_wrap(~ class, nrow = 2)
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-25-1.png)<!-- -->
\#It lets you analyze a specific variable’s data set better, but it also
doesn’t let you see the data compared to one another as well.

5.  Read ?facet\_wrap. What does nrow do? What does ncol do? What other
    options control the layout of the individual panels? Why doesn’t
    facet\_grid() have nrow and ncol arguments?

<!-- end list -->

``` r
?facet_wrap
?facet_grid
```

Nrow and ncol choose number of rows and columns. Facet-grid() doesn’t
have nrow and ncol because the variables choose the columns and rows.

6.  When using facet\_grid() you should usually put the variable with
    more unique levels in the columns. Why?

<!-- end list -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) + facet_grid(cyl ~ cty)
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-27-1.png)<!-- -->

Because there is more space.

### 3.6 Geometric Objects

``` r
ggplot(data = mpg) + geom_smooth(mapping = aes(x = displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-28-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_smooth(mapping = aes(x = displ, y = hwy, linetype = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-29-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_smooth(mapping = aes( x = displ, y = hwy, group = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-30-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_smooth(mapping = aes( x = displ, y = hwy, color = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-31-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy)) + geom_smooth(mapping = aes(x = displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-32-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, color = drv)) + geom_smooth(mapping = aes(x = displ, y = hwy, color = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-33-1.png)<!-- -->

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + geom_point() + geom_smooth()
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-34-1.png)<!-- -->

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + geom_smooth() + geom_point(mapping = aes(color = class))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-35-1.png)<!-- -->

### 3.6.1 Exercises

1.  What geom would you use to draw a line chart? A boxplot? A
    histogram? An area chart? Line chart:geom\_line()
    Boxplot:geom\_boxplot() Histogram: geom\_histogram() Area Chart:
    geom\_area()

<!-- end list -->

``` r
??geom
```

2.  Run this code in your head and predict what the output will look
    like. Then, run the code in R and check your predictions.

Graph that shows the displ compared to the hwy with drv disinguishing
showing line of best fit through each drive type.

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + 
  geom_point() + 
  geom_smooth(se = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-37-1.png)<!-- -->

3.  What does show.legend = FALSE do? What happens if you remove it? Why
    do you think I used it earlier in the chapter?

The legend wouldn’t show up.

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy, color = drv, show.legend = FALSE))
```

    ## Warning: Ignoring unknown aesthetics: show.legend

![](Data-Visualization_files/figure-gfm/unnamed-chunk-38-1.png)<!-- -->

4.  What does the se argument to geom\_smooth() do?

It removes the extra area that it could be from the smooth.

5.  Will these graphs look different? Why/why not?

<!-- end list -->

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point() + 
  geom_smooth()
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-39-1.png)<!-- -->

``` r
ggplot() + 
  geom_point(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_smooth(data = mpg, mapping = aes(x = displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](Data-Visualization_files/figure-gfm/unnamed-chunk-40-1.png)<!-- -->

No because the mappings and aesthetics are the same.

### 3.7 Statistical Transformations

``` r
?diamonds
```

``` r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-42-1.png)<!-- -->
\#\#\# 3.8 Position Adjustments

``` r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, color = cut))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-43-1.png)<!-- -->

``` r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = cut))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-44-1.png)<!-- -->

``` r
ggplot(data = diamonds) + geom_bar(mapping = aes(x = cut, fill = clarity))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-45-1.png)<!-- -->

``` r
ggplot(data = diamonds, mapping = aes(x = cut, fill = clarity)) + geom_bar(alpha = 0.2, position = "identity")
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-46-1.png)<!-- -->

``` r
ggplot(data = diamonds, mapping = aes(x = cut, color = clarity)) + geom_bar(fill = NA, position = "identity")
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-47-1.png)<!-- -->

``` r
ggplot(data = diamonds, mapping = aes(x = cut, fill = clarity)) + geom_bar(position = "fill")
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-48-1.png)<!-- -->

``` r
ggplot(data = diamonds, mapping = aes(x = cut, fill = clarity)) + geom_bar(position = "dodge")
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-49-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-50-1.png)<!-- -->

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = displ, y = hwy), position = "jitter")
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-51-1.png)<!-- -->

### 3.8.1 Exercises

Notebook check - exercises & notes

Project - start next week / due week after

1.  What is the problem with this plot? How could you improve it?

<!-- end list -->

``` r
ggplot(data = mpg, mapping = aes(x = cty, y = hwy)) + geom_point()
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-52-1.png)<!-- -->
Ans: The problem with this plot is you can’t see all the points, you
could improve it by using jitter.

2.  What parameters to geom\_jitter() control the amount of jittering?

Ans: The amount of width and height to the jitter control the jittering.

3.  Compare and contrast geom\_jitter() with geom\_count().

<!-- end list -->

``` r
ggplot(data = mpg, mapping = aes(x = cty, y = hwy)) + geom_jitter()
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-53-1.png)<!-- -->

``` r
ggplot(data = mpg, mapping = aes(x = cty, y = hwy)) + geom_count()
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-54-1.png)<!-- -->

Ans: Both graphs are very cluttery, but geom\_count shows the amount of
points using size and geom\_jitter tries to show all the points.

4.  What’s the default position adjustment for geom\_boxplot()? Create a
    visualisation of the mpg dataset that demonstrates it.

<!-- end list -->

``` r
ggplot(data = mpg) + geom_boxplot(mapping = aes(x = class, y = hwy))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-55-1.png)<!-- -->

``` r
?geom_boxplot
```

``` r
ggplot(data = mpg) + geom_point(mapping = aes(x = class, y = hwy))
```

![](Data-Visualization_files/figure-gfm/unnamed-chunk-56-1.png)<!-- -->

Ans: It accompanies as many points as it can within a certain range.
