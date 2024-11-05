# Most Streamed Spotify Songs 2023

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
  
   > Description: This function prints the output inside it.

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

3.  **print()**
  
   > Description: This function prints the output inside it.

_Analysis:_

There are missing values in some columns, such as 1 is missing for streams, 50 are missing for in_shazam_charts, and 95 are missing in key. Accordingly, these missing values may affect how the data could be interpreted as a different interpretation may be concluded.

---

## Basic Descriptive Statistics

In this section, insights into the dataset's numerical and categorical features are extracted. By understanding central tendencies in the streams column and exploring distributions of released_year and artist_count, potential trends or outliers are identified.

### a. What are the mean, median, and standard deviation of the streams column?










