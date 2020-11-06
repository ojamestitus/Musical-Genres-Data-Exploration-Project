Stat 850 Project Description
================
Neetu Regmi, Cassie Tangen, Oliver Titus …

## Instructions

Each member of your team should modify this document in some way and
push their modifications to the repository in a separate commit. This
will ensure that you have set your repository up in a way that ensures
all group members are working with the same repository.

Note that you must compile your readme (this document) for it to
properly display as part of your github repository.

Once you have received feedback on your project proposal (via Canvas)
you may alter this README so that it describes your final project
instead of the project proposal.

## Data Set

    Parsed with column specification:
    cols(
      .default = col_double(),
      track_id = col_character(),
      track_name = col_character(),
      track_artist = col_character(),
      track_album_id = col_character(),
      track_album_name = col_character(),
      track_album_release_date = col_character(),
      playlist_name = col_character(),
      playlist_id = col_character(),
      playlist_genre = col_character(),
      playlist_subgenre = col_character()
    )

    See spec(...) for full column specifications.

Data from TidyTuesday about songs on Spotify. There are many variables
included which are all described by TidyTuesday in the 01-21-2020 folder
titled song genres.

> You’ll want to describe the variables you’re interested in and talk a
> bit about how the data were assembled. You can use the tidytuesday
> page as a reference, but you’ll want to write this out in your own
> words.

## Potential Topics to Explore Using the Data Set

Describe avenues you might explore using the data

Cassie: Exploring if there is difference in song length based on genre.

    -- Attaching packages ------------------------------------------------------------------------------ tidyverse 1.3.0 --

    v ggplot2 3.3.2     v purrr   0.3.4
    v tibble  3.0.3     v dplyr   1.0.2
    v tidyr   1.1.1     v stringr 1.4.0
    v readr   1.3.1     v forcats 0.5.0

    -- Conflicts --------------------------------------------------------------------------------- tidyverse_conflicts() --
    x dplyr::filter() masks stats::filter()
    x dplyr::lag()    masks stats::lag()

![](README_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

I decided to use a stacked boxplot to look at and compare the duration
of the song duration in milliseconds of each different genre. It appears
that rock and R\&B have the longest durations and EDM is the shortest.

Create a few data frames that have been filtered for each genre. This
will aid in calculations later.

Find out how tracks there are for each genre. This may be useful later.

> Some of this would be a lot easier if you use group\_by\! Right now
> you’re doing it by hand\!

Let’s look closer by looking numerically at the means. I’m also curious
about how many songs there are for each genre so I am going to find the
number of songs in each genre now as well. I will put the data into a
table called genre\_table

    # A tibble: 6 x 2
      genre mean_duration
      <chr>         <dbl>
    1 EDM            1.33
    2 Latin          1.30
    3 Pop            1.31
    4 R&B            1.43
    5 Rap            1.28
    6 Rock           1.49

It appears that the genre with the longest songs is rock and the genre
with the shortest songs is rap. Would be interesting to perform a
hypothesis test to see if there is a statitical difference between the
lengths of songs.

Explore the popularity of each genre.
![](README_files/figure-gfm/unnamed-chunk-6-1.png)<!-- --> It appears
that pop and latin on average are more popular and EDM is the least
popular. Let’s go ahead and calculate mean popularity and add it to the
genre table

    # A tibble: 6 x 4
      genre mean_duration mean_popularity count
      <chr>         <dbl>           <dbl> <dbl>
    1 EDM            1.33            34.8  6043
    2 Latin          1.30            47.0  5155
    3 Pop            1.31            47.7  5507
    4 R&B            1.43            41.2  5431
    5 Rap            1.28            43.2  5746
    6 Rock           1.49            41.7  4951

It appears that EDM is the least popular on average, but it has the most
songs so that could be impacting the popularity. I would be interested
in performing a hypothesis test to see if EDM’s mean popularity is
statistically different than that of the others that all appear to be
roughly the same popularity-wise.

Explore the loudness of different genre.
![](README_files/figure-gfm/unnamed-chunk-8-1.png)<!-- --> EDM appears
to be the loudest with R\&B the least loud. Let’s look at the means
numerically as well.

    # A tibble: 6 x 5
      genre mean_duration mean_popularity mean_loudness count
      <chr>         <dbl>           <dbl>         <dbl> <dbl>
    1 EDM            1.33            34.8         -5.43  6043
    2 Latin          1.30            47.0         -6.26  5155
    3 Pop            1.31            47.7         -6.32  5507
    4 R&B            1.43            41.2         -7.86  5431
    5 Rap            1.28            43.2         -7.04  5746
    6 Rock           1.49            41.7         -7.59  4951

It seems R\&B is the least loud and EDM is the loudest. There is not a
huge spread between genre’s for loudness, but it does seem that EDM is a
decent amount louder than the other varieties. I would be interesting in
running a hypothesis test here as well.

Neetu: 1.Explore the relationship between playlist subgenre and track
popularity .

    Warning: package 'ggthemes' was built under R version 4.0.3

![](README_files/figure-gfm/unnamed-chunk-10-1.png)<!-- --> Some extra
info on the values of track popularity:The score is received from the
Spotify API. The value will be between 0 and 100, with 100 being the
most popular.The popularity is calculated by algorithm and is based, in
the most part, on the total number of plays the track has had and how
recent those plays are. From the above chart, It seems that most of the
playlist subgenere popularity lies between 75 and 100. Some of those are
dance pop, post-teen pop, pop edm, latin hip hop, hip hop while the
lowest popularity are around 75 like new jack swing, hard rock. I would
say according to the chart popularity of song among subgenre are not
extremely varied.

2.Explore a potential relationship between mode and song key.

> You’ll need to clean this data. Key should be A, B, C, D, E, F, G +
> flat/sharp. The numbers likely are factor categories, and you probably
> need the label. See the tidytuesday documentation

> Similarly, mode is also likely to be categorical:
> <https://en.wikipedia.org/wiki/Mode_(music)>. From looking at the
> documentation, it appears they’re misusing the term mode to represent
> major (1) or minor(0). If that’s the case, you might have better luck
> looking at the mode as it relates to genre - certain genres are much
> more likely to use minor keys (they have a sad, haunting sound,
> usually), where I’d assume pop and other upbeat stuff would be more
> likely to use a major key.

    Warning in grid.Call(C_stringMetric, as.graphicsAnnot(x$label)): font family not
    found in Windows font database
    
    Warning in grid.Call(C_stringMetric, as.graphicsAnnot(x$label)): font family not
    found in Windows font database
    
    Warning in grid.Call(C_stringMetric, as.graphicsAnnot(x$label)): font family not
    found in Windows font database

    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database

    Warning in grid.Call.graphics(C_text, as.graphicsAnnot(x$label), x$x, x$y, :
    font family not found in Windows font database

    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database
    
    Warning in grid.Call(C_textBounds, as.graphicsAnnot(x$label), x$x, x$y, : font
    family not found in Windows font database

![](README_files/figure-gfm/unnamed-chunk-11-1.png)<!-- --> This chart
shows the relationship that for mode 0 and 1, the key varies. By looking
at the vertical line, we could say that variability within mode 0 and 1
looks similar because they both vary on different value of key.

> You’re plotting this as a numeric variable when neither variable is
> actually numeric. Please revise and treat this as a categorical
> variable\!

Explore a potential relationship between energy and danceability,

    Warning: Computation failed in `stat_binhex()`:
      Package `hexbin` required for `stat_binhex`.
      Please install and try again.

![](README_files/figure-gfm/unnamed-chunk-12-1.png)<!-- --> This
scatterplot shows the relationship between danceability and energy also
we can see that highest number of observation falls around when both
danceability and energy are above 0.50.This suggests that we can expect
that high value of danceability will likely have high value of energy
ignoring some outliers. Also, I wanted to circle the region that has
large number of points cluster together, tried few things to get some
sort of outline to focus on that region didn’t work, was unsuccessful.

> I’ve used a binned plot to deal with the overplotting here - you see
> that there’s a big region of points, but no clear linear relationship
> - just a big point cloud.

Oliver:

1.  Explore the dancibility, energy, key,mode, speechiness, etc based on
    genre.

Box plot:

![](README_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

## Summary statistics for danceability for each genre:

### EDM

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.162   0.576   0.659   0.655   0.741   0.983 
```

### Latin

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.077   0.655   0.729   0.713   0.792   0.979 
```

### Pop

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.098   0.563   0.652   0.639   0.729   0.979 
```

### R\&B

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.140   0.584   0.689   0.670   0.771   0.977 
```

### Rap

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.150   0.634   0.737   0.718   0.820   0.975 
```

### Rock

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.000   0.429   0.523   0.521   0.615   0.956 
```

We see that rap has the highest mean danceability and rock has the
lowest mean danceabiltiy according the summary statistics and the box
plot. Box plot:

![](README_files/figure-gfm/unnamed-chunk-20-1.png)<!-- -->

## Summary statistics for energy for each genre:

### EDM

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.106   0.723   0.830   0.802   0.913   0.998 
```

### Latin

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.000   0.620   0.729   0.708   0.821   1.000 
```

### Pop

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.008   0.594   0.727   0.701   0.830   0.999 
```

### R\&B

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.012   0.469   0.596   0.591   0.721   0.995 
```

### Rap

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.016   0.546   0.665   0.651   0.776   0.999 
```

### Rock

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.017   0.606   0.775   0.733   0.896   0.998 
```

EDM appears has the highest mean energy according to the summary
statistics and box plot, and R\&B has the lowest mean energy. Box plot:

![](README_files/figure-gfm/unnamed-chunk-27-1.png)<!-- -->

## Summary statistics for speechiness for each genre:

### EDM

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.024   0.044   0.060   0.087   0.098   0.624 
```

### Latin

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.023   0.044   0.067   0.103   0.127   0.662 
```

### Pop

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.023   0.037   0.049   0.074   0.079   0.869 
```

### R\&B

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.022   0.042   0.068   0.117   0.158   0.918 
```

### Rap

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.024   0.079   0.178   0.198   0.290   0.877 
```

### Rock

``` 
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  0.000   0.033   0.042   0.058   0.063   0.488 
```

Every genre seems to have a very similar amount of speechiness, although
rap seems to have significantly higher mean speechiness than the other
genres.

2.  Explore the relationship between danceability and loudness.

<!-- end list -->

    `geom_smooth()` using formula 'y ~ x'

![](README_files/figure-gfm/unnamed-chunk-34-1.png)<!-- -->

``` 

Call:
lm(formula = danceability ~ loudness, data = spotify_songs)

Residuals:
    Min      1Q  Median      3Q     Max 
-0.6310 -0.0924  0.0164  0.1055  0.3304 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 0.663114   0.001970  336.64  < 2e-16 ***
loudness    0.001230   0.000268    4.59  4.4e-06 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 0.145 on 32831 degrees of freedom
Multiple R-squared:  0.000642,  Adjusted R-squared:  0.000611 
F-statistic: 21.1 on 1 and 32831 DF,  p-value: 4.41e-06
```

Looking at the scatter plot, there appears to be no significant
relationship between loudness and danceability because of the
coefficient on loudness and the R^2 being almost 0. 3. Explore the
relationship between danceability and tempo.

    `geom_smooth()` using formula 'y ~ x'

![](README_files/figure-gfm/unnamed-chunk-36-1.png)<!-- -->

``` 

Call:
lm(formula = danceability ~ tempo, data = spotify_songs)

Residuals:
    Min      1Q  Median      3Q     Max 
-0.7749 -0.0899  0.0152  0.1030  0.3332 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)    
(Intercept)  7.75e-01   3.62e-03   213.9   <2e-16 ***
tempo       -9.93e-04   2.93e-05   -33.9   <2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 0.143 on 32831 degrees of freedom
Multiple R-squared:  0.0339,    Adjusted R-squared:  0.0339 
F-statistic: 1.15e+03 on 1 and 32831 DF,  p-value: <2e-16
```

According to this regression output, there appears to be a significant
negative relationship between danceability and tempo because of the
negative and significant coeffiecient on loudness. But, the R^2 is quite
small, so most of the variability in danceability is not explained by
tempo. This is also apparent in the scatter plot.

## Group Members

List all of the project contributors here. Neetu Regmi Oliver Titus
Cassie Tangen

## Cassie’s plan to make things cohesive:

We should look at the following:

Genre: danceability, energy, speechiness, (Oliver has done) popularity,
length, and loudness. (Cassie has done)

Create a scatterplot and perform a test to see if there is a
relationship between popularity and each of the following: danceability,
energy, speechiness, length, and loudness. (Neetu you have done a
scatterplot within your work could you modify that to look at each of
these?)

## A rough draft of “paper” portion:

(this will get intergrated above as we clean things up and oragnize
later.)

Introduction:

There are a wide range of genres and each genre has its own unique
traits that sets it apart from the other genres. We plan to investigate
what makes rock, R\&B, rap, EDM, latin, and pop different based on their
length, danceability, energy, and loudness. We will then analyze the
popularity of each genre. Based on their popularities we will look to
see which factor plays the most important roll, if any does, in the
popularity of songs.

Data Description:

The data we are analyzing was obtained from TidyTuesday. The data was
obtained by using the spotifyr package created by Charlie Thompson,
Josiah Parry, Donal Phipps, and Tom Wolff. The spotifyr package allows
the bulk pulling of features tracks from Spotify’s Web API. Since we are
novices at using new packages, we decided just using the data collected
by TidyTuesday using spotifyr would be sufficient for our study. We do
recognize the fact that there is a potential bias to the data we are
analyzing because we are not aware of the search parameters used by
TidyTuesday when collecting this data using spotifyr.

In our study we will focus on the danceability, energy, speechiness,
popularity, length, and loudness of songs. We will primarily group data
based on the song’s genre.

We need to find a properly cite all of the definitions. (use:
<https://github.com/rfordatascience/tidytuesday/tree/master/data/2020/2020-01-21>)

Format of the rest of the paper I am unsure of how to make super
cohesive, but I could see us going through and doing the scatter plot
and listing some descriptive statistics followed by the hypothesis test
for each of the items listed above. We want to be sure everything is
relevant to what we are studying.

## References:

TidyTuesday:
<https://github.com/rfordatascience/tidytuesday/tree/master/data/2020/2020-01-21>

Spotifyr: <https://www.rcharlie.com/spotifyr/>
