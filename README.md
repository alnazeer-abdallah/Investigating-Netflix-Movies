# Investigating-Netflix-Movies

## Overview
This project aims to explore the netflix_data.csv data to understand more about movies from the 1990s decade.

Netflix! What started in 1997 as a DVD rental service has since exploded into one of the largest entertainment and media companies.

![Investigating-Netflix-Movies Data Col](https://github.com/user-attachments/assets/1a07acfc-3e5a-4a19-a9bd-f934f6a4169e)

What was the most frequent movie duration in the 1990s? Save an approximate answer as an integer called duration (use 1990 as the decade's start year).

## Python Code :

```
# Importing pandas and matplotlib
import pandas as pd
import matplotlib.pyplot as plt

# Read in the Netflix CSV as a DataFrame
netflix_df = pd.read_csv("netflix_data.csv")

# Subset the DataFrame for type "Movie"
netflix_subset = netflix_df[netflix_df["type"] == "Movie"]

# Start by filtering out movies that were released before 1990 and after 2000

movies_1990s = netflix_subset[(netflix_subset["release_year"] >= 1990) & (netflix_subset["release_year"] < 2000)]

# Visualize the duration column of your filtered data to see the distribution of movie durations

plt.hist(movies_1990s["duration"])
plt.title('Distribution of Movie Durations in the 1990s')
plt.xlabel('Duration (minutes)')
plt.ylabel('Number of Movies')
plt.show()

duration = 100
print('The most frequent movie duration in the 1990s is : ' + str(duration) + ' minutes')
```
![Investigating-Netflix-Movies Hist](https://github.com/user-attachments/assets/aedf9d44-87fb-430a-ac44-85931aa6fb0c)

#### The most frequent movie duration in the 1990s is : 100 minutes

A movie is considered short if it is less than 90 minutes. Count the number of short action movies released in the 1990s and save this integer as short_movie_count

## Python Code :

```
# Filter the data again to keep only the Action movies
action_movies_1990s = movies_1990s[movies_1990s["genre"] == "Action"].drop_duplicates()

# Use a for loop and a counter to count how many short action movies there were in the 1990s

# Start the counter
short_movie_count = 0

# Iterate over the labels and rows of the DataFrame and check if the duration is less than 90, if it is, add 1 to the counter, if it isn't, the counter should remain the same
for label, row in action_movies_1990s.iterrows() :
    if row["duration"] < 90 :
        short_movie_count = short_movie_count + 1
    else:
        short_movie_count = short_movie_count

Total_Act_Movies = action_movies_1990s['title'].drop_duplicates().count()
print('Total action movies number is : ' + str(Total_Act_Movies))
print('Short action movies number is : ' + str(short_movie_count))

# A quicker way of counting values in a column is to use .sum() on the desired column
# (action_movies_1990s["duration"] < 90).sum()
```
#### Total action movies number is : 50
#### Short action movies number is : 8

