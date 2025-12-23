### Questions

1. Find five random `user` nodes

MATCH (u:User)
RETURN u
ORDER BY rand()
LIMIT 5

2. Find five random `FOLLOWS` relationships

MATCH ()-[r:FOLLOWS]->()
RETURN r
ORDER BY rand()
LIMIT 5

3. Find the text property of three random Tweet nodes

MATCH (t:Tweet)
RETURN t.text
ORDER BY rand()
LIMIT 3

4. Generate a Cypher statement to visualize sample RETWEETS relationships

MATCH path = (retweet:Tweet)-[r:RETWEETS]->(original:Tweet)
RETURN path

5. Why using merge and not create ?

`MERGE` in Cypher is used when you want to ensure that a specific pattern (node or relationship) exists exactly once, behaving like an “upsert” that matches existing data or creates it if missing. It combines the semantics of matching and creating in a single clause, which avoids duplicates and allows you to distinguish between the first insertion and subsequent updates via `ON CREATE` and `ON MATCH` clauses. By contrast, `CREATE` blindly inserts new nodes or relationships every time the query runs, which is simpler and usually faster but will happily produce duplicates if you run it multiple times with the same data.

6. Calculate the ratio of missing values for the createdAt node property of the Tweet nodes

MATCH (t:Tweet)
WITH count(t) AS total_tweets,
     count(t.createdAt) AS tweets_with_createdAt
RETURN 
  total_tweets,
  tweets_with_createdAt,
  total_tweets - tweets_with_createdAt AS missing_createdAt,
  round(100.0 * (total_tweets - tweets_with_createdAt) / total_tweets, 2) AS missing_percentage

7. Count the number of relationships by their type

MATCH (start)-[r]->(end)
RETURN type(r) AS relationshipType,
       COUNT(r) AS totalCount,
       labels(start)[0] AS fromNodeLabel,
       labels(end)[0] AS toNodeLabel
ORDER BY totalCount DESC

8. Compare the text of an original tweet and its retweet

MATCH (retweet:Tweet)-[r:RETWEETS]->(original:Tweet)
RETURN 
  original.id AS original_id,
  original.text AS original_text,
  retweet.id AS retweet_id,
  retweet.text AS retweet_text
LIMIT 5

9. Calculate the distribution of tweets grouped by year created

MATCH (t:Tweet)
RETURN 
  date(t.createdAt).year AS year,
  count(t) AS tweet_count
ORDER BY year

10. Use the MATCH clause in combination with the WHERE clause to select all the tweets that were created in 2021

MATCH (t:Tweet)
WHERE date(t.createdAt).year = 2021
RETURN t

11. Return the top four days with the highest count of created tweets

MATCH (t:Tweet)
WITH date(t.createdAt) AS day, count(t) AS tweet_count
RETURN day, tweet_count
ORDER BY tweet_count DESC
LIMIT 4

12. Count the number of users who were mentioned but haven’t published a single tweet

MATCH (u:User)
WHERE NOT (u)-[:PUBLISH]->(:Tweet)
  AND (u)<-[:MENTIONS]-(:Tweet)
RETURN count(u) AS mentioned_but_no_tweets

13. Find the top five users with the most distinct tweets retweeted

MATCH (u:User)-[:PUBLISH]->(original:Tweet)<-[:RETWEETS]-(retweet:Tweet)
WITH u, count(DISTINCT original) AS distinct_tweets_retweeted
RETURN 
  u.id,
  u.username,
  distinct_tweets_retweeted
ORDER BY distinct_tweets_retweeted DESC
LIMIT 5

14. Find the top five most mentioned users

MATCH (u:User)<-[:MENTIONS]-(t:Tweet)
WITH u, count(t) AS mention_count
RETURN 
  u.id,
  u.username,
  mention_count
ORDER BY mention_count DESC
LIMIT 5

15. Find the 10 most followed Users

MATCH (u:User)<-[:FOLLOWS]-(follower:User)
WITH u, count(follower) AS follower_count
RETURN 
  u.id,
  u.username,
  follower_count
ORDER BY follower_count DESC
LIMIT 10

16. Find the top 10 users who follow the most people

MATCH (u:User)-[:FOLLOWS]->(following:User)
WITH u, count(following) AS following_count
RETURN 
  u.id,
  u.username,
  following_count
ORDER BY following_count DESC
LIMIT 10