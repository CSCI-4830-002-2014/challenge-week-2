# Name

write-your-name

# How many points have you earned?

0/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[title-of-the-article](http://link-to-an-interesting-article-about-a-cool-use-of-arduino)

# Checkpoints

## Checkpoint 1 (5 points)

![image](Checkpoint1.png?raw=true)

## Checkpoint 2 (5 points)

![image](Checkpoint2.png?raw=true)

## Checkpoint 3 (5 points)

![image](Checkpoint3.png?raw=true)

Note: Here I used the day before I downloaded the data, a filter of 'Yesterday' returns nothing.

## Checkpoint 4 (5 points)

![image](Checkpoint4.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

fill-in-your-answer

### Q2. (3 points)

fill-in-your-answer

### Q3. (3 points)

fill-in-your-answer

### Q4. (3 points)

fill-in-your-answer

# Challenges

## Challenge 1-a (2 points)
```
sourcetype="access_*" | stats count
```
![image](1a.png?raw=true)

## Challenge 1-b (2 points)
```
sourcetype="access_*" | stats count AS Events
```
![image](1b.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype="access_*" | stats count AS Events, count(eval(action="purchase")) AS Purchases
```
![image](1c.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype="access_*" | stats count AS Events, count(eval(action="purchase")) AS Purchases, count(eval(action="addtocart")) AS AddToCarts, count(eval(action="remove")) AS Removes
```
![image](1d.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype="access_*" | stats max(bytes)
```
![image](1e.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype="access_*" | stats max(bytes)
NOTE: This is the same as 1-e for some reason.  Probably a typo in the question.
```
![image[(1f.png?raw=true)

## Challenge 1-g (2 points)
```
sourcetype="access_*" | stats max(bytes) AS MAX
```
![image](1g.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype="access_*" | stats max(bytes) AS MAX, min(bytes) AS MIN, avg(bytes) AS AVG
```
![image](1h.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype="access_*" | stats dc(productId), values(productId)
```
![image](1i.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top clientip
```
![image](2a.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top date_wday limit=3
```
![image](2b.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](2c.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* date_wday="friday" productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](2d.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* date_wday="friday" action="purchase" productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](2e.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* action="purchase" productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId limit=1
```
![image](2f.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* action="purchase" productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId limit=1 by date_wday
```
![image](2g.png?raw=true)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count
```
![image](3a.png?raw=true)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart dc(clientip) AS UniqueIPs
```
![image](3b.png?raw=true)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart span=1h dc(clientip) AS UniqueIPs
```
![image](3c.png?raw=true)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count by source
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
sourcetype=access_* productId=* | timechart count by clientip useother=f
```
![image](3h.png?raw=true)

## Challenge 3-i (2 points)
```
sourcetype=access_* | timechart span=1h sum(bytes)
```
![image](3i.png?raw=true)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET|POST)"| table mymethod, method, _raw
```
![image](4a.png?raw=true)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | 
    rex "(GET|POST) /cart.do\?action=(?<myaction>purchase|view|addtocart|remove|changequantity)" |
    table myaction, action, _raw
```
![image](4b.png?raw=true)
