# Name

Nikita Voskoboynik

# How many points have you earned?

81/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

DIY: An Automated, Motorized Camera Dolly Made Out of LEGO and an Arduino
(http://petapixel.com/2014/09/04/automated-motorized-dolly-made-building-blocks-childhood-lego/)

# Checkpoints

## Checkpoint 1 (5 points)

[Imgur](http://i.imgur.com/zre0gVl)

## Checkpoint 2 (5 points)

[Imgur](http://i.imgur.com/BojCXnU)

## Checkpoint 3 (5 points)

[Imgur](http://i.imgur.com/AOVdhLf)

## Checkpoint 4 (5 points)

[Imgur](http://i.imgur.com/Rw8K1au)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

They represent different web servers. The company must have three different web servers.

### Q2. (3 points)

It is the HTTP status code for a successful action.

### Q3. (3 points)

The pipe operator allows use to query smaller data sets. This is sort of like a nested select statement in T-SQL.

### Q4. (3 points)

Because this will give real-time insight.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
[Imgur](http://i.imgur.com/ghQZvO6.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
[Imgur](http://i.imgur.com/1YnRcbg.png)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) as Purchases
```
[Imgur](http://i.imgur.com/GFm5MfN.jpg)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) as Purchases, count(eval(action="addtocart")) as AddToCarts, count(eval(action="remove")) as Removes
```
[Imgur](http://i.imgur.com/t9qus8g.jpg)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
[Imgur](http://i.imgur.com/444LlwI.jpg)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
[Imgur](http://i.imgur.com/444LlwI.jpg)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX"
```
[Imgur](http://i.imgur.com/Yfh5jDt.jpg)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX", min(bytes) AS "MIN", avg(bytes) AS "AVG"
```
[Imgur](http://i.imgur.com/v4EMebU.jpg)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId) AS "NumberOfUniqueProducts", values(productId) AS "UniqueProductIds"
```
[Imgur](http://i.imgur.com/Hgp6mEY.jpg)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top clientip
```
[Imgur](http://i.imgur.com/PVKcLG0.jpg)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=3 date_wday
```
[Imgur](http://i.imgur.com/8hHFMxr.jpg)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
[Imgur](http://i.imgur.com/NEezUoi.jpg)

## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday| 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
[Imgur](http://i.imgur.com/iJaKnjE.jpg)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday action=purchase| 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
[Imgur](http://i.imgur.com/IgBFQtV.jpg)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=1 productId
```
[Imgur](http://i.imgur.com/5A0p1kQ.jpg)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top 1 productId by date_wday
```
[Imgur](http://i.imgur.com/6IFNM7u.jpg)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count
```
[Imgur](http://i.imgur.com/NNiRSOs.jpg)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart span=2d dc(clientip) AS "UniqueIPs"
```
[Imgur](http://i.imgur.com/GevEcD5.jpg)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart span=1h dc(clientip) AS "UniqueIPs"
```
[Imgur](http://i.imgur.com/3OcezQ7.jpg)

## Challenge 3-d (2 points)
```
????
```
????
## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart span=2d count by productId
```
[Imgur](http://i.imgur.com/Zt1ExmO.jpg)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart span=2d count by productId usenull=f useother=f
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
