# Name

write-your-name

# How many points have you earned?

0/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Helmet of many LEDS built for burning man](http://hackaday.com/2012/09/14/helmet-of-many-leds-built-for-burning-man/)

# Checkpoints

## Checkpoint 1 (5 points)

![image](http://i.imgur.com/HOF1erS.png)

## Checkpoint 2 (5 points)

![image](http://imgur.com/uQVzcXy.png)

## Checkpoint 3 (5 points)

![image](http://i.imgur.com/WH12PlJ.png)

## Checkpoint 4 (5 points)

![image](http://i.imgur.com/tOZH2Zv.png)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

the ww1, ww2, and ww2 hosts are Virtual Hosts on the domain. It is nice to be able to serve different sites, or different parts of your site (a shop vs infomration site, for example) from different IP's for both load balancing and administration purposes. There are three as the site has three different "sections" to there site, a Store .... and two others. I remember it said in one of the tutorials, but now I can't seem to find it. 

### Q2. (3 points)

Status=200 queries are HTTP request "success". We include this so we arn't analyzing errors or other strange happenings with our data.

### Q3. (3 points)

The pipe operator allows us to run functions/"commands" realtime on our query, this seems invaluable. 

### Q4. (3 points)

A few reasons. You probably could use a structural database, but maybe we didn't think of setting it up. It would have also required us to design of database extremely well, to allow for the types of queries we want. Using this "unstrucured" format allows us to save all data we view as relevent, and then conduct arbitrary queries on it at a later point in time, allowing us to decide what is "important" after the data has been generated with relativly little fuss. 

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://i.imgur.com/HuO4dIc.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
![image](http://i.imgur.com/bG8bL17.png)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count as "Events", count(eval(action="purchase")) as "Purchased"
```
![image](http://i.imgur.com/15M67yh.png)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count as "Events", count(eval(action="purchase")) as "Purchased", count(eval(action="addtocart")) as "AddToCarts", count(eval(action="remove")) as "Removes"
```
![image](http://imgur.com/Ol23d7i.png)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/fBZl1Ql.png)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX
```
![image](http://i.imgur.com/SA8Gw9J.png)
## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX
```
![image](http://i.imgur.com/SA8Gw9J.png)
## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX, min(bytes) as MIN, avg(bytes) as AVG
```
![image](http://imgur.com/BPooRWm.png)
## Challenge 1-i (2 points)
```
sourcetype=access_* | stats  dc(productId) as NumberofUniqueProducts ,values(productId) as UniqueProductIds
```
![image](http://i.imgur.com/ZJzOweH.png)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=10 clientip
	```
![image](http://i.imgur.com/7DL2Hrc.png)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=3 date_wday
	```
![image](http://i.imgur.com/L4cAaEM.png)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=10 productId
```
![image](http://imgur.com/F3e0zAN.png)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId date_wday=friday cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=10 productId
```
![image](http://i.imgur.com/yxdOXpo.png)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId date_wday=friday action=purchase cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=10 productId
```
![image](http://i.imgur.com/hS8SoSP.png)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action=purchase| 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=1 productId
```
![image](http://i.imgur.com/ECT354r.png)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do action=purchase| 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=1 productId by date_wday
```
![image](http://i.imgur.com/mH90Db1.png)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by host
```
![image](http://i.imgur.com/47hRsin.png)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart dc(clientip)
```
![image](http://i.imgur.com/k87J52i.png)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart span=1h dc(clientip) as UniqueIps
```
![image](http://i.imgur.com/1TmlK6u.png)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by source
```
![image](http://i.imgur.com/NAgdLnn.png)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count by productId
```
![image](http://i.imgur.com/js7KHbL.png)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart count by productId limit=0
```
![image](http://i.imgur.com/PX5qsZR.png)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip
```
![image](http://i.imgur.com/SMR9crf.png)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=*|  timechart limit=10 count by clientip useother=f
```
![image](http://i.imgur.com/U9VKVXW.png)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=*| timechart span=1h sum(bytes)
```
![image](http://i.imgur.com/fcgQdsI.png)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET||POST)" | 
     table mymethod, method, _rawege
```
![image](http://i.imgur.com/3LZuZ8D.png)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | 
    rex "(GET|POST) /cart.do\?action=(?<myaction>addtocart|purchase|view|changequantity)" |
    table myaction, action, _raw
```
![image](http://imgur.com/9QP2kEB)
