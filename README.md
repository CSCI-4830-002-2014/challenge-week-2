# Name

Justin McBride

# How many points have you earned?

100/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Doctoring devices](http://www.economist.com/news/technology-quarterly/21615070-easy-access-technology-and-lower-cost-entry-are-creating-crowd-startups)

# Checkpoints

## Checkpoint 1 (5 points)

![image](checkpoint1.png?raw=true)

## Checkpoint 2 (5 points)

![image](checkpoint2.png?raw=true)

## Checkpoint 3 (5 points)

![image](checkpoint3.png?raw=true)

## Checkpoint 4 (5 points)

![image](checkpoint4.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

The differing www1, www2, www3 hostnames refer to the server that the data is coming from. Internal server management differentiates the servers using this prefix.

### Q2. (3 points)

This addition in the search query ensures that we're only looking at succesful queries to the server, and not transactions that may have been in progress but failed, and other similar situtations.

### Q3. (3 points)

We use the pipe to be able to perform searches upon larger search result sets, and it kind of seems like a replacement, or at least complement, to a logical join.

### Q4. (3 points)

Server logs may be the only thing recoverable after server crashes or accidental database destruction. The raw info we obtain can rebuild the database. Additionally, sometimes structured databases can become slow and too full of data to be effective.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](ch1a.png?raw=true)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count | rename count as "Events"
```
![image](ch1b.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count, count(eval(action="purchase")) as "Purchases" | rename count as "Events"
```
![image](ch1c.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count, count(eval(action="purchase")) as "Purchases", count(eval(action="remove")) as "Remove", count(eval(action="addtocart")) as "Added" | rename count as "Events"
```
![image](ch1d.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](ch1e.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](ch1f.png?raw=true)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX
```
![image](ch1g.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX, min(bytes) as MIN, avg(bytes) as AVG
```
![image](ch1h.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId) as "Number of unique products", values(productId) as "Unique Product IDs"
```
![image](ch1i.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | table clientip, action, productId, date_month, date_mday, date_wday
```
![image](ch2a.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | table clientip, action, productId, date_month, date_mday, date_wday | top date_wday limit=3
```
![image](ch2b.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](ch2c.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday="friday" | table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](ch2d.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do date_wday="friday" action="purchase" | table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](ch2e.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action="purchase" | table clientip, action, productId, date_month, date_mday, date_wday | top productId limit=1
```
![image](ch2f.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do action="purchase" | table clientip, action, productId, date_month, date_mday, date_wday | top productId by date_wday limit=1
```
![image](ch2g.png?raw=true)

## Challenge 3-a (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 3-b (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 3-c (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 3-d (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 3-e (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 3-f (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 3-g (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 3-h (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 3-i (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 4-a (4 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 4-b (4 points)
```
sourcetype=access_* [fill-in-the-rest]
