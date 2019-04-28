Linear Regression
================

``` r
full_model = lm(popularity ~ acousticness +
                  danceability +
                  energy +
                  instrumentalness +
                  liveness +
                  loudness +
                  speechiness + 
                  tempo + 
                  valence +
                  energy * danceability,
                data = songs)

full_model
```

    ## 
    ## Call:
    ## lm(formula = popularity ~ acousticness + danceability + energy + 
    ##     instrumentalness + liveness + loudness + speechiness + tempo + 
    ##     valence + energy * danceability, data = songs)
    ## 
    ## Coefficients:
    ##         (Intercept)         acousticness         danceability  
    ##           54.914855           -11.147571            23.382243  
    ##              energy     instrumentalness             liveness  
    ##           -0.451486            -3.232293           -10.362437  
    ##            loudness          speechiness                tempo  
    ##            0.801449           -10.290325             0.002643  
    ##             valence  danceability:energy  
    ##           -8.969275           -12.958830

``` r
glance(full_model)$r.squared
```

    ## [1] 0.2817728

``` r
glance(full_model)$adj.r.squared
```

    ## [1] 0.2817413

``` r
selected_model <- step(full_model, direction = "backward")
```

    ## Start:  AIC=1224718
    ## popularity ~ acousticness + danceability + energy + instrumentalness + 
    ##     liveness + loudness + speechiness + tempo + valence + energy * 
    ##     danceability
    ## 
    ##                       Df Sum of Sq      RSS     AIC
    ## <none>                             48911849 1224718
    ## - tempo                1      1346 48913195 1224723
    ## - danceability:energy  1     70486 48982335 1225045
    ## - instrumentalness     1    134704 49046553 1225344
    ## - speechiness          1    483495 49395344 1226961
    ## - liveness             1    645371 49557220 1227707
    ## - valence              1    711737 49623586 1228013
    ## - loudness             1   1120218 50032067 1229883
    ## - acousticness         1   1232834 50144683 1230396

``` r
selected_model
```

    ## 
    ## Call:
    ## lm(formula = popularity ~ acousticness + danceability + energy + 
    ##     instrumentalness + liveness + loudness + speechiness + tempo + 
    ##     valence + energy * danceability, data = songs)
    ## 
    ## Coefficients:
    ##         (Intercept)         acousticness         danceability  
    ##           54.914855           -11.147571            23.382243  
    ##              energy     instrumentalness             liveness  
    ##           -0.451486            -3.232293           -10.362437  
    ##            loudness          speechiness                tempo  
    ##            0.801449           -10.290325             0.002643  
    ##             valence  danceability:energy  
    ##           -8.969275           -12.958830

``` r
glance(selected_model)$r.squared
```

    ## [1] 0.2817728

``` r
glance(selected_model)$adj.r.squared
```

    ## [1] 0.2817413

score\_hat = 54.92 + -11.24 \* acousticness + 16.22 \* danceability -
8.11 \* energy - 3.61 \* instrumentalness + -10.06 \* liveness + 0.71 \*
loudness + -9.89 \* speechiness + 0.018 \* tempo + -8.90 \* valence +
-13.36 \* danceability:energy

When all variables have a value of 0, then it is expected that a song’s
populariy is 54.92. One example of how a variable influences the
popularity is with acousticness. If a song’s acoustic score increases by
1 then popularity will on average decrease by 11.14 points, all else
held constant. There is also an apparent interaction between
danceability and energy. When the interaction increases by one on
average the popularity decreases by 12.96 points, all else held
constant.

The adjusted R squared value for this model is 0.28, which means that
roughly 28.2% of the variability in a song’s popularity can be explained
by the different variables in the multiple regression model. This
indicates that there is a weak to moderate positive overall realtionship
between a song’s popularity and the different variables related to a
song.

``` r
mode_model = lm(popularity ~ mode, data = songs)

mode_model
```

    ## 
    ## Call:
    ## lm(formula = popularity ~ mode, data = songs)
    ## 
    ## Coefficients:
    ## (Intercept)    modeMinor  
    ##      43.517        1.947

``` r
glance(mode_model)$r.squared
```

    ## [1] 0.002910086

score\_hat = 43.517 + 1.947 \* mode\_minor

Minor equation: score\_hat = 43.517 + 1.947 \* 1 = 45.46

Major equestion: score\_hat = 43.517 + 1.947 \* 0 = 43.517

Songs that are in the major mode tent to have higher popularity scores
than songs in a minor key. All else held constant, theere is an expected
popularity score increase of 1.947 if the song is in the minor key
compared to the major key.

``` r
energy_model = lm(popularity ~ energy, data = songs)

energy_model
```

    ## 
    ## Call:
    ## lm(formula = popularity ~ energy, data = songs)
    ## 
    ## Coefficients:
    ## (Intercept)       energy  
    ##       33.51        18.41

``` r
glance(energy_model)$r.squared
```

    ## [1] 0.07709083
