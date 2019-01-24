# Goal
To build a recommendation system that can recommend beers based on previous user's ratings from beeradvocate.com.

# Overview
The craft beer scene has exploded in recent years with microbreweries and major beer suppliers now consistently making 
new kinds of beer on a daily basis. This has led to a lot of confusion when trying to pick out a beer that you like. And
this can be difficult for a casual beer drinker or even for those that consider themselves beer connoisseurs. There are
several apps and websites now solely dedicated to ranking and classifying beers. Whether the point is to help an individual
remember what they liked and didn't like or to help others discover new beers it is worthwhile to explore the reviews given
to try and predict new kinds of beers that an individual would like.

This project uses data scraped from [beeradvocate.com](https://www.beeradvocate.com/) using Beautiful Soup, where users
create profiles and are able to rate any beer they try on a scale of 1 to 5. This site uses a [rating](https://www.beeradvocate.com/community/threads/how-to-review-a-beer.241156/)
system that allows for users to take multiple factors in to consideration during their rating process that everyone can
relate.

# Dataset
The initial factor that we looked at were which users to collect data from. The website breaks reviews down in to five different
sections: recent reviews, top reviews for the last year, top reviews of all time, most popular reviews, and a beer hall of 
fame reviews. We decided to take a small section of users from each category to try and catch a variety of different users
in terms of types of beers, frequency, and variety that we could sample from.

Using Beautiful Soup we were able to scrape user's profiles and create a sparse matrix for 2,682 users that resulted in 32,917
different beers that were reviewed. This totalled 86,133 reviews amongst all users that were collected.

![alt text](https://github.com/scbronder/beer_recommendations/blob/master/Screen%20Shot%202019-01-24%20at%208.53.14%20AM.png)


Next we created a beer matrix that included the name of the beer,  ABV, brewery, and type of the beer.

![alt text](https://github.com/scbronder/beer_recommendations/blob/master/Screen%20Shot%202019-01-24%20at%209.05.38%20AM.png)

# Data Processing
Now that we had all of our data we had to normalize the results. We extracted all of the values from the sparse matrix and 
subtracted the average from each column from each of the populated values. From there we created a were able to run a 
Single Value Decomposition (SVD) using the scipy.sparse.linalg library. This applies a linear transformation using the sigma
matrix as weights for the transformation. 
