# Assignment 1 - Reproducible Research
PRO  
29 de octubre de 2016  




## Loading and preprocessing the data

1. Load the data (i.e. read.csv())

```r
fichero<- paste(dir, "activity.csv", sep="/")
file_o<- read.csv(fichero)
file<- file_o[!is.na(file_o$steps),]
```

2. Process/transform the data (if necessary) into a format suitable for your analysis


```r
file$date<-as.Date(file$date)
file_o$date<-as.Date(file_o$date)
```

## What is mean total number of steps taken per day?

1. Calculate the total number of steps taken per day


```r
stepday<-data.frame(aggregate(file$steps, list(file$date), sum))
colnames(stepday)<-c("Date", "Step")
```

2. If you do not understand the difference between a histogram and a barplot, research the difference between them. Make a histogram of the total number of steps taken each day


```r
hist(stepday$Step, freq=TRUE, breaks=53, xlab="Date",main="STEPS")
```

![](PA1_Template_files/figure-html/unnamed-chunk-4-1.png)<!-- -->

3. Calculate and report the mean and median of the total number of steps taken per day


```r
stepday_avg<-data.frame(aggregate(file$steps, list(file$date), mean))
colnames(stepday_avg)<- c("date", "steps")

stepday_med<-data.frame(aggregate(file$steps, list(file$date), median))
colnames(stepday_avg)<- c("date", "steps")

print(stepday_avg)
```

```
##          date      steps
## 1  2012-10-02  0.4375000
## 2  2012-10-03 39.4166667
## 3  2012-10-04 42.0694444
## 4  2012-10-05 46.1597222
## 5  2012-10-06 53.5416667
## 6  2012-10-07 38.2465278
## 7  2012-10-09 44.4826389
## 8  2012-10-10 34.3750000
## 9  2012-10-11 35.7777778
## 10 2012-10-12 60.3541667
## 11 2012-10-13 43.1458333
## 12 2012-10-14 52.4236111
## 13 2012-10-15 35.2048611
## 14 2012-10-16 52.3750000
## 15 2012-10-17 46.7083333
## 16 2012-10-18 34.9166667
## 17 2012-10-19 41.0729167
## 18 2012-10-20 36.0937500
## 19 2012-10-21 30.6284722
## 20 2012-10-22 46.7361111
## 21 2012-10-23 30.9652778
## 22 2012-10-24 29.0104167
## 23 2012-10-25  8.6527778
## 24 2012-10-26 23.5347222
## 25 2012-10-27 35.1354167
## 26 2012-10-28 39.7847222
## 27 2012-10-29 17.4236111
## 28 2012-10-30 34.0937500
## 29 2012-10-31 53.5208333
## 30 2012-11-02 36.8055556
## 31 2012-11-03 36.7048611
## 32 2012-11-05 36.2465278
## 33 2012-11-06 28.9375000
## 34 2012-11-07 44.7326389
## 35 2012-11-08 11.1770833
## 36 2012-11-11 43.7777778
## 37 2012-11-12 37.3784722
## 38 2012-11-13 25.4722222
## 39 2012-11-15  0.1423611
## 40 2012-11-16 18.8923611
## 41 2012-11-17 49.7881944
## 42 2012-11-18 52.4652778
## 43 2012-11-19 30.6979167
## 44 2012-11-20 15.5277778
## 45 2012-11-21 44.3993056
## 46 2012-11-22 70.9270833
## 47 2012-11-23 73.5902778
## 48 2012-11-24 50.2708333
## 49 2012-11-25 41.0902778
## 50 2012-11-26 38.7569444
## 51 2012-11-27 47.3819444
## 52 2012-11-28 35.3576389
## 53 2012-11-29 24.4687500
```

```r
print(stepday_med)
```

```
##       Group.1 x
## 1  2012-10-02 0
## 2  2012-10-03 0
## 3  2012-10-04 0
## 4  2012-10-05 0
## 5  2012-10-06 0
## 6  2012-10-07 0
## 7  2012-10-09 0
## 8  2012-10-10 0
## 9  2012-10-11 0
## 10 2012-10-12 0
## 11 2012-10-13 0
## 12 2012-10-14 0
## 13 2012-10-15 0
## 14 2012-10-16 0
## 15 2012-10-17 0
## 16 2012-10-18 0
## 17 2012-10-19 0
## 18 2012-10-20 0
## 19 2012-10-21 0
## 20 2012-10-22 0
## 21 2012-10-23 0
## 22 2012-10-24 0
## 23 2012-10-25 0
## 24 2012-10-26 0
## 25 2012-10-27 0
## 26 2012-10-28 0
## 27 2012-10-29 0
## 28 2012-10-30 0
## 29 2012-10-31 0
## 30 2012-11-02 0
## 31 2012-11-03 0
## 32 2012-11-05 0
## 33 2012-11-06 0
## 34 2012-11-07 0
## 35 2012-11-08 0
## 36 2012-11-11 0
## 37 2012-11-12 0
## 38 2012-11-13 0
## 39 2012-11-15 0
## 40 2012-11-16 0
## 41 2012-11-17 0
## 42 2012-11-18 0
## 43 2012-11-19 0
## 44 2012-11-20 0
## 45 2012-11-21 0
## 46 2012-11-22 0
## 47 2012-11-23 0
## 48 2012-11-24 0
## 49 2012-11-25 0
## 50 2012-11-26 0
## 51 2012-11-27 0
## 52 2012-11-28 0
## 53 2012-11-29 0
```


## What is the average daily activity pattern?

1. Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)


```r
intday<- data.frame(aggregate(file$steps,list(file$interval), mean))
colnames(intday)<-c("interval", "steps")

h <- ggplot(data=intday,aes(interval,steps))
h+geom_line(col="brown")+ggtitle("Average steps per interval")+xlab("interval")+ylab("Steps")
```

![](PA1_Template_files/figure-html/unnamed-chunk-6-1.png)<!-- -->

2.Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?


```r
intmax<- intday[intday$steps==max(intday$steps),2]
```

Max interval 206.1698113

## Imputing missing values


1. Calculate and report the total number of missing values in the dataset (i.e. the total number of rows with NAs)


```r
number_missing<-sum(is.na(file_o$steps))
```

Initial number of missing: 2304

2. Devise a strategy for filling in all of the missing values in the dataset. The strategy does not need to be sophisticated. For example, you could use the mean/median for that day, or the mean for that 5-minute interval, etc.


```r
nas <- is.na(file_o$steps)
file_o$steps[nas] <- intday[match(intday$interval, file_o$interval),2]

number_missing<-sum(is.na(file_o$steps))
```

Final number of missing: 0

3. Create a new dataset that is equal to the original dataset but with the missing data filled in.


```r
new_file <- file_o
number_missing<-sum(is.na(new_file$steps))
```

Number of missing: 0

4. Make a histogram of the total number of steps taken each day and Calculate and report the mean and median total number of steps taken per day. Do these values differ from the estimates from the first part of the assignment? What is the impact of imputing missing data on the estimates of the total daily number of steps?


```r
stepday_o<-data.frame(aggregate(file_o$steps, list(file_o$date), sum))
colnames(stepday_o)<-c("Date", "Step")
hist(stepday_o$Step, freq=TRUE, breaks=53, main="STEPS")
```

![](PA1_Template_files/figure-html/unnamed-chunk-11-1.png)<!-- -->

# Are there differences in activity patterns between weekdays and weekends?

1. Create a new factor variable in the dataset with two levels - "weekday" and "weekend" indicating whether a given date is a weekday or weekend day.


```r
weekdays1 <- c('lunes', 'martes', 'miercoles', 'jueves', 'viernes')

file_o$weekdate <- factor((weekdays(file_o$date) %in% weekdays1), 
                          levels=c(FALSE, TRUE), labels=c('weekend', 'weekday')) 
```

2. Make a panel plot containing a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all weekday days or weekend days (y-axis). See the README file in the GitHub repository to see an example of what this plot should look like using simulated data.


```r
ggplot(file_o, aes(interval, steps)) + 
  geom_line() + 
  facet_grid(weekdate~ .) +
  xlab("interval") + 
  ylab("average number of steps")
```

![](PA1_Template_files/figure-html/unnamed-chunk-13-1.png)<!-- -->



