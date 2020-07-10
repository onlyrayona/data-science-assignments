Code Style
================
Zachary del Rosario
2020-05-05

*Purpose*: From the tidyverse style guide “Good coding style is like
correct punctuation: you can manage without it,
butitsuremakesthingseasiertoread.” We will follow the [tidyverse style
guide](https://style.tidyverse.org/); Google’s internal [R style
guide](https://google.github.io/styleguide/Rguide.html) is actually
based on these guidelines\!

*Reading*: [tidyverse style guide](https://style.tidyverse.org/).
*Topics*: [Spacing](https://style.tidyverse.org/syntax.html#spacing)
(subsection only), [Pipes](https://style.tidyverse.org/pipes.html)
(whole section) *Reading Time*: \~ 10 minutes

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────── tidyverse 1.3.0 ──

    ## ✓ ggplot2 3.3.2     ✓ purrr   0.3.4
    ## ✓ tibble  3.0.2     ✓ dplyr   1.0.0
    ## ✓ tidyr   1.1.0     ✓ stringr 1.4.0
    ## ✓ readr   1.3.1     ✓ forcats 0.5.0

    ## ── Conflicts ────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

**q1** Re-write according to the style guide

*Hint*: The pipe operator `%>%` will help make this code more readable.

``` r
## Original code; hard to read
summarize(group_by(diamonds, cut), mean_price = mean(price))
```

    ## `summarise()` ungrouping output (override with `.groups` argument)

    ## # A tibble: 5 x 2
    ##   cut       mean_price
    ##   <ord>          <dbl>
    ## 1 Fair           4359.
    ## 2 Good           3929.
    ## 3 Very Good      3982.
    ## 4 Premium        4584.
    ## 5 Ideal          3458.

``` r
summarize(
  group_by(diamonds, cut), 
  mean_price = mean(price)
  )
```

    ## `summarise()` ungrouping output (override with `.groups` argument)

    ## # A tibble: 5 x 2
    ##   cut       mean_price
    ##   <ord>          <dbl>
    ## 1 Fair           4359.
    ## 2 Good           3929.
    ## 3 Very Good      3982.
    ## 4 Premium        4584.
    ## 5 Ideal          3458.

**q2** Re-write according to the style guide

*Hint*: There are *particular rules* about spacing\!

``` r
## NOTE: You can copy this code to the chunk below
iris %>%
  mutate(Sepal.Area=Sepal.Length*Sepal.Width) %>%
  group_by( Species ) %>%
  summarize_if(is.numeric,mean)%>%
  ungroup() %>%
  pivot_longer( names_to="measure",values_to="value",cols=-Species ) %>%
  arrange(value )
```

    ## # A tibble: 15 x 3
    ##    Species    measure       value
    ##    <fct>      <chr>         <dbl>
    ##  1 setosa     Petal.Width   0.246
    ##  2 versicolor Petal.Width   1.33 
    ##  3 setosa     Petal.Length  1.46 
    ##  4 virginica  Petal.Width   2.03 
    ##  5 versicolor Sepal.Width   2.77 
    ##  6 virginica  Sepal.Width   2.97 
    ##  7 setosa     Sepal.Width   3.43 
    ##  8 versicolor Petal.Length  4.26 
    ##  9 setosa     Sepal.Length  5.01 
    ## 10 virginica  Petal.Length  5.55 
    ## 11 versicolor Sepal.Length  5.94 
    ## 12 virginica  Sepal.Length  6.59 
    ## 13 versicolor Sepal.Area   16.5  
    ## 14 setosa     Sepal.Area   17.3  
    ## 15 virginica  Sepal.Area   19.7

``` r
iris %>%
  mutate(Sepal.Area=Sepal.Length*Sepal.Width) %>%
  group_by( Species ) %>%
  summarize_if(is.numeric,mean) %>%
  ungroup() %>%
  pivot_longer(    
    names_to="measure",
    values_to="value",
    cols=-Species ) %>%
  arrange(value )
```

    ## # A tibble: 15 x 3
    ##    Species    measure       value
    ##    <fct>      <chr>         <dbl>
    ##  1 setosa     Petal.Width   0.246
    ##  2 versicolor Petal.Width   1.33 
    ##  3 setosa     Petal.Length  1.46 
    ##  4 virginica  Petal.Width   2.03 
    ##  5 versicolor Sepal.Width   2.77 
    ##  6 virginica  Sepal.Width   2.97 
    ##  7 setosa     Sepal.Width   3.43 
    ##  8 versicolor Petal.Length  4.26 
    ##  9 setosa     Sepal.Length  5.01 
    ## 10 virginica  Petal.Length  5.55 
    ## 11 versicolor Sepal.Length  5.94 
    ## 12 virginica  Sepal.Length  6.59 
    ## 13 versicolor Sepal.Area   16.5  
    ## 14 setosa     Sepal.Area   17.3  
    ## 15 virginica  Sepal.Area   19.7

**q3** Re-write according to the style guide

*Hint*: What do we do about long lines?

``` r
iris %>%
  group_by(Species) %>%
  summarize(Sepal.Length = mean(Sepal.Length), Sepal.Width = mean(Sepal.Width), Petal.Length = mean(Petal.Length), Petal.Width = mean(Petal.Width))
```

    ## `summarise()` ungrouping output (override with `.groups` argument)

    ## # A tibble: 3 x 5
    ##   Species    Sepal.Length Sepal.Width Petal.Length Petal.Width
    ##   <fct>             <dbl>       <dbl>        <dbl>       <dbl>
    ## 1 setosa             5.01        3.43         1.46       0.246
    ## 2 versicolor         5.94        2.77         4.26       1.33 
    ## 3 virginica          6.59        2.97         5.55       2.03

``` r
iris %>%
  group_by(Species) %>%
  summarize(
            Sepal.Length = mean(Sepal.Length), 
            Sepal.Width = mean(Sepal.Width), 
            Petal.Length = mean(Petal.Length), 
            Petal.Width = mean(Petal.Width)
            )
```

    ## `summarise()` ungrouping output (override with `.groups` argument)

    ## # A tibble: 3 x 5
    ##   Species    Sepal.Length Sepal.Width Petal.Length Petal.Width
    ##   <fct>             <dbl>       <dbl>        <dbl>       <dbl>
    ## 1 setosa             5.01        3.43         1.46       0.246
    ## 2 versicolor         5.94        2.77         4.26       1.33 
    ## 3 virginica          6.59        2.97         5.55       2.03

<!-- include-exit-ticket -->

# Exit Ticket

<!-- -------------------------------------------------- -->

Once you have completed this exercise, make sure to fill out the **exit
ticket survey**, [linked
here](https://docs.google.com/forms/d/e/1FAIpQLSeuq2LFIwWcm05e8-JU84A3irdEL7JkXhMq5Xtoalib36LFHw/viewform?usp=pp_url&entry.693978880=e-code-target).
