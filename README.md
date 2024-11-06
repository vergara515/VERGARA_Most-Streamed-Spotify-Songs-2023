# Most Streamed Spotify Songs 2023

Author: Vergara, Revie Shane D.

---

In this exploratory data analysis (EDA), a dataset about the popular tracks on Most Streamed Spotify Songs 2023 is explored along with its various musical attributes and their relationship to popularity metrics like the number of streams. An initial exploration provided summary statistics, focusing on key features such as release dates, BPM, and danceability which helped understand the different features available. Through visualizations like bar charts and scatter plots, trends and patterns are uncovered that reveal insights into what makes a track successful. Finally, correlations between musical characteristics and streams are also investigated, offering recommendations to better understand the dynamics of popular music.

---

## Initializing the Dataset

In the first part, the necessary libraries and the dataset are loaded in order to get the necessary information and an overview of the overall structure.

![image](https://github.com/user-attachments/assets/b3a6dc42-8782-4ae4-a59f-c6e3b380181c)

_Functions:_

1. **import pandas as pd**
   
   > Description: This function grants access to the Pandas Library.

2. **import matplotlib.pyplot as plt**
   
   > Description: This function grants access to the Matplotlib Library.

3. **import seaborn as sns**

   > Description: This function grants access to the Seaborn Library.

---

![image](https://github.com/user-attachments/assets/75f32c86-62b3-4c88-8e68-6d25efb4ba46)

_Functions:_

1. **data = pd.read_excel('spotify-2023.xlsx')**
   
   > Description: This function loads the 'spotify-2023.xlsx' dataset and is stored in the variable 'data'.

---

## Overview of Dataset

Understanding the structure and content of the dataset is an essential part of doing an analysis. This involves checking the number of rows and columns, reviewing data types, and identifying any missing values that might require cleaning.

### a. How many rows and columns does the dataset contain?

![image](https://github.com/user-attachments/assets/9f1139a6-3cdb-4f12-aa6b-10963d8fe90c)

_Functions:_

1. **data.shape**

   > Description: The 'data.shape' function is used to know how many rows and columns the dataset has in 'data'.

2. **print()**
  
   > Description: This function prints the statement inside it.

_Analysis:_

The dataset contains 953 tracks (rows) which all have 24 unique attributes or features (columns).

### b.1. What are the data types of each column? 

![image](https://github.com/user-attachments/assets/f017319a-dcf3-4992-a875-ed2262c44c65)

_Functions:_

1. **data.dtypes**

   > Description: The 'data.dtypes' function is used to reflect the data type of each column.

**Note:** In this dataset, the data types 'object' represents text or mixed data, 'int64' represents a 64-bit integer, and 'float64' represents a 64-bit float point number. 

_Analysis:_

There are a lot of 'int64' data types of columns. Second to it is the 'object' data type and then the least occurring data type would be 'float64'.

### b.2. Are there any missing values?

![image](https://github.com/user-attachments/assets/5cfcc8f0-0756-4489-9ff6-918245dfd886)

_Functions:_

1. **data.isnull()**

   > Description: This function checks for any missing values in each column of the dataset with True in places where values are missing and False where they are present.

2. **.sum()**

   > Description: This function '.sum()' then adds up the True values (where there are missing values) for each column, giving a count of missing values per column.

3. **print()**
  
   > Description: This function prints the statement inside it.

_Analysis:_

There are missing values in some columns, such as 1 is missing for streams, 50 are missing for in_shazam_charts, and 95 are missing in key. Accordingly, these missing values may affect how the data could be interpreted as a different interpretation may be concluded.

---

## Basic Descriptive Statistics

In this section, insights into the dataset's numerical and categorical features are extracted. By understanding central tendencies in the streams column and exploring distributions of released_year and artist_count, potential trends or outliers are identified.

### a. What are the mean, median, and standard deviation of the streams column?

![image](https://github.com/user-attachments/assets/cc7ab7a1-61ab-4c43-a476-bd571535735d)

_Functions:_

1. pd.to_numeric(data['streams'])

   > Description: This function is used to convert the values in the streams column to a numeric type.
   
2. errors = 'coerce'

   > Description: This parameter prevents the function from throwing an error when encountering problematic entries.

**Note:** This line of code was added since there are texts in the stream column that are not allowed when getting the mean, median, and standard deviation. Therefore, this will prevent that error and allow the codes to get the mean, median, and standard deviation run.

---

![image](https://github.com/user-attachments/assets/b62b74a2-de8f-49db-97e2-ec8c689af9b9)

_Functions:_

1. **data['streams'].mean()**

   > Description: This function gets the mean in the dataset named 'data' which is limited to its 'streams' column only.

2. **print()**
  
   > Description: This function prints the statement inside it.

---

![image](https://github.com/user-attachments/assets/96b1df85-a661-428f-8f8a-e9816f2739a1)

_Functions:_

1. **data['streams'].median()**

   > Description: This function gets the median in the dataset named 'data' which is limited to its 'streams' column only.

2. **print()**
  
   > Description: This function prints the statement inside it.

---

![image](https://github.com/user-attachments/assets/edbe2d24-c8f1-4194-b76b-0fb5d54ff090)

_Functions:_

1. **data['streams'].std()**

   > Description: This function gets the standard devation in the dataset named 'data' which is limited to its 'streams' column only.

2. **print()**
  
   > Description: This function prints the statement inside it.

_Analysis:_

The data shows that, on average, each song has about 514 million streams, but the median has 291 million streams. This suggests that a some songs get a huge number of streams, which pulls the average up. The standard deviation of around 566 million then means there’s a lot of variation in stream counts across songs. Essentially, most songs have fewer streams than the average, but a small number of hits have very high counts, creating an uneven spread.

### b.1. What is the distribution of released_year and artist_count?

![image](https://github.com/user-attachments/assets/c4ec5439-8ac9-4da4-a74f-10b25facd439)

_Functions:_

1. **plt.figure(figsize = (5, 5))**

   > Description: This function initializes the figure for the plot with a specific size of 5 inches wide and 5 inches tall.

2. **sns.histplot(data['released_year'], bins = 30, kde = True)**

   > Description: The function **"sns.histplot(data['released_year']"** makes the 'released_year' from the data into a histogram.

   > Description: The parameter **"bins = 30"** determines the number of intervals or "bins" for grouping in years.

   > Description: The parameter **"kde = True"** enables the Kernel Density Curve (KDE) curve.

3. **plt.title('Distribution of Released Year')**

   > Description: This function allows the plot to have a title "Distribution of Released Year".

4. **plt.xlabel('Released Year')**

   > Description: This function labels the x-axis as "Released Year", representing the years in which the tracks were released.

5. **plt.ylabel('Tracks')**

   > Description: This function labels the y-axis as "Tracks", representing the count of tracks released in the specific interval of years.

_Analysis:_ 

It can be observed that as more time progresses, more tracks are being released through the years. A sharp increase during the 2010 and especially after 2020 reflects the growing volume of music releases in recent years, as well as the focus of the dataset on more recent tracks since earlier years have very few tracks. 

---

![image](https://github.com/user-attachments/assets/9ac46539-515f-43ed-a321-ee75d1365f31)

_Functions:_

1. **plt.figure(figsize = (5, 5))**

   > Description: This function initializes the figure for the plot with a specific size of 5 inches wide and 5 inches tall.

2. **sns.histplot(data['artist_count'], bins = 30, kde = True)**

   > Description: The function **"sns.histplot(data['artist_count']"** makes the 'artist_count' from the data into a histogram.

   > Description: The parameter **"bins = 30"** determines the number of intervals or "bins" for grouping in years.

   > Description: The parameter **"kde = True"** enables the Kernel Density Curve (KDE) curve.

3. **plt.title('Distribution of Artist Count')**

   > Description: This function allows the plot to have a title "Distribution of Artist Count".

4. **plt.xlabel('Released Year')**

   > Description: This function labels the x-axis as "Artist Count", representing the years in which the tracks were released.

5. **plt.ylabel('Tracks')**

   > Description: This function labels the y-axis as "Tracks", representing the count of tracks released in the specific interval of years.

_Analysis:_ 

The graph suggests that as the artist count increases, the less tracks are there. This pattern reveals that tracks with solo artist are more dominant in the dateset than those tracks with collaboration of multiple artists. 

### b.2. Are there any noticeable trends or outliers?

![image](https://github.com/user-attachments/assets/c2258254-7856-4385-b9de-46d10a0e3768)

_Functions:_

1. **plt.figure(figsize = (12, 6))**

   > Description: This function initializes the figure for the plot with a specific size of 12 inches wide and 6 inches tall.

2. **sns.boxplot(x=data['released_year'])**

   > Description: This function creates a box plot about the released_year column on the x-axis, representing the distribution of release years for tracks.

3. **plt.title('Boxplot of Released Year')**

   > Description: This function allows the plot to have a title "Boxplot of Released Year".

4. **plt.xlabel('Released Year')**

   > Description: This function labels the x-axis as "Released Year", representing the data on track for release years.

_Analysis:_

As shown in the box plot, multiple outliers are observed. This is because most tracks are from the 2020 and only a few tracks are from the earlier years. The big difference from the number of tracks in the recent years are evidently more compared to the earlier years which cause the outliers.

---

![image](https://github.com/user-attachments/assets/18233901-665e-4b0f-9da5-88c5ef8c6833)

_Functions:_

1. **plt.figure(figsize = (12, 6))**

   > Description: This function initializes the figure for the plot with a specific size of 12 inches wide and 6 inches tall.

2. **sns.boxplot(x=data['artist_count'])**

   > Description: This function creates a box plot about the artist_count column on the x-axis, representing the distribution of artist count for tracks.

3. **plt.title('Boxplot of Artist Count')**

   > Description: This function allows the plot to have a title "Boxplot of Artist Count".

4. **plt.xlabel('Artist Count')**

   > Description: This function labels the x-axis as "Artist Count", representing the data on track for artist count.

_Analysis:_

The box plot shows outliers when there are more than 4 artists, indicating that it is uncommon and that most tracks only have 1-2 artists and a few with 3 artists.

--- 

## Top Performers

In this section, the most streamed tracks and the artists with the most releases are analyzed. Tracks that garnered the highest popularity and the artists who are the most prolific based on the number of tracks they released are identified.

### a. Which track has the highest number of streams? Display the top 5 most streamed tracks.

![image](https://github.com/user-attachments/assets/0c80e445-2a88-4da5-a832-661cf4e551f1)

_Functions:_

1. **data[['track_name', 'streams']].sort_values(by = 'streams', ascending = False).head(5)**

   > Description: The function **"data[['track_name', 'streams']]"** creates a data frame that contains only the 'track_name' and 'streams' columns.

   > Description: The function **".sort_values(by = 'streams', ascending = False)"** sorts the data frame by streams column in descending order due to the 'ascending = False' argument.

   > Description: The function **".head(5)"** returns only the first 5 rows of the sorted data frame.

2. **print()**
  
   > Description: This function prints the statement inside it.

_Analysis:_

The top 5 most streamed tracks are Blinding Lights, Shape of You, Someone You Loved, Dance Monkey, and Sunflower - Spider-Man: Into the Spider-Verse. Accordingly, the track with the highest number of streams is Blinding Lights.

### b. Who are the top 5 most frequent artists based on the number of tracks in the dataset?

![image](https://github.com/user-attachments/assets/92f584e1-968b-4bb0-9c2f-a8ff30fdf6c0)

_Functions:_

1. **top_artists = data['artist(s)_name'].value_counts().head(5)**

   > Description: The function **"data['artist(s)_name']"** accesses the 'artist(s)_name' column.

   > Description: The function **".value_counts()"** counts the occurences of each artist in the column.

   > Description: The function **".head(5)"** returns the first 5 rows of the sorted data frame.

   > All together, they are stored in variable name **"top_artists"**.

2. **for artist, count in top_artists.items():**

   > Description: This function checks the number of tracks the top 5 most frequent artist have through the use of for loop.

3.  **print(artist, ':', count, 'tracks')**
   
      > Description: This function prints the artist name along with the number of tracks they occur.

_Analysis:_

The top 5 most frequent artists based on the number of tracks in the dataset are Taylor Swift with 34 tracks, The Weeknd with 22 tracks, Bad Bunny with 19 Tracks, Sza with 19 tracks, and Harry Styles with 17 tracks.

---

## Temporal Trends

In this part, insights about how music release patterns have changed over time are gained. Moreover, release patterns by month revealed trends such as which months are the tracks typically released. 

### a. Analyze the trends in the number of tracks released over time. Plot the number of tracks released per year.

![image](https://github.com/user-attachments/assets/a5ef3d80-8703-429c-ad04-eddef40ffb6f)

_Functions:_

1. **plt.figure(figsize = (10, 5))**

   > Description: This function initializes the figure for the plot with a specific size of 10 inches wide and 5 inches tall.

2. **tracks_per_year = data['released_year'].value_counts().sort_index()**

   > Description: The function **"data['released_year'].value_counts()"** counts the occurances of each unique year in the 'released_year' column.

   > Description: The function **".sort_index()"**** sorts the series by the release year, ensuring that the years appear in chronological order.

   > All in all, they are stored in variable name **"tracks_per_year"**.

3. **sns.lineplot(x=tracks_per_year.index, y=tracks_per_year.values)**

   > Description: The function **"sns.lineplot"** creates a line plot of the number of tracks released.

   > Description: The function **"x=tracks_per_year.index"** represents the years in chronological order.
   
   > Description: The function **"y=tracks_per_year.values"** represents the number of tracks released for each year in the sorted order.

4. **plt.title('Number of Tracks Released per Year')**

   > Description: This function allows the plot to have a title "Number of Tracks Released per Year".

5. **plt.xlabel('Year')**

   > Description: This function labels the x-axis as "Year", representing the number of released track per year interval.

6. **plt.ylabel('Number of Tracks')**

   > Description: This function labels the y-axis as "Number of Tracks", representing the number of tracks for each year interval.

_Analysis:_

As the graph shows, the number of tracks released per year had a steady increse around 2000, but had a high sharp increase around 2020. This indicates that more tracks were released around 2020 compared to the years before that.

### b. Does the number of tracks released per month follow any noticeable patterns? Which month sees the most releases?

![image](https://github.com/user-attachments/assets/f083cbaa-3c14-49c5-aa08-40e31ff25f82)

_Function:_

1. **plt.figure(figsize = (10, 5))**

   > Description: This function initializes the figure for the plot with a specific size of 10 inches wide and 5 inches tall.

2. **tracks_per_month = data['released_month'].value_counts().sort_index()**

   > Description: The function **"data['released_month'].value_counts()"** counts the occurences of each unique month in the 'released_month' column.
   
   > Description: The function **".sort_index()"** sorts the series by the month, ensuring that the months appear in calendar order.

   > > All in all, they are stored in variable name **"tracks_per_month"**.

3. **sns.barplot(x=tracks_per_month.index, y=tracks_per_month.values)**
   
   > Description: The function **"sns.barplot"** creates a bar plot of the number of tracks released.

   > Description: The function **"x=tracks_per_month.index"** represents the months in chronological order.
   
   > Description: The function **"y=tracks_per_month.values"** represents the number of tracks released in each month.

4. **plt.title('Number of Tracks Released per Month')**

   > Description: This function allows the plot to have a title "Number of Tracks Released per Month".

5. **plt.xlabel('Month')**

   > Description: This function labels the x-axis as "Month", representing the number of released track per month.

6. **plt.ylabel('Number of Tracks')**

   > Description: This function labels the y-axis as "Number of Tracks", representing the number of tracks for each month.

_Analysis:_

As observed, there are no noticeable patterns or trends in the number of tracks released per month. The tracks being released per month just happends to be more in the start of the year which is January and about the mid-year, Summer season, which is May. Accordingly, the month with the most tracks released is during January.

---

## Genre and Music Characteristics

In this part, the relationship between streams and various musical arrtibutues revealed how these can contribute to a track's popularity. Additionally, the correlations between danceability, energy, valence, and acousticness provided insights into how these qualities intereact.

### a. Examine the correlation between streams and musical attributes like bpm, danceability_%, and energy_%. Which attributes seem to influence streams the most?

![image](https://github.com/user-attachments/assets/590fe4de-8f98-46ff-98c6-002544272f1f)

_Functions:_

1. **plt.figure(figsize = (10, 5))**

   > Description: This function initializes the figure for the plot with a specific size of 10 inches wide and 5 inches tall.

2. **sns.heatmap(data[['streams', 'bpm', 'danceability_%', 'energy_%', 'valence_%', 'acousticness_%']].corr(), annot = True, cmap = 'coolwarm', vmin = -1, vmax = 1)**

   > Description: The function **"sns.heatmap(data[['streams', 'bpm', 'danceability_%', 'energy_%', 'valence_%', 'acousticness_%']]"** creates a heatmap from the correlation matrix. Moreover, it only selects the specific columns from the data.
   
   > Description: The function **".corr()"** calculates the correlation matrix from the selected columns.

   > Description: The parameter **"annot = True"** adds the correlation values within each cell of the heatmap.

   > Description: The parameter **"cmap = 'coolwarm'"** specifies the color map used in the heatmap.

   > Description: The functions **"vmin = -1"** and **"vmax = 1"** set the color scale to range from -1 (negative correlation) to 1 (positive correlation).

3. **plt.title("Correlation Matrix of Streams and Musical Attributes")**

   > Description: This function allows the plot to have a title "Correlation Matrix of Streams and Musical Attributes".

_Analysis:_

Examining the correlation matrix, the number of streams does not seem to evidently inluence any specific musical attribute like bpm, danceability, or energy as there is almost no correlation. However, among the musical attributes, the danceability of the track have the most inluence compared to the other attributes as it has the highest correlation to streams.

### b.1. Is there a correlation between danceability_% and energy_%?

![image](https://github.com/user-attachments/assets/7ee443ce-da1b-4aa0-baaf-ce902328bda5)

_Functions:_

1. **plt.figure(figsize = (8, 5))**

   > Description: This function initializes the figure for the plot with a specific size of 8 inches wide and 5 inches tall.

2. **sns.scatterplot(x = 'danceability_%', y = 'energy_%', hue = 'streams', palette = 'viridis', data = data**

   > Description: The function **"sns.scatterplot(x = 'danceability_%', y = 'energy_%')"** creates a scatter plot from the data. It also sets the x-axis to the 'danceablity_%' attribute and the y-axis to the 'energy_%' attribute of the each track.

   > Description: The parameter **"hue = 'streams'"** sets the color according to the 'streams' column.

   > Description: The parameter **"palette = 'viridis'"** defines the color pallate used for the plot.

   > Description: The parameter **"data = data"** specifies which source of data set to be used.

3. **plt.title("Scatter Plot of Danceability % vs. Energy %")**

   > Description: This function allows the plot to have a title "Scatter Plot of Danceability % vs. Energy %".

4. **plt.xlabel("Danceability %")**

   > Description: This function labels the x-axis as "Danceability %", representing the danceability percentage per track.

5. **plt.ylabel("Energy %")**

   > Description: This function labels the y-axis as "Energy %", representing the energy percentage per track.

_Analysis:_

By observing the scatter plot, a slight positive correlation can be induced. This is because points with higher danceability generally appear with higher energy values, but again, the correlation is not strong—there’s a wide spread in values. This suggests that while some tracks may be both highly danceable and energetic, these attributes don’t necessarily increase together in a consistent way.

### b.2. How about valence_% and acousticness_%?

![image](https://github.com/user-attachments/assets/ecf71010-369e-47eb-8d2a-3c203d516510)

1. **plt.figure(figsize = (8, 5))**

   > Description: This function initializes the figure for the plot with a specific size of 8 inches wide and 5 inches tall.

2. **sns.scatterplot(x = 'valence_%', y = 'acousticness_%', hue = 'streams', palette = 'viridis', data = data)**

   > Description: The function **"sns.scatterplot(x = 'valence_%', y = 'acousticness_%')"** creates a scatter plot from the data. It also sets the x-axis to the 'valence_%' attribute and the y-axis to the 'acousticness_%' attribute of the each track.

   > Description: The parameter **"hue = 'streams'"** sets the color according to the 'streams' column.

   > Description: The parameter **"palette = 'viridis'"** defines the color pallate used for the plot.

   > Description: The parameter **"data = data"** specifies which source of data set to be used.

3. **plt.title("Scatter Plot of Valence % vs. Acousticness %")**

   > Description: This function allows the plot to have a title "Scatter Plot of Valence % vs. Acousticness %".

4. **plt.xlabel("Valence %")**

   > Description: This function labels the x-axis as "Valence %", representing the valence percentage per track.

5. **plt.ylabel("Acousticness %")**

   > Description: This function labels the y-axis as "Acousticness %", representing the acousticness percentage per track.

_Analysis:_

From the scatter plot, it appears that there is no strong correlation between Valence % and Acousticness %. This is because the points are widely scattered across the graph without a clear trend. Most tracks, however, seem to have lower Acousticness % values, even at varying levels of Valence.

---

## Platform Popularity

In this section, the number of tracks in Spotify, Deezer, and Apple playlists are compared. By analyzing the playlist counts across platforms, the platform which tends to include more popular tracks are identified. Accordingly, a bar plot is used to analyze the platform popularity.

### a. How do the numbers of tracks in spotify_playlists, deezer_playlist, and apple_playlists compare? Which platform seems to favor the most popular tracks?

![image](https://github.com/user-attachments/assets/8c47be76-28cb-49ad-bca2-701bcc95b572)

_Functions:_

1. **platform_counts = data[['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists']].sum()**

   > Description: The function **"data[['in_spotify_playlists', 'in_deezer_playlists', 'in_apple_playlists']].sum()"** counts the total number of tracks on each platform and are added.

   > All together, they are stored in variable **"pkatform_counts"**.

2. **plt.figure(figsize=(8, 5))**

   > Description: This function initializes the figure for the plot with a specific size of 8 inches wide and 5 inches tall.

3. **sns.barplot(x=platform_counts.index, y=platform_counts.values)**

   > Description: The function **"sns.barplot()"** creates a bar plot from the data.

   > Description: The function **"x=platform_counts.index"** displays the total number of tracks for each platform's playlist on the x-axis

   > Description: The function "**y=platform_counts.values"** counts the number of tracks on each platform are set on the y-axis. These count values are represented by the height of each bar (one for each platform).

4. **plt.title("Platform Popularity Comparison")**

   > Description: This function allows the plot to have a title "Platform Popularity Comparison".

5. **plt.xlabel("Platform")**

   > Description: This function labels the x-axis as "Platform", representing the platforms.

6. **plt.ylabel("Number of Tracks")**

   > Description: This function labels the y-axis as "Number of Tracks", representing the number of tracks per platform playlist.

_Analysis:_

By observation, there is a big difference between the number of tracks across spotify_playlists, deezer_playlist, and apple_playlists. The Spotify platform contain a high number of tracks in playlists than both Deezer and Apple combined. Accordingly the platform that seems to favor the most popular tracks is Spotify.

---

## Advanced Analysis

In this last part, musical features like key and mode are examined to see whether there are preferences for certain tonalities. Moreover, genre and occurences of artist in playlists or charts are observed to help identify which genre or artist have a stronger platform presence.

### a. Based on the streams data, can you identify any patterns among tracks with the same key or mode (Major vs. Minor)?

![image](https://github.com/user-attachments/assets/e62c7fc9-ea6c-4e5e-998f-a98d292f726d)

_Functions:_

1. **avg_streams_by_key = data.groupby('key')['streams'].mean().reset_index()**

   > Description: The function **"data.groupby('key')['streams']"** represents the musical key of each track and computes the average number of streams for each distinct musical key.

   > Description: The function **".mean()"** calculates the mean (average) number of streams for each musical key.

   > Description: The function ".reset_index()" cleans data set where the musical key and the corresponding average streams are both columns.

2. **graphkey_data = avg_streams_by_key**

   > Description: This funcion assigns the **"avg_streams_by_key"** to a variable **"graphkey_data"**.

3. **"graphkey_data['key'] = avg_streams_by_key['key'].astype(str)"**

   > Description: The function **".astype(str)"** converts the data type of the 'key' column from its current type to string. 

4. **plt.figure(figsize=(8, 5))**

   > Description: This function initializes the figure for the plot with a specific size of 8 inches wide and 5 inches tall.

5. **sns.barplot(data=avg_streams_by_key, x='key', y='streams')**

   > Description: The function **"sns.barplot(data=avg_streams_by_key"** creates a bar plot about the data set stored in **"avg_streams_by_key"**.

   > Description: The function **"x='key'"** specifies the column from avg_streams_by_key to be used for the x-axis, representing the different musical keys.

   > Description: The function **"y='streams'"** specifies the column from avg_streams_by_key to be used for the y-axis, representing the average number of streams for each key.

6. **plt.title("Average Streams by Key")**

   > Description: This function allows the plot to have a title "Average Streams by Key".

7. **plt.xlabel("Key")**

   > Description: This function labels the x-axis as "Key", representing the keys.

8. **plt.ylabel("Average Streams")**

   > Description: This function labels the y-axis as "Average Streams", representing the number of tracks per key.

_Analysis:_

Based on the bar plot, there are no evident patterns among the tracks. However, it can be observed that sharper keys tend to have higher average streams compared to its base keys. It also noticeable that the C# key has the most average keys.

---

![image](https://github.com/user-attachments/assets/ac52e3c9-2303-49c9-ba60-4322e617a0d0)

_Functions:_

1. **streams_by_mode = data.groupby('mode')['streams'].mean().reset_index()**

   > Description: The function **"data.groupby('mode')['streams']"** represents the mode of each track and computes the average number of streams for each mode.

   > Description: The function **".mean()"** calculates the mean (average) number of streams for each mode.

   > Description: The function ".reset_index()" cleans data set where the mode and the corresponding average streams are both columns. 

32. **plt.figure(figsize=(8, 5))**

   > Definition: This function initializes the figure for the plot with a specific size of 8 inches wide and 5 inches tall.

3. **sns.barplot(data=streams_by_mode, x='mode', y='streams')**

   > Description: The function **"sns.barplot(data=streams_by_mode"** creates a bar plot about the data set stored in **"streams_by_mode"**.

   > Description: The function **"x='mode'"** specifies the column from streams_by_mode to be used for the x-axis, representing the modes.

   > Description: The function **"y='streams'"** specifies the column from streams_by_mode to be used for the y-axis, representing the average number of streams for each mode. 

4. **plt.title("Average Streams by Mode (Major vs. Minor)")**

   > Description: This function allows the plot to have a title "Average Streams by Mode (Major vs. Minor)".

5. **plt.xlabel("Mode")**

   > Description: This function labels the x-axis as "Mode", representing the mode (Major or Minor).

6. **plt.ylabel("Average Streams")**

   > Description: This function labels the y-axis as "Average Streams", representing the number of tracks per mode.

_Analysis:_

Based on the bar plot, Minor mode are more streamed compared to Major mode. In other words, people tend to enjoy more somber emotional quality of music than bright and happy ones.

### b. Do certain genres or artists consistently appear in more playlists or charts? Perform an analysis to compare the most frequently appearing artists in playlists or charts.

![image](https://github.com/user-attachments/assets/2d5aff7f-9edb-402e-bb7c-56017249607a)

_Functions:_

1. **artist_playlist_counts = data['artist(s)_name'].value_counts().reset_index()**

   > Description: The function **"data['artist(s)_name']"** contains the names of the artists.

   > Description: The function **".value_counts()"** counts how many times each unique value appears in a specified column.
   
   > Description: The function **".reset_index()"** used to reset the index of the resulting Series from value_counts().

   > All together, they are stored in variable **"artist_playlist_counts"**

2. **artist_playlist_counts.columns = ['artist', 'playlist_count']**

   > Description: The function **".columns"** refers to the column names of the data.

3. **top_artists_playlists = artist_playlist_counts.head(10)**

   > Description: The function **"artist_playlist_counts"** contains data about artists and how many playlists they are featured in.

   > Description: The function **".head(10)"** returns the first 10 rows of the artist_playlist_counts.

   > All together, they are stored in variable **"top_artists_playlists"**.

4. **plt.figure(figsize=(12, 6))**

   > Description: This function initializes the figure for the plot with a specific size of 12 inches wide and 6 inches tall.

5. **sns.barplot(x='playlist_count', y='artist', data=top_artists_playlists)**

   > Description: The function **"sns.barplot()"** creates a bar plot about the **top_artists_playlists**.

   > Description: The function **"x='playlist_count'"** represents how many playlists the artist’s tracks appear in.

   > Description: The function **"y='artist'"** represents the artists.

   > Description: The function **"data=top_artists_playlists"** defines the data source for the plot.

6. **plt.title('Top 10 Artists by Playlist Appearances')**

   > Description: This function allows the plot to have a title "Top 10 Artists by Playlist Appearances".
   
7. **plt.xlabel('Number of Playlists')**

   > Description: This function labels the x-axis as "Number of Playlists", representing the number of playlists per artist.

8. **plt.ylabel('Artist')**

   > Description: This function labels the y-axis as "Artist", representing the artist.

_Analysis:_

Based on the bar plot, certain genres or artists do consistently appear in more playlists or charts as they have multiple tracks on the data set provided. Accordingly, the most frequently appearing artists in playlists or charts would be Taylor Swift with around 34 tracks. 

---

## Recommendation

After performing analyzations and through observations, there seems to be missing data in the data set. The missing data could affect the result or how some results could be interpreted; thus, the recommendation would be to fill or research the missing values as it could greatly affect interpretations. Additional insights on what makes a track popular would be the artists. Some artists in the data set are well-known and being famous greatly affects the popularity of a track as more people or fans would listen to it. Moreover, tracks mostly streamed are in these recent years, especially 2020, as through time, naturally, musical trends shift and tracks are being made based on that so people would stream it more.
