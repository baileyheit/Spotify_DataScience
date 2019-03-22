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
Nest algorithms. The dataset curator retrieved data for 19,000 songs and
aggregated this information into the dataset.

The variables for this data set are: \* Song\_name - The name of the
track. \* Song\_popularity - The popularity of the track from 0 to 100
based on recent stream counts from when the data was pulled. \*
Song\_duration\_ms - The duration of the track in milliseconds. \*
Acousticness - A confidence measure from 0 to 1.0 of whether the song is
acoustic. \* Danceability - How suitable a song is for dancing from 0 to
1.0 based on tempo, rhythmic stability, beat strength, and overall
regularity. \* Energy - A song’s energy from 0.0 to 1.0 considering
dynamic range, perceived loudness, timbre, onset rate, and general
entropy. \* Instrumentalness - A confidence measure from 0 to 1.0 on
whether a track is majorly instrumental. Values above 0.5 represent an
instrumental track, but the closer the index is to 1.0 the more
confident the prediction. \* Key - The key of the track based on the
Pitch Class notation. \* Liveness - The likelihood that the track was
performed live from 0 to 1.0 \* Loudness - The overall loudness of the
track in decibels. \* Audio\_mode - The modality of the track, 1 for
major, 0 for minor. \* Speechiness - A measure of how exclusively
speech-like the track is from 0 to 1.0. Values above 0.66 describe
tracks that are probably made entirely of spoken words. Values between
0.33 and 0.66 describe tracks that may contain both music and speech,
either in sections or layered, including such cases as rap music. Values
below 0.33 most likely represent music and other non-speech-like tracks.
\* Tempo - The overall estimate beats per minute of the track. \*
Time\_signature - An estimated overall time signature of a track. The
time signature (meter) is a notational convention to specify how many
beats are in each bar (or measure). \* Audio\_valence - A measure from
0.0 to 1.0 describing the musical positiveness conveyed by a track.
Tracks with high valence sound more positive (e.g. happy, cheerful,
euphoric), while tracks with low valence sound more negative (e.g. sad,
depressed, angry).

## Section 2. Data analysis plan

This project will analyze the variables of a song that correlate with
song popularity. To find this, we will assign song popularity as our
dependent response variable and the other variables such as
danceability, energy, key, etc as our predictor variables. In addition
to looking at individual songs, we intend to group songs by
genres/playlists. After grouping, we will explore the difference in
population means within certain genres. For example, if the genres rap
and pop each have 100 songs within the data set, we will perform
simulations on small samples from both genres to determine mean
popularity within each population. Then we will look at the difference
in means to see if there is significant variation. Visualizations can be
used to determine skewness of the data set using single predictors
models and backwards selection using multiple predictors models. This
will help us determine whether mean/SD or median/IQR is more fitting to
describe the data set. We will be interested in looking at the
distribution of different variables.The goal is to have a representative
sample of the entirety of spotify, with a range of different
popularities, keys, liveliness, etc. A skew will indicate that the songs
tend towards a certain type of sound. To support our hypothesized
answer, we want to look at what variables are better predictors of
popularity (higher R^2 value for single predictors model or a higher
adjusted R^2 value for multiple predictors), 95% confidence intervals
for the difference in popularity score means or medians (depending on
skewness of data) between different variables, and interpretations of
visualizations in order to determine skewness of data.

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
