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
    ##  1 Rap   Future      SOME MORE  5sT2yQr…         55       0.493 
    ##  2 Regg… Lunay       Si Te Vas… 43vTR8i…         62       0.488 
    ##  3 Alte… BANNERS     Start A R… 3cpOqFZ…         59       0.0135
    ##  4 Come… Tim Wilson  It Was Am… 5HIWweV…         14       0.697 
    ##  5 Alte… Eric Belli… Repeat     06Ygqg0…         44       0.256 
    ##  6 Movie Cerise Cal… "L’amour … 4fqHESw…         32       0.306 
    ##  7 Come… Tommy John… Humorous … 0YiG40a…         30       0.829 
    ##  8 Pop   Logic       Wassup     5KVciTE…         64       0.0822
    ##  9 Rock  Cake        Short Ski… 3OOFEF2…         64       0.0028
    ## 10 World Dean Evens… Mending Y… 6tIFO8z…         42       0.967 
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
    ##         57.395025         -10.394532          16.976497  
    ##            energy   instrumentalness           liveness  
    ##         -7.282225          -3.750035           0.649082  
    ##          loudness        speechiness              tempo  
    ##          0.727135         -10.775193          -0.002083  
    ##           valence  liveness:loudness  
    ##         -8.474525           1.068332

    ## [1] 0.2987758

    ## [1] 0.2973702

    ## Start:  AIC=26680.94
    ## popularity ~ acousticness + danceability + energy + instrumentalness + 
    ##     liveness + loudness + speechiness + tempo + valence + loudness * 
    ##     liveness
    ## 
    ##                     Df Sum of Sq     RSS   AIC
    ## - tempo              1      18.7 1034057 26679
    ## <none>                           1034038 26681
    ## - instrumentalness   1    3744.3 1037782 26697
    ## - energy             1    3765.7 1037804 26697
    ## - liveness:loudness  1    5761.1 1039799 26707
    ## - speechiness        1   11246.2 1045284 26733
    ## - valence            1   14222.1 1048260 26747
    ## - acousticness       1   23538.2 1057576 26792
    ## - danceability       1   27100.1 1061138 26808
    ## 
    ## Step:  AIC=26679.03
    ## popularity ~ acousticness + danceability + energy + instrumentalness + 
    ##     liveness + loudness + speechiness + valence + liveness:loudness
    ## 
    ##                     Df Sum of Sq     RSS   AIC
    ## <none>                           1034057 26679
    ## - instrumentalness   1    3748.2 1037805 26695
    ## - energy             1    3788.7 1037845 26695
    ## - liveness:loudness  1    5745.5 1039802 26705
    ## - speechiness        1   11249.4 1045306 26731
    ## - valence            1   14442.2 1048499 26746
    ## - acousticness       1   23560.8 1057617 26790
    ## - danceability       1   27770.3 1061827 26810

    ## 
    ## Call:
    ## lm(formula = popularity ~ acousticness + danceability + energy + 
    ##     instrumentalness + liveness + loudness + speechiness + valence + 
    ##     liveness:loudness, data = songs)
    ## 
    ## Coefficients:
    ##       (Intercept)       acousticness       danceability  
    ##           57.1178           -10.3741            17.0352  
    ##            energy   instrumentalness           liveness  
    ##           -7.3000            -3.7519             0.6526  
    ##          loudness        speechiness            valence  
    ##            0.7259           -10.7767            -8.5030  
    ## liveness:loudness  
    ##            1.0663

    ## [1] 0.2987631

    ## [1] 0.2974984

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
    ##      44.151        1.125

    ## [1] 0.0009816861

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
    ##       33.38        18.98

    ## [1] 0.08253054

    ## 
    ## Call:
    ## lm(formula = popularity ~ danceability, data = songs)
    ## 
    ## Coefficients:
    ##  (Intercept)  danceability  
    ##        29.34         27.38

    ## [1] 0.08609871

    ## 
    ## Call:
    ## lm(formula = popularity ~ liveness, data = songs)
    ## 
    ## Coefficients:
    ## (Intercept)     liveness  
    ##       48.31       -17.62

    ## [1] 0.03979683

    ## 
    ## Call:
    ## lm(formula = popularity ~ liveness, data = songs)
    ## 
    ## Coefficients:
    ## (Intercept)     liveness  
    ##       48.31       -17.62

    ## [1] 0.03979683

### Bootstrapping

### Conclusion

Your project goes here\! Before you submit, make sure your chunks are
turned off with `echo = FALSE`.

You can add sections as you see fit. Make sure you have a section called
Introduction at the beginning and a section called Conclusion at the
end. The rest is up to you\!
