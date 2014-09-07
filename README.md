# Name

Alexander Tsankov

# How many points have you earned?

0/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[title-of-the-article](http://link-to-an-interesting-article-about-a-cool-use-of-arduino)

# Checkpoints

## Checkpoint 1 (5 points)

[Imgur](http://i.imgur.com/3EGKh7i)

## Checkpoint 2 (5 points)

[Imgur](http://i.imgur.com/J8yCy4f)

## Checkpoint 3 (5 points)

[Imgur](http://i.imgur.com/6SYAtwk)

## Checkpoint 4 (5 points)

[Imgur](http://i.imgur.com/EyfF5rd)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

The hostnames refer to different servers. There seems to be three different web servers (www1,www2,www3) listed in the tutorial data for the same website and the host field is used to differentiate them. 

### Q2. (3 points)

The status field referes to the HTTP status code of the transaction, with 200 being considered OK and the transaction going through properly. 

### Q3. (3 points)

The pipe operator is carry over from BASH and it allows the user to chain together multiple results from different querys and feed them as input into different applications easily. 

### Q4. (3 points)

Sometimes if the data is being collected in either large amounts or very quickly, a structural database might not be able to keep track of all of the transactions and we might instead turn towards an application like Splunk which would allow us to do analysis of the actual server logs. This would also reuqire lower overhead because we wouldn't be managing a database on top of the server, we would only be logging the server data and possibly having Splunk on a different machine doing analysis retroactively. 

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count

```
[Imgur](http://i.imgur.com/QCICgiR)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
[Imgur](http://i.imgur.com/hqafIHp)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events", c(eval(action="purchase")) AS "Purchases"
```
[Imgur](http://i.imgur.com/EsV1epu)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events", c(eval(action="purchase")) AS "Purchases", c(eval(action="addtocart")) AS "Add to Cart",c(eval(action="remove")) AS "Remove"
```
[Imgur](http://i.imgur.com/4Ysjnsc)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
[Imgur](http://i.imgur.com/UlJwUNn)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
[Imgur](http://i.imgur.com/UlJwUNn)
## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX"
```
[Imgur](http://i.imgur.com/24ogoaB)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX", min(bytes) AS "MIN", avg(bytes) AS "AVG"
```
[Imgur](http://i.imgur.com/lc6Nme7)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats distinct_count(productId), values(productId) as "UniqueProducts"
```
[Imgur](http://i.imgur.com/Qmm0qlD)

## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top clientip
```
[Imgur](http://i.imgur.com/wvxfVi1)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | top date_wday limit=3
```
[Imgur](http://i.imgur.com/QG63A4w)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | top productId
```
[Imgur](http://i.imgur.com/WrnpoZP)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday | top productId
```
[Imgur](http://i.imgur.com/WZnyLda)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday action=purchase| top productId
```
[Imgur](http://i.imgur.com/xwULP5t)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action=purchase| top productId limit=1
```
[Imgur](http://i.imgur.com/jYed3tL)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do action=purchase| top productId by date_wday limit=1
```
[Imgur](http://i.imgur.com/jLymNCl)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count(action) BY dates
```
[Imgur](http://i.imgur.com/OO7qbxs)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) by days
```
[Imgur](http://i.imgur.com/uccpCVI)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) span=hours
```
[Imgur](http://i.imgur.com/N6x6hYe)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart c(action) by host
```
[Imgur](http://i.imgur.com/MWRWrmP)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by productId
```
[Imgur](http://i.imgur.com/SD2fxbp)

## Challenge 3-f (2 points)
```
sourcetype=access_* | timechart count(action) by productId useother=f usenull=f limit=16
```
[Imgur](http://i.imgur.com/YnAIk1u)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by clientip
```
[Imgur](http://i.imgur.com/S38hH5Y)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by clientip useother=f limit=10
```

[Imgur](http://i.imgur.com/aMUcjbz)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=* | timechart sum(bytes) span=hours
```
[Imgur](http://i.imgur.com/68dGIXR)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET)" | table mymethod, method, _raw |  rex "(?<mymethod>POST)" | table mymethod, method, _raw
```
[Imgur](http://i.imgur.com/ufAU2p5)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | rex "(GET|POST) /cart.do\?action=(?<myaction>(purchase|addtocart|remove|view|remove|purchase|changequantity))" | table myaction, action, _raw
```
[Imgur](http://i.imgur.com/ikPMX6a)
