# Name

Jake Charland

# How many points have you earned?

100/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[twitter mood light](http://www.instructables.com/id/Twitter-Mood-Light-The-Worlds-Mood-in-a-Box/)

# Checkpoints

## Checkpoint 1 (5 points)

![Imgur](http://i.imgur.com/vBhi5LW)

## Checkpoint 2 (5 points)

![Imgur](http://i.imgur.com/c2LYpi5)

## Checkpoint 3 (5 points)

![Imgur](http://i.imgur.com/2jfdtQv)

## Checkpoint 4 (5 points)

![Imgur](http://i.imgur.com/MYwKMEz)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

They are the three different web servers that these logs came from.

### Q2. (3 points)

The purpose of including status=200 in the query is it tells us that the request completed with an http status 200 OK.

### Q3. (3 points)

I believe they used the pipe operator to chain commands together because this is exactly how a command line interface works on all UNIX machines. This is important because most developers are already familiar with this kind of behavior so when using splunk it already feels familiar to them.

### Q4. (3 points)

If you were to store that sort of data in structure on the server it would be very time and memory costly to the server to do so and would not be worth the extra loads on the server. Especially when you have programs like splunk that allow you to query your data so easily.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![Imgur](http://i.imgur.com/cR1mJBE)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
![Imgur](http://i.imgur.com/unUAQgA)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) AS Purchases
```
![Imgur](http://i.imgur.com/sfuQGtY)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) AS Purchases, count(eval(action="addtocart")) AS AddToCarts, count(eval(action="remove")) AS Removes
```
![Imgur](http://i.imgur.com/UArB0mr)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![Imgur](http://i.imgur.com/EPMEV3F)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![Imgur](http://i.imgur.com/EPMEV3F)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS MAX
```
![Imgur](http://i.imgur.com/S72gvUP)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS MAX, min(bytes) AS MIN, avg(bytes) AS AVG
```
![Imgur](http://i.imgur.com/8mBOquF)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId) AS NumberOfUniqueProducts, values(productId) AS UniqueProducts
```
![Imgur](http://i.imgur.com/eOsTfRC)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId | top limit=10 clientip
```
![Imgur](http://i.imgur.com/J5SVejL)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId | top limit=3 date_wday
```
![Imgur](http://i.imgur.com/oQFyijC)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId | top productId
```
![Imgur](http://i.imgur.com/iGHcXfN)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do | top productId by date_wday | where date_wday="friday"
```
![Imgur](http://i.imgur.com/yCcBarE)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId action=purchase | top productId by date_wday | where date_wday="friday"
```
![Imgur](http://i.imgur.com/t9S1OhP)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId action=purchase | top limit=1 productId
```
![Imgur](http://i.imgur.com/7XEFCqU)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId action=purchase | top limit=1 productId by date_wday
```
![Imgur](http://i.imgur.com/RENSy24)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count(action)
```
![Imgur](http://i.imgur.com/nDV4rZU)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart dc(clientip) AS UniqueIp's
```
![Imgur](http://i.imgur.com/IJIifia)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart span=1h dc(clientip) AS UniqueIp's
```
![Imgur](http://i.imgur.com/Fc51RWc)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart span=1d count by host
```
![Imgur](http://i.imgur.com/JceF4LT)
## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart span=1d count by productId
```
![Imgur](http://i.imgur.com/Msr1XQP)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart span=1d count by productId limit=0
```
![Imgur](http://i.imgur.com/RWv0uVh)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart span=1d count by clientip
```
![Imgur](http://i.imgur.com/UY1a5rT)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart span=1d count by clientip useother=f
```
![Imgur](http://i.imgur.com/HEdRr0Y)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=* | timechart span=1h sum(bytes)
```
![Imgur](http://i.imgur.com/ccCRw2v)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET|POST)" | table mymethod, _raw
```
![Imgur](http://i.imgur.com/JedZ8IF)

## Challenge 4-b (4 points)
```
sourcetype=access_* sourcetype=access_* action | 
    rex "(GET|POST) /cart.do\?action=(?<myaction>purchase|addtocart|view)" |
    table myaction, action, _raw
```
![Imgur](http://i.imgur.com/jArnUPf)
