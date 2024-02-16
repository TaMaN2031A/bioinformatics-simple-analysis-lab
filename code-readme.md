Lab one
================
Abdullah Taman
2024-02-15

# Lab One

Abdullah Mohamed Abdullah Taman 20010906

## Part Zero

------------------------------------------------------------------------

``` r
num <- numeric(5)
intgr <- 5L
ch <- 'c'
cmplx <- 2 + 2i
print(typeof(num))
```

    ## [1] "double"

``` r
print(typeof(intgr))
```

    ## [1] "integer"

``` r
print(typeof(ch))
```

    ## [1] "character"

``` r
print(typeof(cmplx))
```

    ## [1] "complex"

Now we’ll perform the while loop.

``` r
i <- 10L
while( i > 0){
  i <- i-1
  print(i)
}
```

    ## [1] 9
    ## [1] 8
    ## [1] 7
    ## [1] 6
    ## [1] 5
    ## [1] 4
    ## [1] 3
    ## [1] 2
    ## [1] 1
    ## [1] 0

Now we’ll create the if condition to check whether a number is even or
odd

``` r
n <- 5
if(n %% 2){
  print('odd')
}else {
  print('even')
}
```

    ## [1] "odd"

``` r
n <- 6
if(n %% 2){
  print('odd')
}else {
  print('even')
}
```

    ## [1] "even"

Now create a vector and iterate over it using a for loop

``` r
m <- c(1:10)
for(i in 0 : 10){
  print(m[i])
}
```

    ## integer(0)
    ## [1] 1
    ## [1] 2
    ## [1] 3
    ## [1] 4
    ## [1] 5
    ## [1] 6
    ## [1] 7
    ## [1] 8
    ## [1] 9
    ## [1] 10

We can see it’s an open range, it stops before the last number. Now
create a 4d array in r.

``` r
array_4d <- array(rnorm(16), dim=c(2,2,2,2))
print(array_4d)
```

    ## , , 1, 1
    ## 
    ##            [,1]       [,2]
    ## [1,] -0.9362186  0.4317767
    ## [2,] -0.9420861 -0.4829257
    ## 
    ## , , 2, 1
    ## 
    ##            [,1]       [,2]
    ## [1,] -0.5121397 -0.2190220
    ## [2,]  0.1684359  0.1860094
    ## 
    ## , , 1, 2
    ## 
    ##           [,1]       [,2]
    ## [1,] 0.7842222 -1.1730696
    ## [2,] 2.5996063  0.6658585
    ## 
    ## , , 2, 2
    ## 
    ##            [,1]       [,2]
    ## [1,]  0.5425542 -0.3702114
    ## [2,] -1.0211079  0.4190784

Now we’ll load the iris data set into a frame and do the requested
operations

``` r
library(datasets)
data(iris)
d <- iris
print(nrow(d))
```

    ## [1] 150

``` r
print(ncol(d))
```

    ## [1] 5

``` r
print(colnames(d))
```

    ## [1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width"  "Species"

``` r
print(nrow(subset(d, (Petal.Length > 1.5) & (Species == "setosa"))))
```

    ## [1] 13

## Part One

### Dependencies And Dataset Loading

Now we’ll install tidyverse package

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.4.4     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

Now after download brain cancer table, we’ll read it in r, print the
number of rows, columns, and columns names.

``` r
cancer <- read.csv("J:/champions work/datasets/Brain_GSE50161.csv")
```

This takes a lot of time. Now we’ll print the requested characteristics
of cancer data.

``` r
print(nrow(cancer))
```

    ## [1] 130

``` r
print(ncol(cancer))
```

    ## [1] 54677

``` r
print(head(colnames(cancer), 20))
```

    ##  [1] "samples"       "type"          "X1007_s_at"    "X1053_at"     
    ##  [5] "X117_at"       "X121_at"       "X1255_g_at"    "X1294_at"     
    ##  [9] "X1316_at"      "X1320_at"      "X1405_i_at"    "X1431_at"     
    ## [13] "X1438_at"      "X1487_at"      "X1494_f_at"    "X1552256_a_at"
    ## [17] "X1552257_a_at" "X1552258_at"   "X1552261_at"   "X1552263_at"

## Part Two

### Determining the Working Set

Now we’ll create a subset table of the required table, with the first 5
columns and the last 4 columns, right now I’m using excel along with r
because r is handeling a really big dataset and I want to get a taste of
the data

``` r
cancer2 <- subset(cancer, select=c(1:5, (ncol(cancer)-3):ncol(cancer)))
head(cancer2)
```

    ##   samples       type X1007_s_at X1053_at   X117_at AFFX.ThrX.M_at
    ## 1     834 ependymoma   12.49815 7.604868  6.880934       4.047380
    ## 2     835 ependymoma   13.06744 7.998090  7.209076       3.786437
    ## 3     836 ependymoma   13.06818 8.573674  8.647684       4.005343
    ## 4     837 ependymoma   12.45604 9.098977  6.628784       3.892318
    ## 5     838 ependymoma   12.69996 8.800721 11.556188       3.796856
    ## 6     839 ependymoma   12.46109 7.676462  7.244519       3.887500
    ##   AFFX.TrpnX.3_at AFFX.TrpnX.5_at AFFX.TrpnX.M_at
    ## 1        3.721936        4.516434        4.749940
    ## 2        3.564481        4.430891        4.491416
    ## 3        3.595382        4.563494        4.668827
    ## 4        3.759429        4.748381        4.521275
    ## 5        3.577544        4.504385        4.541450
    ## 6        3.596379        4.518055        4.526295

I need to check the operation was successful, I’ll print the number of
rows in cancer2

``` r
print(nrow(cancer2))
```

    ## [1] 130

Now I’ll create a table of types data

``` r
typ = table(cancer2$type)
most_occ = which.max(typ)
print(most_occ)
```

    ## ependymoma 
    ##          1

It’s ependymoma.

### Data Cleaning and Filtering

Now we’ll count the number of the NA’s from the cancer2 dataframe.

``` r
na <- apply(cancer2, 2, function(x) sum(is.na(x)))
print(na)
```

    ##         samples            type      X1007_s_at        X1053_at         X117_at 
    ##               0               0               0               0               0 
    ##  AFFX.ThrX.M_at AFFX.TrpnX.3_at AFFX.TrpnX.5_at AFFX.TrpnX.M_at 
    ##               0               0               0               0

It’s zero in all attributes, which gives us and indication that the data
is clean. Now we’ll filter the rows which have first gene X1007_s_at is
greater than 12.0

``` r
filt = subset(cancer2, (X1007_s_at > 12))
print(paste(nrow(filt), nrow(cancer2)))
```

    ## [1] "91 130"

They are 91 rows, the other are 130.

### Data Analysis

Now we’ll calculate standard deviation and mean of the genes in the
cancer2 dataframe

``` r
mean_and_standard_deviation <- apply(cancer2[, c('X1007_s_at', 'X1053_at', 'X117_at', 'AFFX.ThrX.M_at','AFFX.TrpnX.3_at','AFFX.TrpnX.5_at','AFFX.TrpnX.M_at')], 2, function(x) c(mean(x), sd(x)))
print(mean_and_standard_deviation)
```

    ##      X1007_s_at  X1053_at  X117_at AFFX.ThrX.M_at AFFX.TrpnX.3_at
    ## [1,] 12.2763929 8.7695830 7.722634      3.9167947        3.701539
    ## [2,]  0.7901601 0.6733962 1.037339      0.1659169        0.180251
    ##      AFFX.TrpnX.5_at AFFX.TrpnX.M_at
    ## [1,]       4.6279120       4.6333770
    ## [2,]       0.1606634       0.1923529

Now we’ll do the second part by using the aggregate function

``` r
mean_and_sd_to_each_type <- aggregate(cancer2[, c('X1007_s_at', 'X1053_at', 'X117_at', 'AFFX.ThrX.M_at','AFFX.TrpnX.3_at','AFFX.TrpnX.5_at','AFFX.TrpnX.M_at')], by=list(cancer2$type), FUN = function(x) c(mean(x), sd(x)) )
colnames(mean_and_sd_to_each_type) <- c('type', 'X1007_s_at', 'X1053_at', 'X117_at', 'AFFX.ThrX.M_at','AFFX.TrpnX.3_at','AFFX.TrpnX.5_at','AFFX.TrpnX.M_at')
write.csv(mean_and_sd_to_each_type, file="j:/result.csv", row.names=FALSE)
```

Here is the picture of the file

``` r
knitr::include_graphics("C:\\Users\\20106\\Pictures\\Screenshots\\Screenshot 2024-02-16 092011.png") 
```

    ## Warning in
    ## knitr::include_graphics("C:\\Users\\20106\\Pictures\\Screenshots\\Screenshot
    ## 2024-02-16 092011.png"): It is highly recommended to use relative paths for
    ## images. You had absolute paths: "C:\Users\20106\Pictures\Screenshots\Screenshot
    ## 2024-02-16 092011.png"

![](C:\Users\20106\Pictures\Screenshots\Screenshot%202024-02-16%20092011.png)<!-- -->

Now we’ll create the last frame required

``` r
final <- cancer2 %>%
  select(samples, type, X1007_s_at) %>%
  mutate(mean_of_cancer_type = ave(X1007_s_at, type, FUN=mean))
print(final)
```

    ##     samples                  type X1007_s_at mean_of_cancer_type
    ## 1       834            ependymoma   12.49815            12.75799
    ## 2       835            ependymoma   13.06744            12.75799
    ## 3       836            ependymoma   13.06818            12.75799
    ## 4       837            ependymoma   12.45604            12.75799
    ## 5       838            ependymoma   12.69996            12.75799
    ## 6       839            ependymoma   12.46109            12.75799
    ## 7       840            ependymoma   13.65564            12.75799
    ## 8       841            ependymoma   12.60137            12.75799
    ## 9       842            ependymoma   12.46323            12.75799
    ## 10      843            ependymoma   12.26571            12.75799
    ## 11      844            ependymoma   12.92103            12.75799
    ## 12      845            ependymoma   12.78655            12.75799
    ## 13      846            ependymoma   12.54533            12.75799
    ## 14      847            ependymoma   12.58752            12.75799
    ## 15      848            ependymoma   13.23495            12.75799
    ## 16      849            ependymoma   12.69891            12.75799
    ## 17      850            ependymoma   13.52952            12.75799
    ## 18      851            ependymoma   13.26825            12.75799
    ## 19      852            ependymoma   12.88427            12.75799
    ## 20      853            ependymoma   13.14187            12.75799
    ## 21      854            ependymoma   13.12623            12.75799
    ## 22      855            ependymoma   12.87771            12.75799
    ## 23      856            ependymoma   13.30534            12.75799
    ## 24      857            ependymoma   13.01007            12.75799
    ## 25      858            ependymoma   12.88582            12.75799
    ## 26      859            ependymoma   12.68075            12.75799
    ## 27      860            ependymoma   12.96515            12.75799
    ## 28      861            ependymoma   12.95582            12.75799
    ## 29      862            ependymoma   12.90768            12.75799
    ## 30      863            ependymoma   12.36983            12.75799
    ## 31      864            ependymoma   12.52924            12.75799
    ## 32      865            ependymoma   12.93000            12.75799
    ## 33      866            ependymoma   12.16255            12.75799
    ## 34      867            ependymoma   12.32100            12.75799
    ## 35      868            ependymoma   12.89403            12.75799
    ## 36      869            ependymoma   12.50689            12.75799
    ## 37      870            ependymoma   11.94630            12.75799
    ## 38      871            ependymoma   12.47752            12.75799
    ## 39      872            ependymoma   12.69406            12.75799
    ## 40      873            ependymoma   12.41619            12.75799
    ## 41      874            ependymoma   12.77586            12.75799
    ## 42      875            ependymoma   12.25728            12.75799
    ## 43      876            ependymoma   12.70864            12.75799
    ## 44      877            ependymoma   13.03961            12.75799
    ## 45      878            ependymoma   12.64576            12.75799
    ## 46      879            ependymoma   12.64335            12.75799
    ## 47      880          glioblastoma   11.36747            12.41685
    ## 48      881          glioblastoma   12.11184            12.41685
    ## 49      882          glioblastoma   12.68623            12.41685
    ## 50      883          glioblastoma   12.95673            12.41685
    ## 51      884          glioblastoma   12.13290            12.41685
    ## 52      885          glioblastoma   12.18032            12.41685
    ## 53      886          glioblastoma   13.08376            12.41685
    ## 54      887          glioblastoma   12.51533            12.41685
    ## 55      888          glioblastoma   12.78854            12.41685
    ## 56      889          glioblastoma   12.53021            12.41685
    ## 57      890          glioblastoma   13.06000            12.41685
    ## 58      891          glioblastoma   12.42215            12.41685
    ## 59      892          glioblastoma   12.24966            12.41685
    ## 60      893          glioblastoma   12.61178            12.41685
    ## 61      894          glioblastoma   12.11100            12.41685
    ## 62      895          glioblastoma   12.68002            12.41685
    ## 63      896          glioblastoma   11.66494            12.41685
    ## 64      897          glioblastoma   11.47724            12.41685
    ## 65      898          glioblastoma   12.28389            12.41685
    ## 66      899          glioblastoma   11.88057            12.41685
    ## 67      900          glioblastoma   12.46182            12.41685
    ## 68      901          glioblastoma   12.86800            12.41685
    ## 69      902          glioblastoma   11.92588            12.41685
    ## 70      903          glioblastoma   13.29125            12.41685
    ## 71      904          glioblastoma   12.38154            12.41685
    ## 72      905          glioblastoma   12.88070            12.41685
    ## 73      906          glioblastoma   12.90131            12.41685
    ## 74      907          glioblastoma   12.54613            12.41685
    ## 75      908          glioblastoma   11.63263            12.41685
    ## 76      909          glioblastoma   12.45702            12.41685
    ## 77      910          glioblastoma   11.78521            12.41685
    ## 78      911          glioblastoma   12.65480            12.41685
    ## 79      912          glioblastoma   12.76600            12.41685
    ## 80      913          glioblastoma   12.82618            12.41685
    ## 81      914       medulloblastoma   10.15621            11.18692
    ## 82      915       medulloblastoma   11.22875            11.18692
    ## 83      916       medulloblastoma   10.80123            11.18692
    ## 84      917       medulloblastoma   11.03512            11.18692
    ## 85      918       medulloblastoma   11.56152            11.18692
    ## 86      919       medulloblastoma   11.33546            11.18692
    ## 87      920       medulloblastoma   11.40119            11.18692
    ## 88      921       medulloblastoma   11.42586            11.18692
    ## 89      922       medulloblastoma   11.26910            11.18692
    ## 90      923       medulloblastoma   11.04525            11.18692
    ## 91      924       medulloblastoma   12.10601            11.18692
    ## 92      925       medulloblastoma   10.92315            11.18692
    ## 93      926       medulloblastoma   10.66018            11.18692
    ## 94      927       medulloblastoma   11.84743            11.18692
    ## 95      928       medulloblastoma   11.16694            11.18692
    ## 96      929       medulloblastoma   11.18648            11.18692
    ## 97      930       medulloblastoma   10.48618            11.18692
    ## 98      931       medulloblastoma   10.37532            11.18692
    ## 99      932       medulloblastoma   10.80910            11.18692
    ## 100     933       medulloblastoma   11.72406            11.18692
    ## 101     934       medulloblastoma   11.19517            11.18692
    ## 102     935       medulloblastoma   12.37256            11.18692
    ## 103     936                normal   11.05835            11.30912
    ## 104     937                normal   10.89108            11.30912
    ## 105     938                normal   12.42831            11.30912
    ## 106     939                normal   11.60726            11.30912
    ## 107     940                normal   11.04664            11.30912
    ## 108     941                normal   10.70182            11.30912
    ## 109     942                normal   10.78385            11.30912
    ## 110     943                normal   12.53642            11.30912
    ## 111     944                normal   11.29989            11.30912
    ## 112     945                normal   11.16260            11.30912
    ## 113     946                normal   11.13525            11.30912
    ## 114     947                normal   10.89174            11.30912
    ## 115     948                normal   11.47531            11.30912
    ## 116     949 pilocytic_astrocytoma   13.10124            12.91731
    ## 117     950 pilocytic_astrocytoma   13.38057            12.91731
    ## 118     951 pilocytic_astrocytoma   13.04765            12.91731
    ## 119     952 pilocytic_astrocytoma   12.95628            12.91731
    ## 120     953 pilocytic_astrocytoma   12.45164            12.91731
    ## 121     954 pilocytic_astrocytoma   13.22084            12.91731
    ## 122     955 pilocytic_astrocytoma   13.06536            12.91731
    ## 123     956 pilocytic_astrocytoma   13.01701            12.91731
    ## 124     957 pilocytic_astrocytoma   13.03605            12.91731
    ## 125     958 pilocytic_astrocytoma   13.22258            12.91731
    ## 126     959 pilocytic_astrocytoma   12.65823            12.91731
    ## 127     960 pilocytic_astrocytoma   12.81282            12.91731
    ## 128     961 pilocytic_astrocytoma   12.70699            12.91731
    ## 129     962 pilocytic_astrocytoma   12.68459            12.91731
    ## 130     963 pilocytic_astrocytoma   12.39772            12.91731
