# Machine Learning Project Report - Endricho Abednego

## Project Overview

Watching movies is a form of entertainment highly favored by many due to the vast selection of available categories or *genres*. Ranging from horror, comedy, action, and drama, to documentaries. Many films serve not only as mere entertainment; sometimes, there are films with hidden meanings about life, or films that can increase our knowledge in various aspects. However, every person's preferences and movie-watching habits are undoubtedly different. Some people view movies strictly as entertainment, while others use them as a learning reference media.

The tendency for people who have found movies that suit them is to usually revolve around those same categories. From this tendency, a recommendation system can be created to suggest movies based on habits and preferences, helping users find films they might like. This recommendation system is used to save time in deciding what movie to watch, as finding a suitable movie can sometimes take a long time, wasting valuable time [1]. This system can be applied and would be very profitable for applications providing film or TV series *streaming* services.

## Business Understanding

This project is built for a society with the following business characteristics:
+ A society with a high interest in watching movies.
+ Users of film or TV series *streaming* service applications.
+ Developer companies of film or TV series *streaming* service applications.

### Problem Statements

+ What features are contained within a film identification?
+ How to build a movie-based recommendation system that is accurate and effective?
+ What steps need to be taken to prepare the data so it can be trained well by the model?

### Goals

+ To know what features are contained within a film identification.
+ To build a recommendation system using *Content-Based Filtering* and *Bag of Words* approaches.
+ To perform *Data Preparation* before inputting data into the model for the training process.

### Solution Statements
+ The features contained in a dataset, and in this case, a film, can detail the components or *columns* existing in the dataset itself. In this case: *Movie_id, title, Genres, release_date, Keywords, overview, poster_path, Budget, Revenue, popularity, vote_average, vote_count, Unnamed:0_y, Cast, and Crew*. Performing data visualization can also help in understanding the data better.
+ To build a recommendation system that can show several movies with concepts, categories, and stories similar to movies watched previously, *Content-Based Filtering* and *Bag of Words* approaches can be applied. The *Content-Based Filtering* approach utilizes the main features of a movie watched previously, such as title, synopsis, and popularity. Meanwhile, the *Bag of Words* approach converts text data into vectors; simply put, this method counts the frequency of word occurrences in a dataset.
+ In the dataset used for this project, there are several data points with null or NaN values. Therefore, normalization needs to be performed for the null values.

## Data Understanding
The dataset used is the *TMDB 10000 Movies Dataset*. This dataset is taken from Kaggle and can be downloaded via the following link [*TMDB 10000 Movies Dataset*](https://www.kaggle.com/datasets/gazu468/tmdb-10000-movies-dataset).

### Detailed Information regarding the dataset
+ Contains approximately 10,000 movie data points along with other detailed information such as titles, cast, *genres*, and much more.
+ Contains data with NaN values, so data normalization is required.
+ There are two files: 10000 Credits Data and 10000 Movies Data.

### Features of the Dataset
10000 Movies Data:
+ *Movie_id* = Unique code for each film
+ *title* = Film Title
+ *Genres* = *Genre* or film category
+ *release_date* = Film release date
+ *Keywords* = Keywords for the film
+ *overview* = Film synopsis
+ *poster_path* = *path* for the film poster
+ *Budget* = Total cost incurred for making the film
+ *Revenue* = Income from the film
+ *popularity* = Film popularity
+ *vote_average* = Average vote score obtained for the film
+ *vote_count* = Number of votes obtained for the film

10000 Credits Data:
+ *Movie_id* = Unique code for each film
+ *title* = Film Title
+ *Cast* = Actors/actresses in the film
+ *Crew* = People tasked with the film production process such as Directors, Writers, etc.

## Data Preparation
+ **Download Dataset**
  To download the dataset, it is necessary to import the dataset from Kaggle via the link above using the Kaggle API by uploading the kaggle.json file as an API key into the notebook.
+ **ZIP Extraction**
  After the dataset is successfully downloaded, file extraction is still required because the downloaded file is in .zip format. After extraction or *unzipping* is performed, the dataset can be used.
+ **Merge Dataset**
  In this dataset, there are two files, so a dataset *merge* is required because this project needs both files for building the recommendation system. The *merge* process is done using the `merge()` function.
+ **Dataset Normalization**
  Because there are some empty values in this dataset, a normalization process is required by filling in the data that has null values and replacing them with empty strings by calling the `fillna()` function.

## Modeling
+ **Content-Based Filtering**
  This recommendation system will use the *Content-Based Learning* approach.
  Initially, the process involves importing the *TFIdfVectorizer* function. Then, initialization of the function will be done by declaring the variable `tfVect`. This function is used to find important features of each film category. Then, in the *TfIdfVectorizer* function initialization process, the *stop_words* parameter will be inserted to avoid common words based on English; this is also a way to perform data normalization. After that, the model needs to be transformed into a matrix form using the `todense()` function. Then, the *similarity degree* calculation will be performed using the *cosine similarity* technique. The calculation formula used is as follows:
  ![RumusCosineSimilarity](https://github.com/endrichoabednego/Dicoding-Academy/blob/main/GambarTerapan1/cosine-similarity-1.png?raw=true)
  Figure 1. *Cosine Similarity Formula*

  The formula is used to calculate the numerical quantity indicating the similarity between films.

+ **Bag of Words**
  This approach takes documents as input and breaks them down into words. These words can be called tokens, and the process is called tokenization.
  Unique tokens collected from all processed documents form an ordered vocabulary. Finally, for each document, a vector of length equal to the vocabulary size is generated with values representing the frequency of tokens appearing in that document.

## Result
+ The following are the recommendation results of the *Content-Based Filtering* model:
----

+ Example model output with input "Batman Begins"
  |   | title	|
  |---|:---|
  |0  |Batman: Bad Blood|
  |1  |	Batman: The Dark Knight Returns, Part 1|
  |2  |	Batman: Mask of the Phantasm|
  |3  |	The Batman|
  |4  |	Batman|
  |5  |	Batman|
  |6  | 	Batman: Year One|
  |7  |	The Lego Batman Movie|
  |8  |	Batman: Hush|
  |9  |	Batman: Gotham by Gaslight|
  |10 |	Batman: Gotham Knight|
  |11 | 	Batman: Mystery of the Batwoman|
  |12 |	Wayne's World|
  |13 |	Batman: Under the Red Hood|
  |14 |	The Dark Knight Rises|
  |15 | 	Batman: The Long Halloween, Part Two|
  Table 1. *Content-Based Filtering* model output

  It can be seen from the table above that the model using the *Content-Based Filtering* approach has displayed several recommendations from the input film titled *Batman Begins*. All films in the output are films that have a synopsis similar to the input film.

+ The following are the recommendation results of the *Bag of Words* model:
+ Example model output with input "Batman Begins"
  | title	|
  |---|
  |The Dark Knight|
  |	The Batman|
  |	Batman: Bad Blood|
  |	Batman|
  |	The Raid 2|
  |	Batman: Under the Red Hood|
  | Spider-Man : Homecoming|
  |	Don|
  |	The Dark Knight Rises|
  |	Pain and Glory|
  |	The Heir Apparent: Largo Winch|
  | Sorry If I Call You Love|
  |	Batman: Gotham by Gaslight|
  |	Batman: The Dark Knight Returns, Part 1|
  |	Twelve|
  | 	Sound of Metal|
  Table 2. *Bag of Words* model output

  It can be seen from the table above that the model using the *Bag of Words* approach has displayed several recommendations from the input film titled *Batman Begins*. All films in the output have a word count calculation that is similar in the 'tags' table.

## Evaluation
The evaluation metric used for both algorithm models, *Content-Based Filtering* and *Bag of Words*, is *precision*. For the *precision* calculation process, it can be done manually using the formula as follows:
![rumusPrecision](https://github.com/endrichoabednego/Dicoding-Academy/blob/main/GambarTerapan1/R.png?raw=true)
Figure 2. *Precision* Formula

For the model using the *Content-Based Filtering* approach, it has a precision result with a perfect score of 100%, while the *Bag of Words* approach was only able to obtain a precision score of 73%. This shows that in this recommendation system project using this dataset, the better approach is *Content-Based Filtering*. This can happen because the characteristics of a film are more clearly visible in the film synopsis, and that is what is searched for similarity in *Content-Based Filtering*, whereas *Bag of Words* may have lower accuracy because, for this approach, the model only counts the number of unique tokens in a 'tags' document then compares them and looks for similarities with films in the dataset.

## Conclusion
From the results obtained from both models, it can be concluded that in the recommendation system project using the [*TMDB 10000 Movies Dataset*](https://www.kaggle.com/datasets/gazu468/tmdb-10000-movies-dataset), better recommendation results will be obtained when using the *Content-Based Filtering* approach.

## References

[1] S. Agrawal and P. Jain, "An improved approach for movie recommendation system," 2017 International Conference on I-SMAC (IoT in Social, Mobile, Analytics and Cloud) (I-SMAC), 2017, pp. 336-342, doi: 10.1109/I-SMAC.2017.8058367.
