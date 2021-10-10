# Plot-based-Movie-Data
Movie lovers have been trying to find movies based on its story irrespective of movie genre. We can see this among user search queries in different platforms like google, youtube, bing etc. So I have collected all such user queries which begins with "movies where" from online search engine service websites : https://soovle.com/ , https://answerthepublic.com/ 

# plot-wise-searches.csv
This file consists of combined data collected from the soovle, answerthepublic website and a small preprocessing over it.
Now each of these plots are searched in google using web scraping in python and all the links which begin with “https://www.imdb.com/list” in the obtained google search result page are obtained. And each of the obtained hyperlink to the imdb's movie list page is accesed again using BeautifulSoup in python to get the details of the movies in the respective lists.

# plot-movies-list.csv
This file consists of details about each movie list scraped form imdb. IMDB url to movie list page, list of movie id's and plot-aspects which relate to the respective movie list.


# moviedata.csv
This file consists of all the movie details obtained from imdb along with the plot-aspect from which it is found. There is a column 'topics' in this dataset which is not scraped but assigned to the movie with machine learning.
