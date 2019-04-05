# ISOC631
Repository for ISOC631 about tweepy on Python 

Made with @WilliamBurillon 

Introduction

This report will explain the different steps used in the TP1 (Twitter API and Database)
and 2 (Open Street Map). We have discovered in more detail the notion of API and
deepened our knowledge on database. We will present those in chronological order,
like we have proceeded. 

1. Retrieve tweets with Twitter API: Tweepy (twitter_streaming.py)

The first step has consisted of retrieve tweets with the keywords “HIV”, “VIH”, “AIDS
” on a Json file. For that, we have used Python and the package for
Twitter API: Tweepy.
So, let’s talk about the Python code and the way that we have used the Twitter API.
We have used the streaming API to catch the tweets and return them into JSON
format. To reduce the number of tweets, we have used a filter with the track
parameter, to track the tweets related to the HIV subject. So, the API scan the tweet
in real time and detect the tweets related to the keywords. There are two kinds
of tweet:
• tweets in direct relation with the keywords. In other words, the API checks if
one of the keywords appear in the “text” tag of the tweet JSON file.
• tweets which are indirectly in relation with the keywords. there are the tweets
which respond to another tweet and this tweet mentioned one of the keywords.
So, we can say that these tweets are still in relation with the subject.
To store the tweets that meet criteria for the project, we have filtered another time the
tweets and we have decided to only keep the tweets with GPS data. Then, we have
decided to store this data into a file which is structured as list of JSON. So, we can
easily use it to put into our database.

2. Upload data received on a local Database (uploadSQL.py)

The next step has consisted of upload data in our json file on a local database (it’s
the same processes for upload on database on server). So, for that, we have used a
Python program. We have imported as usually 2 packages: json
and MySQL.connector for database connection. To use it you must create a local
database (personally we have used PhpMyAdmin). We have created a class with
4 functions that work on your new local database:
    • CreateTable : it creates a new table called “Tweets” on your database with 7
    attributes (id : the id of the tweet, name: the name of the tweet, text: the content of
    the tweet, quoted_status_text: the content of the quoted tweet, creation_date:
    creation date of the tweet, position_X: longitude on a map of the tweet
    broadcaster, position_Y: latitude)
    • RemoveTable: it deletes the table called “Tweets” if it exists.
    • FillTable: it uploads data on json file on your new table and on all of these
    attributes if it exists.
    • CleanTable: it resets the table.

We have met several difficulties for this program. First, the methods for read json and for write on database have been difficult to master. Next, we have had to solve the encoding problem: the json file has been written in utf-8 encoding. It’s not a problem for reading on Python but the upload on database can’t support emoticons in names and comments. So, we have solved that by removing these emoticons with a little piece of code.

3. Localization on Open Street Map (testfolium.py and map.html)

For the beginning, we have chosen to used Java Script to realize this part. But after several days of trying without success, we have changed and decided to use Python. With a little program, we could create a html file which include a map with many markers, referenced to the tweeter broadcaster position. We have had to import the package “folium” and create a map with Open Street Map. Finally, we have just added cursor on the map with the coordinates on the database.

4. Get city name and coordinates with polygon (findCity.py)

For that final part, we have tried to get city name and coordinates of a city with the packages geopy and overpy. We have made 4 functions :
• getCityName : take coordinate_X and coordinate_Y in parameter, and return the name of the city of the coordinates (if it exists).
• get_Id : take the name of a city in parameter and return its Id in map.
• get_center_coordinate : take the name of a city in parameter and return the coordinates of the center of the city.
• get_polygone : take an id of a city in parameter and return in a list all of the points that create the polygon of the city.

Conclusion

To conclude, we have found several results for these programs. The most interesting is the third where we can create a map with many points. Thanks to it, we can see the impact of a subject in the world and in the same time the lack of importance of this subject in several countries.

