Fixed Report
================
Maddie Quistgaard
2017-06-23 17:00:00 CDT

Introduction
------------

This report contains my data analysis of a scan of a bullet. This data is stored in the file [bullet.csv](./bullet.csv). The data I analyze is one crosscut of a 3D bullet scan at the micrometer level. The red dotted line in the image below shows an example of a bullet crosscut like the one I analyze. To better understand this data, I looked at a plot of it.

![](striations.jpg)

Plot
----

This is my plot. On the *x*-axis, I put the "y" value in my data set. This "y" value is the horizontal position (on the red dotted line) in the image above. On the *y*-axis in my plot, I put the "resid" value in my data set. This "resid" value represents the depth of the striation marks in the bullet. Recall that these values are all measured in micrometers (*μ*m).

<!-- In the brackets below, delete `eval = FALSE` before clicking `knit` -->
``` r
library(ggplot2)
library(readr)
bullet <- read.csv("bullet.csv")
head(bullet)
```

    ##     x          y    value   fitted     resid        se abs_resid  chop
    ## 1 250   W*268.75 129.8557 130.8840 -1.028280 0.2117087  1.028280 FALSE
    ## 2 250 K*270.3125 129.6964 131.2163 -1.519923 0.2105806  1.519923 FALSE
    ## 3 250  C*271.875 129.6787 131.5481 -1.869381 0.2094567  1.869381 FALSE
    ## 4 250 S*273.4375 130.1637 131.8793 -1.715560 0.2083370  1.715560 FALSE
    ## 5 250      X*275 130.2345 132.2099 -1.975356 0.2072217  1.975356 FALSE
    ## 6 250 E*276.5625 130.6558 132.5399 -1.884099 0.2061106  1.884099 FALSE

``` r
ggplot(data = bullet) + 
  geom_point(aes(x = y, y = resid, colour = resid))
```

<img src="2017-06-23-Quistgaard_files/figure-markdown_github/myPlot-1.png" style="display: block; margin: auto;" />

Summarizing my data
-------------------

That was a very pretty plot! Let's look at a summary of the data:

``` r
summary(bullet)
```

    ##        x                 y            value           fitted     
    ##  Min.   :250   A*1035.9375:   1   Min.   :101.8   Min.   :100.4  
    ##  1st Qu.:250   A*1056.25  :   1   1st Qu.:162.6   1st Qu.:165.1  
    ##  Median :250   A*1062.5   :   1   Median :200.0   Median :199.0  
    ##  Mean   :250   A*1067.1875:   1   Mean   :189.4   Mean   :189.5  
    ##  3rd Qu.:250   A*1120.3125:   1   3rd Qu.:219.2   3rd Qu.:219.9  
    ##  Max.   :250   A*1168.75  :   1   Max.   :227.8   Max.   :226.7  
    ##                (Other)    :1205                                  
    ##      resid               se            abs_resid           chop        
    ##  Min.   :-4.9316   Min.   :0.08894   Min.   :0.002286   Mode :logical  
    ##  1st Qu.:-1.3100   1st Qu.:0.09478   1st Qu.:0.599842   FALSE:1211     
    ##  Median :-0.4584   Median :0.09862   Median :1.150184                  
    ##  Mean   :-0.1228   Mean   :0.10685   Mean   :1.403250                  
    ##  3rd Qu.: 0.7444   3rd Qu.:0.10261   3rd Qu.:1.922578                  
    ##  Max.   : 6.6068   Max.   :0.21171   Max.   :6.606805                  
    ## 

One more plot
-------------

Finally, I look for outliers in the data. Outliers are typically defined as values greater than two standard deviations above the mean, and as values less than two standard deviations below the mean.

<!-- In the brackets below, delete `eval = FALSE` before clicking `knit` -->
``` r
library(tidyr)
myLines <- data.frame(meanValue = mean(bullet$resid), 
           OutliersAtLeft = mean(bullet$resid) - 2*sd(bullet$resid),
           OutliersAtRight = mean(bullet$resid) + 2*sd(bullet$resid))
myLines <- myLines %>% gather(id, value)
ggplot() + 
  geom_histogram(data = bullet, aes(x = resid), binwidth = .25) + 
  geom_vline(data = myLines, aes(xintercept = value), color = 'red') +
  geom_label(data = myLines, aes(x = value, y = 100, label = id)) +
  ggtitle("Histogram of the height of the striation marks", 
          subtitle = "Outliers lie outside of the redlines")
```

<img src="2017-06-23-Quistgaard_files/figure-markdown_github/myPlot2-1.png" style="display: block; margin: auto;" />

This was a great learning experience about bullets!
