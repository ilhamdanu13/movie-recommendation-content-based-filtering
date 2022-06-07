# Movie Recommendation with Content Based Filtering
Unlike demographic filtering, content based filtering considers every elements in the movies before recommend them to the users, such as the movies’ descriptions, genres, casts, crews, etc. This way, the users will more likely to receive recommendations that are more aligned with their favorite movies.

![image](https://user-images.githubusercontent.com/86812576/172357550-a671dd08-b4e6-48a9-b8b4-662586d017ff.png)

what will be done is, if the user selects a movie, it will check the synopsis of the movie, then use document search to select another movie based on the similarity of the synopsis.

# Content: Movies's synopsis / overview
# Import Data
The dataset used is movies data which consists of 41362 rows and 2 columns.

# Import Package
import packages:
- import pandas as pd
- from sklearn.feature_extraction.text import CountVectorizer
- from nltk.tokenize import word_tokenize
- from sklearn.metrics.pairwise import cosine_distances
- from luwiji.recommendation_system import illustration

# Encode All Synopsis using Bag of Words
Before that, I will encode all synopsis data into a bank, to make it easier to find similarities.

# Step 1: Encode what user watch

![image](https://user-images.githubusercontent.com/86812576/172361923-27f54d2b-47aa-4086-85d3-404aad4980d9.png)

In step 1, perform a transform using the bag of words on the 'content' variable which contains the 'overview' of the index data.

# Step 2: Document search

in step 2, what is done is to look for similarities from all synopsis, and the technique is to find the smallest distance. Then sort by index which is the smallest distance, previously the initial example was index 0 (Toy Story).

# Step 3: Recommend
The results of the recommendations can be seen, that the most similar Toy Story (index 0) movie based on the synopsis is as follows.

![image](https://user-images.githubusercontent.com/86812576/172363479-db07b300-90ae-452e-8407-02472a0590d8.png)

Actually, content based filtering has a weakness, namely the content itself. if we look at the 3rd line recommendation movie, The 40 Year Old Virgin, there is no resemblance in the contents of the movie. It's just that in The 40 Year Old Virgin, there is the word 'Andy' which is also a character in the movie which is also found in the Toy Story movie. This is what makes the recommendation system put the movie on the recommendation list. 

Looks like content-based recommendations don't work very well. If only based on the 'overview' is actually not enough to give a recommendation so it must be more specific what content is used as a measure.

# Content: Multiple information -> Metadata soup
