# Name

Adrian Chen

# How many points have you earned?

100/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Turn Signal Jacket](http://www.instructables.com/id/turn-signal-biking-jacket/)

# Checkpoints

## Checkpoint 1 (5 points)

![image](image.png?raw=true)

## Checkpoint 2 (5 points)

![image](image.png?raw=true)

## Checkpoint 3 (5 points)

![image](image.png?raw=true)

## Checkpoint 4 (5 points)

![image](image.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

The number after the WWW denotes which server is responding. Especially to handle large amounts of web traffic, multiple servers are often needed.

### Q2. (3 points)

The Status Code for a successful purchase is 200. This only searches only though the successful purchases.

### Q3. (3 points)

The pipe (|) is a commonly used programming tool, it is used with such regularity both here and in other languages because it is well known and easy to use.

### Q4. (3 points)

Doing this data analysis in real time may be impossible depending on the number of requests a server recieves. A structural database isn't fully scalable to large sizes.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://imgur.com/asmhOLe.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
![image](image.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS Events, count(eval(action="purchase")) AS Purchases
```
![image](image.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS Events, count(eval(action="purchase")) AS Purchases, count(eval(action="addtocart")) AS AddToCarts, count(eval(action="remove")) AS Removes
```
![image](image.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](image.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](image.png?raw=true)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS MAX
```
![image](image.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS MAX, min(bytes) AS MIN, avg(bytes) AS AVG
```
![image](image.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId), values(productId)
```
![image](image.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top clientip
```
![image](image.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top date_wday limit=3
```
![image](image.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](image.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* date_wday="friday" productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](image.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* date_wday="friday" action="purchase" productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](image.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* action="purchase" productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId limit=1
```
![image](image.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* action="purchase" productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId limit=1 by date_wday
```
![image](image.png?raw=true)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count
```
![image](image.png?raw=true)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart dc(clientip) AS UniqueIPs
```
![image](image.png?raw=true)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart span=3h dc(clientip) AS UniqueIPs
```
![image](image.png?raw=true)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count by source
```
![image](image.png?raw=true)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count by productId
```
![image](image.png?raw=true)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart count by productId limit=16
```
![image](image.png?raw=true)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip
```
![image](image.png?raw=true)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip useother=f
```
![image](image.png?raw=true)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=* | timechart span=3h sum(bytes)
```
![image](image.png?raw=true)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET|POST)" | table mymethod, method, _raw
```
![image](image.png?raw=true)

## Challenge 4-b (4 points)
```
sourcetype=access_* | rex "(GET|POST)" /cart.do\?action=(?<myaction>purchase|view|addtocart|remove|changequantity)"| table mymethod, method, _raw
