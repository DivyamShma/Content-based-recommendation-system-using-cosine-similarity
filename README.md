# Content-based-recommendation-system-using-cosine-similarity
**Dataset link** - https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata
 
**Python 3+ Dependencies** - pandas, numpy, ast, nltk (portstemmer), sklearn (count vectorizer, cosine similarity), jupyter notebook/ VS code

## Project Description 
This project uses nltk to stem all words to their base form and then uses sklearn count vectorizer to convert the words to vectors and use cosine similarity to find the closest movies to the provided movie as input. Once the cosine similarity has been calculated for every movie to every other movie it does not need to run again for recalculating for a new input movie.
 
## Data  cleaning- 
 - use pandas to read the downloaded dataset
 - In the data cleaning block uncomment the following to remove incorrect data entires
   - `movies.drop(axis=0,index=19730,inplace=True)`
   -  `movies.drop(axis=0,index=29503,inplace=True)`
   -   `movies.drop(axis=0,index=35587,inplace=True)`

## Data pre-processing - 
The current version of the model is nerfed, but can easily be brought back to the best performance but then it wil only run on this dataset and not remain universal.

To do that comment out this line `movies  = movies[['id','title','genres']]` and uncomment this `movies = movies[['id','title','overview','genres','keywords','cast','crew']]`

If you made these changes then also make these changes or else you will end up with errors and sad 
  -  uncomment all others in this cell and this as well `movies['genres'] = movies['genres'].apply(lambda x:[i.replace(" ","") for i in x])`
  -  uncomment everything in this cell as well `movies['genres'] = movies['genres'].apply(lambda x:[i.lower() for i in x])`
  -  `movies['tags'] = movies['genres']` comment this and uncomment the other line
  -  Now you can run evrything altogether after you completed the neccesary changes


Then the duplicates and null values are dropped, three functions are defined for pre processing. ast library is used for this as the current data is in form of a string i.e. `'[{"id": 28, "name": "Action"}, {"id": 12, ".....]'` and so on which makes preprocessing cumbersome so just use ast literal_eval for direct conversion of string to list.

Functions fetch_actors, convert, fetch_directors are used to convert this `{"id": 28, "name": "Action"}` to this `["Action']`. I fetched only the first three actors you can choose more if you want and i only fetched director from the crew if you wish to experiment then feel free and if you wish to suggest some improvements then please create pull requests.
