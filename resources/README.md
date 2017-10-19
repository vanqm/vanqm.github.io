# Python Language
## Ref: [http://tomaugspurger.github.io](http://tomaugspurger.github.io)

**Practical Pandas**
- [Practical Pandas Part 1 - Reading the Data](http://tomaugspurger.github.io/practical-pandas-part-1-reading-the-data.html)
- [Practical Pandas Part 2 - More Tidying, More Data, and Merging](http://tomaugspurger.github.io/practical-pandas-part-2-more-tidying-more-data-and-merging.html)
- [Practical Pandas Part 3 - Exploratory Data Analysis](http://tomaugspurger.github.io/practical-pandas-part-3-exploratory-data-analysis.html)

**Using Python to tackle the CPS**
- [Using Python to tackle the CPS](http://tomaugspurger.github.io/tackling%20the%20cps.html)
- [Using Python to tackle the CPS (Part 2)](http://tomaugspurger.github.io/tackling%20the%20cps%20(part%202).html)
- [Using Python to tackle the CPS (Part 3)](http://tomaugspurger.github.io/tackling%20the%20cps%20(part%203).html)
- [Using Python to tackle the CPS (Part 4)](http://tomaugspurger.github.io/tackling%20the%20cps%20(part%204).html)

## Pandas Official Documentation
- [Web Version](http://pandas.pydata.org/pandas-docs/stable/#)
- [PDF Version](http://pandas.pydata.org/pandas-docs/stable/pandas.pdf)
- [Zipped HTML](http://pandas.pydata.org/pandas-docs/stable/pandas.zip)


## Tidy Data in Action
- [Hadley Whickham](http://had.co.nz) wrote a famous paper (for a certain definition of famous) about the importance of [tidy data](http://vita.had.co.nz/papers/tidy-data.pdf) when doing data analysis.
- [Tidy Data](http://r4ds.had.co.nz/tidy-data.html): from http://r4ds.had.co.nz 
   - Spreading and gathering
   - Separating and uniting

## General Textbooks
- [Forecasting: Principles and Practice](https://www.otexts.org/fpp/2/5): A great introduction
- [Stock and Watson](http://wps.aw.com/aw_stock_ie_3/178/45691/11696965.cw/): Readable undergraduate resource, has a few chapters on time series
- [Greene's Econometric Analysis](http://pages.stern.nyu.edu/~wgreene/Text/econometricanalysis.htm): My favorite PhD level textbook
- [Hamilton's Time Series Analysis](https://www.amazon.com/Time-Analysis-James-Douglas-Hamilton/dp/0691042896): A classic
- [Lutkehpohl's New Introduction to Multiple Time Series Analysis](https://www.amazon.com/New-Introduction-Multiple-Time-Analysis/dp/3540262393): Extremely dry, but useful if you're implementing this stuff

# R Language
## R Performance
Ref: [Advanced R](http://adv-r.had.co.nz/Performance.html)

R is not a fast language. This is not an accident. R was purposely designed to make data analysis and statistics easier for you to do. It was not designed to make life easier for your computer. While R is slow compared to other programming languages, for most purposes, it’s fast enough.

The following four chapters will give you the skills to improve the speed of your code when you need to:
- In [Profiling](http://adv-r.had.co.nz/Profiling.html#profiling), you’ll learn how to systematically make your code faster. First you figure what’s slow, and then you apply some general techniques to make the slow parts faster.
- In [Memory](http://adv-r.had.co.nz/memory.html#memory), you’ll learn about how R uses memory, and how garbage collection and copy-on-modify affect performance and memory usage.
- For really high-performance code, you can move outside of R and use another programming language. [Rcpp](http://adv-r.had.co.nz/Rcpp.html#rcpp) will teach you the absolute minimum you need to know about C++ so you can write fast code using the Rcpp package.
- To really understand the performance of built-in base functions, you’ll need to learn a little bit about [R’s C API](http://adv-r.had.co.nz/C-interface.html#c-api). In R’s C interface, you’ll learn a little about R’s C internals.
