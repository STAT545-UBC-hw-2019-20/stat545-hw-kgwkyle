---
title: 'Assignment 4: Tidy Data'
author: "Kyle Wlodarczyk"
date: "October 4, 2019"
output: 
  html_document:
    keep_md: true
    df_print: paged
    toc: yes
    theme: cerulean
---



# Exercise 1 - Univariate Option 1

Let's take a look at the life expectancy of two countries, such as Poland and Switzerland, for each year. Note that in the table below, the values have been rounded and are given in the unit "years".

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["year"],"name":[1],"type":["int"],"align":["right"]},{"label":["Poland"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["Switzerland"],"name":[3],"type":["dbl"],"align":["right"]}],"data":[{"1":"1952","2":"61.3","3":"69.6"},{"1":"1957","2":"65.8","3":"70.6"},{"1":"1962","2":"67.6","3":"71.3"},{"1":"1967","2":"69.6","3":"72.8"},{"1":"1972","2":"70.8","3":"73.8"},{"1":"1977","2":"70.7","3":"75.4"},{"1":"1982","2":"71.3","3":"76.2"},{"1":"1987","2":"71.0","3":"77.4"},{"1":"1992","2":"71.0","3":"78.0"},{"1":"1997","2":"72.8","3":"79.4"},{"1":"2002","2":"74.7","3":"80.6"},{"1":"2007","2":"75.6","3":"81.7"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>
</div>

To get a better idea of how the life expectancies of the two countries are changing relative to each other, let's graph them against each other since visuals are powerful communication tools.

![](hw04-tidydata_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

We can see that the life expectancy in Poland stagnates between 1972 and 1992 while it continues to increase in Switzerland.

Now let's return the data back to the format found in the gapminder dataset, where observations are listed for each country and arranged by country.

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["country"],"name":[1],"type":["chr"],"align":["left"]},{"label":["year"],"name":[2],"type":["int"],"align":["right"]},{"label":["lifeExp"],"name":[3],"type":["dbl"],"align":["right"]}],"data":[{"1":"Poland","2":"1952","3":"61.3"},{"1":"Poland","2":"1957","3":"65.8"},{"1":"Poland","2":"1962","3":"67.6"},{"1":"Poland","2":"1967","3":"69.6"},{"1":"Poland","2":"1972","3":"70.8"},{"1":"Poland","2":"1977","3":"70.7"},{"1":"Poland","2":"1982","3":"71.3"},{"1":"Poland","2":"1987","3":"71.0"},{"1":"Poland","2":"1992","3":"71.0"},{"1":"Poland","2":"1997","3":"72.8"},{"1":"Poland","2":"2002","3":"74.7"},{"1":"Poland","2":"2007","3":"75.6"},{"1":"Switzerland","2":"1952","3":"69.6"},{"1":"Switzerland","2":"1957","3":"70.6"},{"1":"Switzerland","2":"1962","3":"71.3"},{"1":"Switzerland","2":"1967","3":"72.8"},{"1":"Switzerland","2":"1972","3":"73.8"},{"1":"Switzerland","2":"1977","3":"75.4"},{"1":"Switzerland","2":"1982","3":"76.2"},{"1":"Switzerland","2":"1987","3":"77.4"},{"1":"Switzerland","2":"1992","3":"78.0"},{"1":"Switzerland","2":"1997","3":"79.4"},{"1":"Switzerland","2":"2002","3":"80.6"},{"1":"Switzerland","2":"2007","3":"81.7"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>
</div>


# Exercise 2



#Exercise 3



