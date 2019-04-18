# data

Observations: 228,159
Variables: 18

The variables for this data set are: 
Song_name - The name of the track.
Song_popularity - The popularity of the track from 0 to 100 based on recent stream counts from when the data was pulled from the API.
Song_duration_ms - The duration of the track in milliseconds.
Acousticness - A confidence measure from 0 to 1.0 of whether the song is acoustic.
Danceability - How suitable a song is for dancing from 0 to 1.0 based on tempo, rhythmic stability, beat strength, and overall regularity.
Energy - A measure of a song’s energy from 0.0 to 1.0 and represents a perceptual measure of intensity and activity including dynamic range, perceived loudness, timbre, onset rate, and general entropy.
Instrumentalness - A prediction from 0 to 1.0 on whether a track is majorly instrumental. Values above 0.5 represent an instrumental track, but the closer the index is to 1.0 the more confident the prediction. 
Key - The key of the track based on the Pitch Class notation.
Liveness - The likelihood that the track was performed live from 0 to 1.0
Loudness - The overall loudness of the track in decibels.
Audio_mode - The modality of the track, 1 for major, 0 for minor.
Speechiness - A measure of how exclusively speech-like the track is from 0 to 1.0. Values above 0.66 describe tracks that are probably made entirely of spoken words. Values between 0.33 and 0.66 describe tracks that may contain both music and speech, either in sections or layered, including such cases as rap music. Values below 0.33 most likely represent music and other non-speech-like tracks.
Tempo - The overall estimate beats per minute of the track.
Time_signature - An estimated overall time signature of a track. The time signature (meter) is a notational convention to specify how many beats are in each bar (or measure).
Audio_valence - A measure from 0.0 to 1.0 describing the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).

Categorical Variables:
Genre, artist_name, track_name, track_id, mode, time_signature (An estimated overall time signature of a track), key

Continuous Numerical:
$ duration_ms      Duration of song in miliseconds
$ loudness         The overall loudness of the track in decibels.
$ speechiness      A measure of how exclusively speech-like the track is from 0 to 1.0
$ tempo            The overall estimate beats per minute of the track.

Discrete Numerical Variables
$ popularity       The popularity of the track from 0 to 100 based on recent stream counts
$ acousticness     A confidence measure from 0 to 1.0 of whether the song is acoustic
$ danceability     How suitable a song is for dancing from 0 to 1.0 
$ liveness         The likelihood that the track was performed live from 0 to 1.0
$ valence          A measure from 0.0 to 1.0 describing the musical positiveness 
$ instrumentalness A confidence measure from 0 to 1.0 on whether song is instrumental
$ energy           A song’s energy from 0.0 to 1.0 considering various factors

