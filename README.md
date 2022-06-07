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

# Improve
# Content: Multiple information -> Metadata soup
Now I will try different content to improve the previous model. Because content based sees the similarity of content, then I will change the content, namely with multiple information.

# Import Data
In this case I use data with more complete features / columns. The dataset consists of 42277 rows and 6 columns. the columns are 'title', 'genres', 'cast', 'keywords', 'director', and the combined column is 'metadata'.

# Recommend
I took two examples of data to see the similarities. The sample data are index data 0 = Toy Story, index data 1 = Jumanji, and index data 579 = Home Alone.

Sample movie Toy Story:

![image](https://user-images.githubusercontent.com/86812576/172399102-8bf20143-e419-4333-b4c5-70fd1416fe05.png)

Sample movie Jumanji:

![image](https://user-images.githubusercontent.com/86812576/172399307-51c1af11-3138-4d1e-9223-77a26f6d66f9.png)

Sample moive Home Alone:

![image](https://user-images.githubusercontent.com/86812576/172399651-2fdd2af2-3260-4765-a2e0-d6967db6178c.png)

It can be seen from the results above that the results of the recommendations are more relevant, it can be seen that there are similarities in the metadata. If you want to improve again, you can add a synopsis/overivew to the metadata.
