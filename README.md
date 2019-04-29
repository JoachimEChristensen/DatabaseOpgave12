# DatabaseOpgave12

## Exercise 1:
LOAD CSV FROM "file:///some2016UKgeotweets.csv" AS row FIELDTERMINATOR ";"
    
CREATE (:Tweets {username:toString(row[3]), handle:toString(row[4]), residence:toString(row[12]), latitude:toFloat(row[9]), longitude:toFloat(row[10]), body:toString(row[6]), mentions:extract( m in filter(m in split(row[6]," ") where m starts with "@" and size(m) > 1) | right(m,size(m)-1))})

## Exercise 2:

LOAD CSV FROM "file:///some2016UKgeotweets.csv" AS row FIELDTERMINATOR ";"

CREATE (:Tweeters {username:toString(row[3])})

MATCH (a:Tweeters), (b:Tweets)

CREATE (a)-[r:MENTIONS]->(b.mentions)

MATCH (a:Tweeters), (b:Tweets)

CREATE (a)-[r:TWEETED]->(b)

## Exercise 3

Since the question here seems quite unclear, we tried to solve it but not success
