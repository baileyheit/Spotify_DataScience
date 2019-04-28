Project Proposal: What Makes a Song Popular on Spotify?
================
CCBK
3/21/18

    ## Parsed with column specification:
    ## cols(
    ##   genre = col_character(),
    ##   artist_name = col_character(),
    ##   track_name = col_character(),
    ##   track_id = col_character(),
    ##   popularity = col_double(),
    ##   acousticness = col_double(),
    ##   danceability = col_double(),
    ##   duration_ms = col_double(),
    ##   energy = col_double(),
    ##   instrumentalness = col_double(),
    ##   key = col_character(),
    ##   liveness = col_double(),
    ##   loudness = col_double(),
    ##   mode = col_character(),
    ##   speechiness = col_double(),
    ##   tempo = col_double(),
    ##   time_signature = col_character(),
    ##   valence = col_double()
    ## )

    ## # A tibble: 5,000 x 18
    ##    genre artist_name track_name track_id popularity acousticness
    ##    <chr> <chr>       <chr>      <chr>         <dbl>        <dbl>
    ##  1 Pop   Fifth Harm… Worth It   41Fflg7…         76    0.063    
    ##  2 Coun… Lori McKen… People Ge… 2Tm7nXW…         44    0.216    
    ##  3 Jazz  Montefiori… Conversaz… 5DwEJRx…         46    0.141    
    ##  4 Rock  Neil Diamo… Forever I… 1K1nzhb…         61    0.0221   
    ##  5 Movie Emmanuel M… Et si on … 3CV62vV…         34    0.0473   
    ##  6 Come… Mo Mandel   Hand Jobs… 37DtjmD…         11    0.856    
    ##  7 Folk  Elvis Cost… Veronica   5zHgT1i…         49    0.128    
    ##  8 Anime Nirvana     Serve The… 3w5Ekq9…         53    0.0000136
    ##  9 R&B   D'Angelo    The Root   2Qmkg3J…         44    0.498    
    ## 10 Alte… DRAMA       Missing    5tcuzbA…         51    0.0392   
    ## # … with 4,990 more rows, and 12 more variables: danceability <dbl>,
    ## #   duration_ms <dbl>, energy <dbl>, instrumentalness <dbl>, key <chr>,
    ## #   liveness <dbl>, loudness <dbl>, mode <chr>, speechiness <dbl>,
    ## #   tempo <dbl>, time_signature <chr>, valence <dbl>

### Introduction

### Visualization

### Data Wrangling

### Linear Regression

    ## 
    ## Call:
    ## lm(formula = popularity ~ acousticness + danceability + energy + 
    ##     instrumentalness + liveness + loudness + speechiness + tempo + 
    ##     valence + loudness * liveness, data = songs)
    ## 
    ## Coefficients:
    ##       (Intercept)       acousticness       danceability  
    ##          55.10788          -13.03446           16.67457  
    ##            energy   instrumentalness           liveness  
    ##          -7.09103           -5.16912           -2.59013  
    ##          loudness        speechiness              tempo  
    ##           0.49316           -6.42511            0.01177  
    ##           valence  liveness:loudness  
    ##          -8.09749            1.08062

    ## [1] 0.2962603

    ## [1] 0.2948497

    ## Start:  AIC=26716.81
    ## popularity ~ acousticness + danceability + energy + instrumentalness + 
    ##     liveness + loudness + speechiness + tempo + valence + loudness * 
    ##     liveness
    ## 
    ##                     Df Sum of Sq     RSS   AIC
    ## <none>                           1041483 26717
    ## - tempo              1       601 1042083 26718
    ## - energy             1      3480 1044962 26732
    ## - speechiness        1      3785 1045268 26733
    ## - liveness:loudness  1      6351 1047834 26745
    ## - instrumentalness   1      7359 1048842 26750
    ## - valence            1     12519 1054001 26775
    ## - danceability       1     24517 1065999 26831
    ## - acousticness       1     37419 1078902 26891

    ## 
    ## Call:
    ## lm(formula = popularity ~ acousticness + danceability + energy + 
    ##     instrumentalness + liveness + loudness + speechiness + tempo + 
    ##     valence + loudness * liveness, data = songs)
    ## 
    ## Coefficients:
    ##       (Intercept)       acousticness       danceability  
    ##          55.10788          -13.03446           16.67457  
    ##            energy   instrumentalness           liveness  
    ##          -7.09103           -5.16912           -2.59013  
    ##          loudness        speechiness              tempo  
    ##           0.49316           -6.42511            0.01177  
    ##           valence  liveness:loudness  
    ##          -8.09749            1.08062

    ## [1] 0.2962603

    ## [1] 0.2948497

score\_hat = 56.20 + -11.30 \* acousticness + 17.19 \* danceability -
5.933 \* energy - 4.11 \* instrumentalness + -6.40 \* liveness + 0.60 \*
loudness + -10.36 \* speechiness + -8.25 \* valence + 0.62 \*
liveness:loudness

When all variables have a value of 0, then it is expected that a song’s
populariy is 56.20 One example of how a variable influences the
popularity is with acousticness. If a song’s acoustic score increases by
1 then popularity will on average decrease by 11.30 points, all else
held constant. There is also an apparent interaction between
danceability and energy. When the interaction increases by one on
average the popularity decreases by 12.96 points, all else held
constant.

The adjusted R squared value for this model is 0.289, which means that
roughly 28.9% of the variability in a song’s popularity can be explained
by the different variables in the multiple regression model. This
indicates that there is a weak to moderate positive overall realtionship
between a song’s popularity and the different variables related to a
song.

    ## 
    ## Call:
    ## lm(formula = popularity ~ mode, data = songs)
    ## 
    ## Coefficients:
    ## (Intercept)    modeMinor  
    ##      43.979        1.746

    ## [1] 0.002316003

score\_hat = 43.77 + 2.007 \* mode\_minor

Minor equation: score\_hat = 43.77 + 2.007 \* 1 = 45.77

Major equestion: score\_hat = 43.77 + 2.007 \* 0 = 43.77

Songs that are in the major mode tent to have higher popularity scores
than songs in a minor key. All else held constant, theere is an expected
popularity score increase of 2.007 if the song is in the minor key
compared to the major key.

    ## 
    ## Call:
    ## lm(formula = popularity ~ energy, data = songs)
    ## 
    ## Coefficients:
    ## (Intercept)       energy  
    ##       33.36        19.31

    ## [1] 0.08528234

    ## 
    ## Call:
    ## lm(formula = popularity ~ danceability, data = songs)
    ## 
    ## Coefficients:
    ##  (Intercept)  danceability  
    ##        28.56         28.92

    ## [1] 0.0921327

    ## 
    ## Call:
    ## lm(formula = popularity ~ liveness, data = songs)
    ## 
    ## Coefficients:
    ## (Intercept)     liveness  
    ##       48.85       -20.04

    ## [1] 0.05174895

    ## 
    ## Call:
    ## lm(formula = popularity ~ liveness, data = songs)
    ## 
    ## Coefficients:
    ## (Intercept)     liveness  
    ##       48.85       -20.04

    ## [1] 0.05174895

### Bootstrapping

### Conclusion

Your project goes here\! Before you submit, make sure your chunks are
turned off with `echo = FALSE`.

You can add sections as you see fit. Make sure you have a section called
Introduction at the beginning and a section called Conclusion at the
end. The rest is up to you\!
