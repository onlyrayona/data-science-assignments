Documentation
================
2020-05-05

*Purpose*: No programmer memorizes every fact about every function.
Expert programmers get used to quickly reading *documentation*, which
allows them to look up the facts they need, when they need them. Just as
you had to learn how to read English, you will have to learn how to
consult documentation. This exercise will get you started.

*Reading*: (None)

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

The `vignette()` function allows us to look up
[vignettes](https://stat.ethz.ch/R-manual/R-devel/library/utils/html/vignette.html);
short narrative-form tutorials associated with a package, written by its
developers.

**q1** Use `vignette(package = ???)` (fill in the ???) to look up
vignettes associated with `"dplyr"`. What vignettes are available?

``` r
library(tidyverse)
vignette(package = "dplyr")
```

Answer:

Vignettes in package ‘dplyr’:

colwise colwise (source, html) compatibility dplyr compatibility
(source, html) base From base R to dplyr (source, html) grouping Grouped
data (source, html) dplyr Introduction to dplyr (source, html)
programming Programming with dplyr (source, html) rowwise rowwise
(source, html) two-table Two-table verbs (source, html) window-functions
Window functions (source, html)

Once we know *what* vignettes are available, we can use the same
function to read a particular vignette.

**q2** Use `vignette(???, package = "dplyr")` to read the vignette on
`dplyr`. Read this vignette up to the first note on `filter()`. Use
`filter()` to select only those rows of the `iris` dataset where
`Species == "setosa"`.

*Note*: This should open up your browser.

***I used browseVignettes instead because I couldn’t read the vignettes
otherwise***

``` r
iris %>%
  as_tibble() %>%
  filter(Species == "setosa")
```

    ## # A tibble: 50 x 5
    ##    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    ##           <dbl>       <dbl>        <dbl>       <dbl> <fct>  
    ##  1          5.1         3.5          1.4         0.2 setosa 
    ##  2          4.9         3            1.4         0.2 setosa 
    ##  3          4.7         3.2          1.3         0.2 setosa 
    ##  4          4.6         3.1          1.5         0.2 setosa 
    ##  5          5           3.6          1.4         0.2 setosa 
    ##  6          5.4         3.9          1.7         0.4 setosa 
    ##  7          4.6         3.4          1.4         0.3 setosa 
    ##  8          5           3.4          1.5         0.2 setosa 
    ##  9          4.4         2.9          1.4         0.2 setosa 
    ## 10          4.9         3.1          1.5         0.1 setosa 
    ## # … with 40 more rows

Vignettes are useful when we only know *generally* what we’re looking
for. Once we know the verbs (functions) we want to use, we need more
specific help.

**q3** Remember back to `e-setup02-functions`; how do we look up help
for a specific function?

Answer:

Put ‘?’ in front of the function, i.e. ?function

Sometimes we’ll be working with a function, but we won’t *quite* know
how to get it to do what we need. In this case, consulting the
function’s documentation can be *extremely* helpful.

**q4** Use your knowledge of documentation lookup to answer the
following question: How could we `filter` the `iris` dataset to return
only those rows with `Sepal.Length` between `5.1` and `6.4`?

``` r
iris %>%
  as_tibble() %>%
  filter(between(Sepal.Length, 5.1, 6.4))
```

    ## # A tibble: 83 x 5
    ##    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    ##           <dbl>       <dbl>        <dbl>       <dbl> <fct>  
    ##  1          5.1         3.5          1.4         0.2 setosa 
    ##  2          5.4         3.9          1.7         0.4 setosa 
    ##  3          5.4         3.7          1.5         0.2 setosa 
    ##  4          5.8         4            1.2         0.2 setosa 
    ##  5          5.7         4.4          1.5         0.4 setosa 
    ##  6          5.4         3.9          1.3         0.4 setosa 
    ##  7          5.1         3.5          1.4         0.3 setosa 
    ##  8          5.7         3.8          1.7         0.3 setosa 
    ##  9          5.1         3.8          1.5         0.3 setosa 
    ## 10          5.4         3.4          1.7         0.2 setosa 
    ## # … with 73 more rows

On other occasions we’ll know a function, but would like to know about
other, related functions. In this case, it’s useful to be able to trace
the `function` back to its parent `package`. Then we can read the
vignettes on the package to learn more.

**q5** Look up the documentation on `cut_number`; what package does it
come from? What about `parse_number()`? What about `row_number()`?

``` r
?row_number
```

Answer:

cut\_number comes from ggplot. parse\_number comes from readr
row\_number comes from dplyr

<!-- include-exit-ticket -->

# Exit Ticket

<!-- -------------------------------------------------- -->

Once you have completed this exercise, make sure to fill out the **exit
ticket survey**, [linked
here](https://docs.google.com/forms/d/e/1FAIpQLSeuq2LFIwWcm05e8-JU84A3irdEL7JkXhMq5Xtoalib36LFHw/viewform?usp=pp_url&entry.693978880=e-code-target).
