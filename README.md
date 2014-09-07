# Name

Niklas Fejes

# How many points have you earned?

20/100

# Show and tell (10 points)

[title-of-the-article](http://link-to-an-interesting-article-about-a-cool-use-of-arduino)

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

The `www1`, `www2` and `www3` host names are typically used to mirror a site so that
the load balance is distributed over several servers. The `www*` host names on the 
`buttercupgames` website are basically different servers hosting the same site, and that is
why they produce three separate logs.

### Q2. (3 points)

The `status=200` inidicates that only events with HTTP status code 200 (OK) should be
included, which filters out erroneous events from the search.

### Q3. (3 points)

The pipe operator allows for clear distinctions between individual steps in the search. 
It also makes is easier to chain together searches with the available tools 
(`stats`, `top` etc.).

### Q4. (3 points)

The raw server logs may be the only available option if you want to analyze purchases 
for a store that has not yet implemented a structural database. The data from the server
logs can also be used to cross-check a structural database or add information to the
database that has not been saved previously.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](challenge1a.png?raw=true)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
![image](challenge1b.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) AS "Purchases"
```
![image](challenge1c.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) AS "Purchases", count(eval(action="addtocart")) AS "AddToCart", count(eval(action="remove")) AS "Removes"
```
![image](challenge1d.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](challenge1e.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](challenge1e.png?raw=true)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX"
```
![image](challenge1g.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX", min(bytes) AS "MIN", avg(bytes) AS "AVG"
```
![image](challenge1h.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId) AS "NumberOfUniqueProducts", values(productId) AS "UniqueProducts"
```
![image](challenge1i.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top clientip
```
![image](challenge2a.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | top limit=3 date_wday
```
![image](challenge2b.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | top productId
```
![image](challenge2c.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday | top productId
```
![image](challenge2d.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday action=purchase | top productId
```
![image](challenge2e.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action=purchase | top limit=1 productId
```
![image](challenge2f.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do action=purchase | top limit=1 productId by date_wday
```
![image](challenge2g.png?raw=true)

## Challenge 3-a (2 points)
```
```
![image](challenge3a.png?raw=true)

## Challenge 3-b (2 points)
```
```
![image](challenge3b.png?raw=true)

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
