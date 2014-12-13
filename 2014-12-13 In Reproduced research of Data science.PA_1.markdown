2014/12/13 In Reproduced research of Data science.PA_1
--------------------------
Function：<code>aggragete()</code> have many formats:
```r
    aggregate(x, by, FUN, ..., simplify = TRUE) #1
    aggregate(formula, data, FUN, ...,subset, na.action = na.omit) #2
```
The 2nd format will not change the column name other than the 1th: it will make a new dataframe to contain the subset dataset.
In the 2nd format the parameter`formula`is very complex and convenient, it could have the '~','+' as far as I know.
```r
   aggregate(steps~interval+day,filled_data,mean)
```
it will use the `mean()`function to subset the stepson in the dataframe `filled_data` and will based on the eache kind data of column `interval` and `day`.
Function : `ifelse(test, yes, no)` very simple to use:
`which is filled with elements selected from either yes or no depending on whether the element of test is TRUE or FALSE.`
```r
    filled_data$day <- ifelse(weekdays(filled_data$date)%in%c("Saturday","Sunday"),"weekend","weekday")
```
in this code, goal is to classify the datetime to two types `weekend`and `weekday`.
the symbol `%in%`is a simple format of `match()`the usage is:
    
    x %in% table,which returns a logical vector indicating if there is a match or not for its left operand.

Plot:In `ggplot2`
```r
    qplot(total_test$date,total_test$steps,geom="histogram",stat="identity")+
        labs(x="Date",y="Steps")
```
if the histogram is a 2-dimensional plot. must use the `stat="identity"`.
```r
    g <- ggplot(test_mean,aes(interval,steps))
    g+geom_line()+facet_wrap(~ day,ncol=1)
```
To plot the facet plot. The number of facets is dependent on the types of `day`in `test_mean`
the plot is here:
![此处输入图片的描述][1]


  [1]: https://raw.githubusercontent.com/yukeitsao/RepData_PeerAssessment1/master/figure/unnamed-chunk-10-1.png