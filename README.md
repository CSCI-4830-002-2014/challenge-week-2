# Name

Jose-Vieitez
# How many points have you earned?

100/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[title-of-the-article](http://link-to-an-interesting-article-about-a-cool-use-of-arduino)

# Checkpoints

## Checkpoint 1 (5 points)

![image](http://i.imgur.com/EjEXF36.jpg?raw=true)

## Checkpoint 2 (5 points)

![image](http://i.imgur.com/D4FtpzE.png?raw=true)

## Checkpoint 3 (5 points)

![image](http://i.imgur.com/ZRVAXIW.png?raw=true)

## Checkpoint 4 (5 points)

![image](http://i.imgur.com/4THS1lU.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

This was not in the tutorial I read, but they are subdomains created as mirrors of the same site to balance server loads. 

### Q2. (3 points)

200 means they were successful transactions
### Q3. (3 points)

Allows you more control over data results, by running searches given the terms before the "|" in a very quick way without having to access the drop down menu. 
### Q4. (3 points)

You can do more complex data search and correlations retroactively vs by just adding them to a table. This is why in Excel you have to create pivot tables one at a time instead of automatically, it takes too much bandwidth to have every possible option be a pivot table so you have to do it one at a time. 

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://i.imgur.com/crAjI4x.png?raw=true)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count as "Events"
```
![image](http://i.imgur.com/o7wga6w.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count as "Events", c(eval(action="purchase")) as "purchases"
```
![image](http://i.imgur.com/7TNiYHb.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count as "Events", c(eval(action="purchase")) as "purchases", c(eval(action="addtocart")) as "AddToCarts", c(eval(action="remove")) as "Removes"
```
![image](http://i.imgur.com/zqlRfWq.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/EA5kpsN.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/lCRpG4j.png?raw=true)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as "MAX"
```
![image](http://i.imgur.com/ZxsppPi.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as "MAX", min(bytes) as "MIN", avg(bytes) as "AVG"
```
![image](http://i.imgur.com/YTdwNPl.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId) as "NumberOfUniqueProducts", values(productId) as "UniqueProductIds"
```
![image](http://i.imgur.com/09ovMCc.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top limit=10 clientip
```
![image](http://i.imgur.com/Bc1KDut.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | top limit=3 date_wday
```
![image](http://i.imgur.com/BPkV2II.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | top limit=10 productId
```
![image](http://i.imgur.com/EXbzSy6.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday | top limit=10 productId
```
![image](http://i.imgur.com/5rZ5g7M.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday action=purchase | top limit=10 productId
```
![image](http://i.imgur.com/9YdMw1y.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action=purchase | top limit=1 productId
```
![image](http://i.imgur.com/Tg9Q5IW.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do action=purchase | top limit=1 productId by date_wday
```
![image](http://i.imgur.com/SKPlcLN.png?raw=true)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count    - It increases after day 1 and then plateaus 
```
![image](http://i.imgur.com/UVGhCOA.png?raw=true)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart dc(clientip)    - similarly plateaus over time. 
```
![image](http://i.imgur.com/7QJmFlI.png?raw=true)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart span=1h dc(clientip)  - seems consistently spiking earlier in the day, potentially the 12-4am hours
```
![image](http://i.imgur.com/9reiZs9.png?raw=true)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count by host
```
![image](http://i.imgur.com/wuYTATx.png?raw=true)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=*| timechart count by productId
```
![image](http://i.imgur.com/f9HPdr4.png?raw=true)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=*| timechart count by productId limit=20
```
![image](http://i.imgur.com/uQ1tA1B.png?raw=true)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=*| timechart count by clientip
```
![image](http://i.imgur.com/I6wWzNp.png?raw=true)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=*| timechart count by clientip useother=no
```
![image](http://i.imgur.com/gQgYy7N.png?raw=true)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=*| timechart sum(bytes) span=1h
```
![image](http://i.imgur.com/D0pNLzU.png?raw=true)

## Challenge 4-a (4 points)
```
+sourcetype=access_* | rex "(?<mymethod>(GET|POST))" | table mymethod, method, _raw
```
![image](http://i.imgur.com/5enH3XO.jpg?raw=true)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | rex "(GET|POST) /cart.do\?action=(?<myaction>purchase|view|remove|addtocart|changequantity)" |table myaction, action, _raw
```
![image](http://i.imgur.com/4THS1lU.png?raw=true)