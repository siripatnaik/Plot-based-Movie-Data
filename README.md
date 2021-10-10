# Plot-based-Movie-Data
Movie lovers have been trying to find movies based on its story irrespective of movie genre. We can see this among user search queries in different platforms like google, youtube, bing etc. So I have collected all such user queries which begins with "movies where" from online search engine service websites : https://soovle.com/ , https://answerthepublic.com/ 

# plot-wise-searches.csv
This file consists of combined data collected from the soovle, answerthepublic website and a small preprocessing over it.
File info:
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 247 entries, 0 to 246
Data columns (total 8 columns):
 #   Column        Non-Null Count  Dtype      Explanation
---  ------        --------------  ----- 
 0   mwindex       247 non-null    int64      index
 1   plot          247 non-null    object     string part after 'movies where' in the user searched query
 2   pos           247 non-null    object     list of tuples where each tuple (lemmatized word, its pos) for every word in plot column
 3   word_count    247 non-null    int64      no.of words in plot column
 4   stopw_count   247 non-null    int64      no.of stopwords in plot column
 5   unique_count  247 non-null    int64      no.of unique words in plot column
 6   plotlemma     247 non-null    object     lemmatized form of plot column
 7   unique_words  247 non-null    object     plotlemma column data without stopwords
dtypes: int64(4), object(4)
memory usage: 15.6+ KB

Now each of these plots are searched in google using web scraping in python and all the links which begin with “https://www.imdb.com/list” in the obtained google search result page are obtained. And each of the obtained hyperlink to the imdb's movie list page is accesed again using BeautifulSoup in python to get the details of the movies in the respective lists.

# plot-movies-list.csv
This file consists of details about each movie list scraped form imdb.
File info:
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 63 entries, 0 to 62
Data columns (total 4 columns):
 #   Column       Non-Null Count  Dtype     Explanation
---  ------       --------------  ----- 
 0   url          63 non-null     object    link to IMDB webpage displaying the public created movie list based on a plot-aspect
 1   plist        63 non-null     object    List of plot-aspects (strings) leading to the webpage in url column
 2   movieidlist  63 non-null     object    List of IMDB movie ID's found in the imdb list (url column)
 3   plotrepr     63 non-null     object    A single plot-aspect which represent all plot-aspects of plist
dtypes: object(4)
memory usage: 2.1+ KB

# moviedata.csv
This file consists of all the movie details obtained from imdb along with the plot-aspect from which it is found
File info:
<class 'pandas.core.frame.DataFrame'>
Index: 2170 entries, tt0012349 to tt13318052
Data columns (total 13 columns):
 #   Column       Non-Null Count  Dtype     Explanation
---  ------       --------------  -----  
 0   plotaspect   2170 non-null   object    set of plot-aspects i.e plist from plot-movies-list.csv where this movie exists in movieidlist
 1   title        2170 non-null   object    Movie Title
 2   year         2170 non-null   object    Movie Released Year
 3   genre        2170 non-null   object    Genre of movie
 4   rating       2168 non-null   float64   Imdb rating of the movie
 5   certificate  2170 non-null   object    Imdb certificate of the movie
 6   runtime      2155 non-null   object     total runtime of movie
 7   miniplot     2170 non-null   object    2-3 line summary of the plot
 8   poster       2170 non-null   object    link to movie poster
 9   plotrepr     2170 non-null   object    plot-aspect i.e plotrepr from plot-movies-list.csv where this movie exists in movieidlist
 10  plotsum      2170 non-null   object    List of plot-summaries (strings) available in imdb website for the movie
 11  votes        2170 non-null   int64     no.of votes for the movie
 12  topics       2170 non-null   object    This is the data assigned to the movie by topic modeling and NLP clustering over words used in plotsum
dtypes: float64(1), int64(1), object(11)
memory usage: 317.3+ KB
