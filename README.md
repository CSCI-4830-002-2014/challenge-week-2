# Name

Joshua Ferge

# How many points have you earned?

100/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Farm Geeks Love Arduinos](http://modernfarmer.com/2013/05/farm-geeks-learning-to-love-the-circuit-board/)

# Checkpoints

## Checkpoint 1 (5 points)

![image](check1.png?raw=true)

## Checkpoint 2 (5 points)

![image](check2.png?raw=true)

## Checkpoint 3 (5 points)

![image](check3.png?raw=true)

## Checkpoint 4 (5 points)

![image](check4.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

www1, www2, and ww3 are mirrors for server load balancing, so that the pages can be hosted on different servers.

### Q2. (3 points)

status=200 means that the page was queried and returned successfuly, which is necessary because otherwise we would query pages that didn't return correctly

### Q3. (3 points)

So that you may do many different steps of commands, and be able to chip and chip until you get the right set of data that you want.

### Q4. (3 points)

Doing database entries like that can take a lot of server time and make our clients experience worse by making it slower.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* stats count
```
![image](1a.png?raw=true)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count as Events
```
![image](1b.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count as Events, count(eval(action="purchase")) as Purchases
```
![image](1c.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count as Events, count(eval(action="purchase")) as Purchases, count(eval(action="addtocart")) as AddToCarts, count(eval(action="remove")) as Removes```
![image](1d.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](1e.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](1f.png?raw=true)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX 
```
![image](1g.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype=access_* stats max(bytes) as MAX, min(bytes) as MIN, avg(bytes) as AVG
```
![image](1h.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats distinct_count(productId) as NumberOfUniqueProducts, values(productId) as UniqueProducts
```
![image](1i.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top clientip
```
![image](2a.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | top date_wday limit=3
```
![image](2b.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* action="*" | top productId
```
![image](2c.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* date_wday=friday action="*" | top productId
```
![image](2d.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* date_wday=friday action="purchase" | top productId
```
![image](2e.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* action="purchase" | top productId limit=1
```
![image](2f.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* action="purchase" | top productId by date_wday limit=1
```
![image](2g.png?raw=true)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count
```
![image](3a.png?raw=true)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) as UniqueIPs
```
![image](3b.png?raw=true)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) as UniqueIPs span=1h
```
![image](3c.png?raw=true)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count by host
```
![image](3d.png?raw=true)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count by productId
```
![image](3e.png?raw=true)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart count by productId limit=16
```
![image](3f.png?raw=true)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip
```
![image](3g.png?raw=true)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip useother=false
```
![image](3h.png?raw=true)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=* | timechart sum(bytes) span=1h
```
![image](3i.png?raw=true)

## Challenge 4-a (4 points)
```
sourcetype=access_* sourcetype=access_* | rex "(?<mymethod>(GET|POST))" | table mymethod, method, _raw
```
![image](4a.png?raw=true)

## Challenge 4-b (4 points)
```
sourcetype=access_* | rex "(GET|POST) /cart.do\?action=(?<myaction>purchase|addtocart|view|remove|changequantity)" | table myaction, action, _raw
