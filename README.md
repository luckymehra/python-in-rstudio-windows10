
<!-- README.md is generated from README.Rmd. Please edit that file -->

# python-in-rstudio-windows10

<!-- badges: start -->
<!-- badges: end -->

I used Kristopher Overholt’s [awesome
guide](https://support.rstudio.com/hc/en-us/articles/360023654474-Installing-and-Configuring-Python-with-RStudio)
to configure Python in RStudio. However, there were some steps that I
had to tweak slightly to make it work on Windows 10 operating system.

I will only list the steps that I had to do differently. I used Anaconda
Prompt for installing `virtualenv` (step 1 and step 2).

### Step 3

Instead of `source python/bin/activate` use
`source python/Scripts/activate`. Also, enter
`source python/Scripts/activate` in the Terminal tab (next to the
Console) tab. I am using *Git Bash* as my RStudio Terminal.

### Step 5

Inside .Rprofile file, the content should be

    Sys.setenv(RETICULATE_PYTHON = "python/Scripts/python.exe")

Everything else should be same as described the guide from [RStudio
Support](https://support.rstudio.com/hc/en-us/articles/360023654474-Installing-and-Configuring-Python-with-RStudio)

### Test python run

``` python
import pandas as pd

d = {'col1': [1, 2], 'col2': [3, 4]}
df = pd.DataFrame(data=d)
df
#>    col1  col2
#> 0     1     3
#> 1     2     4
type(df)
#> <class 'pandas.core.frame.DataFrame'>
```

Access python dataframe in an R chunk

``` r
library(reticulate)
df_in_r <- py$df

df_in_r
#>   col1 col2
#> 1    1    3
#> 2    2    4

class(df_in_r)
#> [1] "data.frame"
```

``` r
sessionInfo()
#> R version 4.0.3 (2020-10-10)
#> Platform: x86_64-w64-mingw32/x64 (64-bit)
#> Running under: Windows 10 x64 (build 19042)
#> 
#> Matrix products: default
#> 
#> locale:
#> [1] LC_COLLATE=English_United States.1252 
#> [2] LC_CTYPE=English_United States.1252   
#> [3] LC_MONETARY=English_United States.1252
#> [4] LC_NUMERIC=C                          
#> [5] LC_TIME=English_United States.1252    
#> 
#> attached base packages:
#> [1] stats     graphics  grDevices utils     datasets  methods   base     
#> 
#> other attached packages:
#> [1] reticulate_1.18
#> 
#> loaded via a namespace (and not attached):
#>  [1] Rcpp_1.0.6        lattice_0.20-41   digest_0.6.27     grid_4.0.3       
#>  [5] jsonlite_1.7.2    magrittr_2.0.1    evaluate_0.14     rlang_0.4.10     
#>  [9] stringi_1.5.3     Matrix_1.2-18     rmarkdown_2.7.1   tools_4.0.3      
#> [13] stringr_1.4.0     xfun_0.21         yaml_2.2.1        compiler_4.0.3   
#> [17] htmltools_0.5.1.1 knitr_1.31
```
