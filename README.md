MOVIE RECOMMENDATION SYSTEM
=============================

OVERVIEW
--------
This project implements an item-based collaborative filtering recommender
system that suggests movies similar to a given movie, based on user rating
patterns. It uses correlation-based similarity between movies computed from
a user-movie rating matrix.

WORKFLOW
--------
1. Data Loading
   - Load movie metadata (movies_dataset_unique.csv) and user ratings
     (ratings_dataset.csv).
   - Drop the "genres" column from the movies dataset (not used in this
     approach).

2. Common Movies Exploration
   - A helper function, find_common_movies(user1, user2), identifies movies
     rated by both users, merging their ratings and joining with movie
     titles for inspection.

3. Data Cleaning
   - Duplicate userId-movieId rating pairs are removed, keeping the highest
     rating per pair.

4. User-Movie Rating Matrix
   - Ratings are pivoted into a matrix (movies as rows, users as columns),
     with missing ratings filled as 0.

5. Movie Similarity Computation
   - Pairwise correlation distance is computed between movies based on
     their rating vectors, converted to a similarity score (1 - distance).
   - Results stored in a movie-by-movie similarity matrix (movie_sim_df),
     with self-similarity values zeroed out.

6. Recommendation Function
   - get_similar_movies(movieid, top_n=5) looks up a movie's similarity
     scores against all other movies, returns the top N most similar
     movies along with their titles.

REQUIREMENTS
------------
  pandas
  numpy
  scikit-learn


METHOD & RESULTS
------------------
Item-Based Collaborative Filtering - Movie similarity is derived purely
from patterns in user ratings (not movie content/genre), using Pearson
correlation distance between each pair of movies' rating vectors across
all users. Movies that tend to be rated similarly by the same users are
considered more similar.

Recommendation Output - Given a movieId, the system returns the top N
movies with the highest similarity score, along with their titles,
providing a straightforward "users who liked this also liked..." style
recommendation.


LICENSE
-------
This project is for educational purposes.
