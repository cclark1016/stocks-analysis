# stocks-analysis

# VBA Challenge Analysis

## Overview
The goal of this project is to refactor the code that was written for the initial VBA stock analysis and determine if the refactorization affected performance. 

## Results
### Changes
The most significant change made during refactorization was the alteration to the order loops were executed in. In the initial code the ticker was assigned in the first “for” loop. Then a nested “for” loop ran through all rows of data looking for matches to the ticker and adding values to the total volume when ticker matches were made. This process of going through every single row of data was repeated for each individual ticker. 

#### Orignal VBA Loops
![Original_VBA_Code](https://github.com/cclark1016/stocks-analysis/blob/master/VBA_Code_PNG/Original_VBA_Code.png) 


In the refactorization the “for” loop was changed so that it only went through the rows of stock data once. By using the “tickerIndex” variable to recognize which ticker each row was assigned to the refactored code assigned all values to their proper tickers as it went through each row. The tickerIndex was increased by 1 when a row with the final ticker was recognized, allowing the code to begin assigning the following values to the next ticker in the array. 

#### Refactored VBA Loops
![Refactored_VBA Code](https://github.com/cclark1016/stocks-analysis/blob/master/VBA_Code_PNG/Refactored_Code.png)

### Outcome
The refactored code saw a dramatic decrease in execution time, taking approximately ¼ the time to execute in comparison to the original code (.2968 seconds vs 1.0585 seconds). This is likely due to the reduction in the number of times the refactored code looped through all the ticker rows. 

#### Original 2018 Execution Time
![Original 2018 Time](https://github.com/cclark1016/stocks-analysis/blob/master/Resources_PNG/VBA%20All%20Stocks%202018%20Original.png)

#### Refactored 2018 Execution Time
![Refactored 2018 Time](https://github.com/cclark1016/stocks-analysis/blob/master/Resources_PNG/VBA%20All%20Stocks%202018%20Refactored.png)

## Conclusion
Refactoring code can increase the performance, reliability, and user friendliness of an application. This can be particularly important in data analysis when working with very large datasets that can take a long time to constantly run through. It can also be important to ensure new data added to an analysis will be properly executed upon, as it may not fit the original parameters defined. However refactoring can also be a lengthy process, especially when dealing with code that was not well documented or pieced together by a large number of individuals. In some cases, especially when working with smaller datasets or code that will not be consistently used, the performance increases gained by refactoring are not worth the effort needed to properly refactor. 


In this case of the refactored VBA Stock Analysis ran ~4x faster than the original Stock Analysis code. The relevance of this depends on how the analysis is to be used in the future. As more tickers are added the performance gap will become more noticeable, and if this analysis is run consistently the refactorization could be well worth the effort put into it. However with this increased performance we do see a decrease in the agility of the refactored code, as it relies on the tickers all being clustered together in their current order within the dataset. In the original code the name of a ticker is looked for in every row of data, so if the tickers were sorted differently (but still grouped together, as not to affect starting/ending price) the result would be the same. However the refactored code begins statically at the tickerIndex 0 and moves down the list of tickers assuming they’re grouped together alphabetically. If this alphabetical sorting changed the values and tickers could become misaligned the output would be representative of wrongly assigned data.    

