# Name

Manpreet Singh

# How many points have you earned?

0/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[title-of-the-article] http://makezine.com/projects/smart-remote-control/

# Checkpoints

## Checkpoint 1 (5 points)

![Imgur](http://i.imgur.com/zXvwRM4.png)

## Checkpoint 2 (5 points)

![Imgur](http://i.imgur.com/KbEOhg2)

## Checkpoint 3 (5 points)

![Imgur](http://i.imgur.com/El0FY55)

## Checkpoint 4 (5 points)

![Imgur](http://i.imgur.com/6q4J3D9)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

The three names probably represent three different servers. There are three of these because having multiple servers helps in case of heavy traffic.

### Q2. (3 points)

Including “status=200” in queries helps ensure that only thse results are retrned which represent successfully completed transactions.

### Q3. (3 points)

Using the pipe operator in queries helps in cases where the search parameters are either unknown or variable, and need information from the results of another query etc. The alternative would be to run a search, use the results of that search for another query and so  on. This would take a lot of time and would be prone to error.

### Q4. (3 points)

Saving all the product purchase behavior in sructural databases would lead to a huge and slow-to-traverse database, which is highly undesirable. Also

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count 
```
![Imgur](http://i.imgur.com/jqHknYi.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
![Imgur](http://i.imgur.com/34tb0ly)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) AS "Purchases"
```
![Imgur](http://i.imgur.com/vNzTbtL)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) as "Purchases", count(eval(action="addtocart")) as "AddToCarts", count(eval(action="remove")) as "Removes"
```
![Imgur](http://i.imgur.com/4EST5Rd)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![Imgur](http://i.imgur.com/EvyCDcJ)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![Imgur](http://i.imgur.com/iO9jIVc)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX"
```
![Imgur](http://i.imgur.com/UUdzUc9)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX", min(bytes) AS "MIN", avg(bytes) AS "AVG"
```
![Imgur](http://i.imgur.com/JYucKJk)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId) as "NumberofUniqueProducts", values(productId) as "UniqueProductIds"
```
![Imgur](http://i.imgur.com/wK6SWeB)


## Challenge 2-a (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

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
