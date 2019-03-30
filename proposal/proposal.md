Project Proposal: What Makes a Song Popular on Spotify?
================
CCBK
3/21/19

## Section 1. Introduction

The goal of our project is to determine the qualities of a song that
influence popularity on Spotify. The dataset was retrieved online at
<https://www.kaggle.com/edalrami/19000-spotify-songs>. The data is
derived from the Spotify Web API, which uses internal Spotify metrics to
determine the parameters of the dataset. For subjective variables such
as danceability and instrumentalness, the Spotify Web API utilizes Echo
Nest algorithms. The dataset curator retrieved data for 19,000 songs at
random and aggregated this information into the dataset. Below is a
brief description explaining the 18 variables that are within the chosen
dataset.

  - Categorical Variables: Genre, artist\_name, track\_name, track\_id,
    mode, time\_signature (An estimated overall time signature of a
    track), key.

  - Continuous Numerical Variables: duration\_ms (Duration of song in
    miliseconds), loudness (The overall loudness of the track in
    decibels), tempo (The overall estimate beats per minute of the
    track).

  - Discrete Numerical Variables: popularity (The popularity of the
    track from 0 to 100 based on recent stream counts), acousticness (A
    confidence measure from 0 to 1.0 of whether the song is acoustic),
    danceability (How suitable a song is for dancing from 0 to 1.0),
    liveness (The likelihood that the track was performed live from 0 to
    1.0), valence (A measure from 0.0 to 1.0 describing the musical
    positiveness), instrumentalness (A confidence measure from 0 to 1.0
    on whether song is instrumental), energy (A song’s energy from 0.0
    to 1.0 considering various factors), speechiness (A measure of how
    exclusively speech-like the track is from 0 to 1.0).

## Section 2. Data analysis plan

This project will analyze the variables of a song that correlate with a
higher song popularity. To find this, we will assign song popularity as
our dependent response variable and the other variables such as
danceability, energy, and key as our predictor variables. Using single
predictors models and backwards selection using multiple predictors
models, we can determine which variables are the best predictors of a
song’s popularity score. Higher R^2 value for single predictors model or
a higher adjusted R^2 value for multiple predictors can help us
determine this.

In addition to looking at individual songs, we intend to group songs by
genres or playlists. After grouping, we will explore the difference in
popularity means/medians within certain genres. For example, if the
genres rap and pop each have 100 songs within the data set, we will
perform simulations on samples with replacement from both genres to
create a distribution of the difference in means. In this case,
popularity score would be the response variable and the genre would be
the explanatory variable. Then we will look at the p-value (p-value \<
0.05 for proving dependence) to determine if there is a significant
difference. 95% confidence intervals for the difference in popularity
score means or medians can also be used to make conclusions about the
difference in populations.

Visualizations can be used to determine skewness of the data set. This
will help us determine whether mean/SD or median/IQR is more fitting to
describe the certain variables or groupings. We will be interested in
looking at the distribution of different variables. A skew will indicate
that the songs tend towards a certain type of sound. The goal is to have
a representative sample of the entirety of spotify, with a range of
different popularities, keys, liveliness, and more.

## Section 3. Data

    ## Observations: 228,159
    ## Variables: 18
    ## $ genre            <chr> "Opera", "Opera", "Opera", "Opera", "Opera", "O…
    ## $ artist_name      <chr> "Giuseppe Verdi", "Giacomo Puccini", "Giacomo P…
    ## $ track_name       <chr> "Stiffelio, Act III: Ei fugge! … Lina, pensai c…
    ## $ track_id         <chr> "7EsKYeHtTc4H4xWiTqSVZA", "7MfmRBvqaW0I6UTxXnad…
    ## $ popularity       <dbl> 21, 18, 10, 17, 19, 20, 13, 19, 20, 16, 20, 17,…
    ## $ acousticness     <dbl> 0.986, 0.972, 0.935, 0.961, 0.985, 0.990, 0.980…
    ## $ danceability     <dbl> 0.3130, 0.3600, 0.1680, 0.2500, 0.1420, 0.2110,…
    ## $ duration_ms      <dbl> 490867, 176797, 266184, 288573, 629760, 334720,…
    ## $ energy           <dbl> 0.23100, 0.20100, 0.47000, 0.00605, 0.05800, 0.…
    ## $ instrumentalness <dbl> 4.31e-04, 2.80e-02, 2.04e-02, 0.00e+00, 1.46e-0…
    ## $ key              <chr> "C#", "D#", "C", "D", "D", "G#", "D", "F#", "C"…
    ## $ liveness         <dbl> 0.0964, 0.1330, 0.3630, 0.1200, 0.0969, 0.0730,…
    ## $ loudness         <dbl> -14.287, -19.794, -8.415, -33.440, -23.625, -20…
    ## $ mode             <chr> "Major", "Major", "Major", "Major", "Major", "M…
    ## $ speechiness      <dbl> 0.0547, 0.0581, 0.0383, 0.0480, 0.0493, 0.0534,…
    ## $ tempo            <dbl> 86.001, 131.798, 75.126, 76.493, 172.935, 81.40…
    ## $ time_signature   <chr> "4/4", "4/4", "3/4", "4/4", "4/4", "3/4", "1/4"…
    ## $ valence          <dbl> 0.0886, 0.3690, 0.0696, 0.0380, 0.0382, 0.0400,…
