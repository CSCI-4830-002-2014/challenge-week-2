# Name

Dawson Botsford

# How many points have you earned?

0/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Powerduino](http://lifehacker.com/build-your-own-smart-powerstrip-with-an-arduino-1573480006)

# Checkpoints

## Checkpoint 1 (5 points)

![image](http://i.imgur.com/IEmLX1X.png)

## Checkpoint 2 (5 points)

![image](http://i.imgur.com/vXwGEds.png)

## Checkpoint 3 (5 points)

Keep in mind my data dates and sizes of sets were not the same as theirs.
Data issues fixed for the challenges, but exact search integer results were still wrong with broken data :)

![image](http://i.imgur.com/LAaA1Uw.png)

## Checkpoint 4 (5 points)

![image](http://i.imgur.com/jNutZcL.png)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

fill-in-your-answer

### Q2. (3 points)

200 is the HTTP status code is the "OK" sign. This means the HTTP request succeeded.

### Q3. (3 points)

Similar to bash, the pipe concantenates actions so that the output of one filter becomes the input of another. This creates a very specific output because we can sort, cut, concatenate more data, etc. all to the original returned data.

### Q4. (3 points)

fill-in-your-answer

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://i.imgur.com/j3AdDwT.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
![image](http://i.imgur.com/J14Rin8.png)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS Views, count(eval(action="purchase")) AS Purchases
```
![image](http://i.imgur.com/sfoAw4o.png)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS Views, count(eval(action="purchase")) AS Purchases, count(eval(action="addtocart")) AS AddToCarts, count(eval(action="remove")) AS Removes
```
![image](http://i.imgur.com/KwCnBQF.png)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/AMhr6cr.png)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/AMhr6cr.png)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX
```
![image](http://i.imgur.com/ffidYVp.png)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX, min(bytes) as MIN, avg(bytes) as AVG
```
![image](http://i.imgur.com/3FkelBY.png)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats, dc(productId) AS NumberOfUniqueProducts, values(productId)
```
![image](http://i.imgur.com/IPFc9qd.png)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top clientip
```
![image](http://i.imgur.com/1PHBvc1.png)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top date_wday limit=3
```
![image](http://i.imgur.com/wCW3xtZ.png)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](http://i.imgur.com/5alMdBU.png)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday="friday" | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](http://i.imgur.com/NLZ8NJu.png)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do date_wday="friday" action="purchase"| 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](http://i.imgur.com/UoCxlsF.png)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action="purchase"| 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId limit="1"
```
![image](http://i.imgur.com/rfj84RA.png)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do action="purchase"| 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId by date_wday limit="1"
```
![image](http://i.imgur.com/7s7U5RQ.png)

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
