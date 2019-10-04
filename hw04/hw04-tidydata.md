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

Now let's return the data back to the format found in the gapminder dataset, where observations are listed for each country and arranged by country followed by year.

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["country"],"name":[1],"type":["chr"],"align":["left"]},{"label":["year"],"name":[2],"type":["int"],"align":["right"]},{"label":["lifeExp"],"name":[3],"type":["dbl"],"align":["right"]}],"data":[{"1":"Poland","2":"1952","3":"61.3"},{"1":"Poland","2":"1957","3":"65.8"},{"1":"Poland","2":"1962","3":"67.6"},{"1":"Poland","2":"1967","3":"69.6"},{"1":"Poland","2":"1972","3":"70.8"},{"1":"Poland","2":"1977","3":"70.7"},{"1":"Poland","2":"1982","3":"71.3"},{"1":"Poland","2":"1987","3":"71.0"},{"1":"Poland","2":"1992","3":"71.0"},{"1":"Poland","2":"1997","3":"72.8"},{"1":"Poland","2":"2002","3":"74.7"},{"1":"Poland","2":"2007","3":"75.6"},{"1":"Switzerland","2":"1952","3":"69.6"},{"1":"Switzerland","2":"1957","3":"70.6"},{"1":"Switzerland","2":"1962","3":"71.3"},{"1":"Switzerland","2":"1967","3":"72.8"},{"1":"Switzerland","2":"1972","3":"73.8"},{"1":"Switzerland","2":"1977","3":"75.4"},{"1":"Switzerland","2":"1982","3":"76.2"},{"1":"Switzerland","2":"1987","3":"77.4"},{"1":"Switzerland","2":"1992","3":"78.0"},{"1":"Switzerland","2":"1997","3":"79.4"},{"1":"Switzerland","2":"2002","3":"80.6"},{"1":"Switzerland","2":"2007","3":"81.7"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>
</div>


# Exercise 2 - Multivariate Option 1

After reviewing the life expectancy of Poland and Switzerland for each year, let's see how the GDP per capita changes with life expectancy. Note that in the table below, the values have been rounded and are given in the unit "years" for life expectancy or "dollars" for GDP per capita.

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["year"],"name":[1],"type":["int"],"align":["right"]},{"label":["lifeExp_Poland"],"name":[2],"type":["dbl"],"align":["right"]},{"label":["gdpPercap_Poland"],"name":[3],"type":["dbl"],"align":["right"]},{"label":["lifeExp_Switzerland"],"name":[4],"type":["dbl"],"align":["right"]},{"label":["gdpPercap_Switzerland"],"name":[5],"type":["dbl"],"align":["right"]}],"data":[{"1":"1952","2":"61.3","3":"4029.33","4":"69.6","5":"14734.23"},{"1":"1957","2":"65.8","3":"4734.25","4":"70.6","5":"17909.49"},{"1":"1962","2":"67.6","3":"5338.75","4":"71.3","5":"20431.09"},{"1":"1967","2":"69.6","3":"6557.15","4":"72.8","5":"22966.14"},{"1":"1972","2":"70.8","3":"8006.51","4":"73.8","5":"27195.11"},{"1":"1977","2":"70.7","3":"9508.14","4":"75.4","5":"26982.29"},{"1":"1982","2":"71.3","3":"8451.53","4":"76.2","5":"28397.72"},{"1":"1987","2":"71.0","3":"9082.35","4":"77.4","5":"30281.70"},{"1":"1992","2":"71.0","3":"7738.88","4":"78.0","5":"31871.53"},{"1":"1997","2":"72.8","3":"10159.58","4":"79.4","5":"32135.32"},{"1":"2002","2":"74.7","3":"12002.24","4":"80.6","5":"34480.96"},{"1":"2007","2":"75.6","3":"15389.92","4":"81.7","5":"37506.42"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>
</div>

Now that we've seen how GDP per capita compares to life expectancy for both Poland and Switzerland, let's return the data back to the format found in the gapminder dataset, where observations are listed for each country and arranged by country followed by year.

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["country"],"name":[1],"type":["chr"],"align":["left"]},{"label":["year"],"name":[2],"type":["int"],"align":["right"]},{"label":["lifeExp"],"name":[3],"type":["dbl"],"align":["right"]},{"label":["gdpPercap"],"name":[4],"type":["dbl"],"align":["right"]}],"data":[{"1":"Poland","2":"1952","3":"61.3","4":"4029.33"},{"1":"Poland","2":"1957","3":"65.8","4":"4734.25"},{"1":"Poland","2":"1962","3":"67.6","4":"5338.75"},{"1":"Poland","2":"1967","3":"69.6","4":"6557.15"},{"1":"Poland","2":"1972","3":"70.8","4":"8006.51"},{"1":"Poland","2":"1977","3":"70.7","4":"9508.14"},{"1":"Poland","2":"1982","3":"71.3","4":"8451.53"},{"1":"Poland","2":"1987","3":"71.0","4":"9082.35"},{"1":"Poland","2":"1992","3":"71.0","4":"7738.88"},{"1":"Poland","2":"1997","3":"72.8","4":"10159.58"},{"1":"Poland","2":"2002","3":"74.7","4":"12002.24"},{"1":"Poland","2":"2007","3":"75.6","4":"15389.92"},{"1":"Switzerland","2":"1952","3":"69.6","4":"14734.23"},{"1":"Switzerland","2":"1957","3":"70.6","4":"17909.49"},{"1":"Switzerland","2":"1962","3":"71.3","4":"20431.09"},{"1":"Switzerland","2":"1967","3":"72.8","4":"22966.14"},{"1":"Switzerland","2":"1972","3":"73.8","4":"27195.11"},{"1":"Switzerland","2":"1977","3":"75.4","4":"26982.29"},{"1":"Switzerland","2":"1982","3":"76.2","4":"28397.72"},{"1":"Switzerland","2":"1987","3":"77.4","4":"30281.70"},{"1":"Switzerland","2":"1992","3":"78.0","4":"31871.53"},{"1":"Switzerland","2":"1997","3":"79.4","4":"32135.32"},{"1":"Switzerland","2":"2002","3":"80.6","4":"34480.96"},{"1":"Switzerland","2":"2007","3":"81.7","4":"37506.42"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>
</div>


#Exercise 3



