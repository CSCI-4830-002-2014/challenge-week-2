# Name

Austin Wood

# How many points have you earned?

100/100

# Show and tell (10 points)

[Build a Universal Smart Remote Control with an Arduino](http://lifehacker.com/build-a-universal-smart-remote-control-with-an-arduino-1627481048)

# Checkpoints

## Checkpoint 1 (5 points)

![checkpoint 1](images/splunk2_cp1.png?raw=true)

## Checkpoint 2 (5 points)

![checkpoint 2](images/splunk2_cp2.png?raw=true)

## Checkpoint 3 (5 points)

![checkpoint 3](images/splunk2_cp3.png?raw=true)

## Checkpoint 4 (5 points)

![checkpoint 4](images/splunk2_cp4.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

The www1, www2, and www3 are all hosting servers for data. Multiple servers serving the same sites are often useful if the site is getting a lot of traffic.

### Q2. (3 points)

The code "status=200" stands for success (i.e. successful purchases).

### Q3. (3 points)

The pipe (|) character is also used in shell commands and allows the user to chain or combine results from different queries and carry them through a process. This is perfect when filtering search results in our case.

### Q4. (3 points)

Tracking actual server logs seems much faster than storing every single transaction in a database, especially if there is heavy traffic for the site. It could also be easier to manage and maintain since you wouldn't have to be keeping track of database commands on top of running queries in a server log.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* stats count
```
![challenge 1a](images/splunk2_ch1a.png?raw=true)

## Challenge 1-b (2 points)
```
sourcetype=access_* stats AS Events
```
![challenge 1b](images/splunk2_ch1b.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* stats AS Events count(eval(action="purchase")) As Purchases
```
![challenge 1c](images/splunk2_ch1c.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* stats count AS Events, count(eval(action="purchase")) AS Purchases, count(eval(action="addtocart")) AS AddToCarts, count(eval(action="remove")) AS Removes
```
![challenge 1d](images/splunk2_ch1d.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![challenge 1e](images/splunk2_ch1e.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype=access_ * | stats max(bytes)
```
![challenge 1f](images/splunk2_ch1f.png?raw=true)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS MAX
```
![challenge 1g](images/splunk2_ch1g.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS MAX, min(bytes) AS MIN, avg(bytes) AS AVG
```
![challenge 1h](images/splunk2_ch1h.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats  dc(productId) as NumberofUniqueProducts, values(productId) as UniqueProductIds
```
![challenge 1i](images/splunk2_ch1i.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top clientip
```
![challenge 2a](images/splunk2_ch2a.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | top date_wday limit=3
```
![challenge 2b](images/splunk2_ch2b.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* action=* | top productId
```
![challenge 2c](images/splunk2_ch2c.png?raw=true)

## Challenge 2-d (2 points)
```
sourcetype=access_* action=* date_wday=friday | top productId
```
![challenge 2d](images/splunk2_ch2d.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* action=purchase date_wday=friday | top productId
```
![challenge 2e](images/splunk2_ch2e.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* action=purchase | top productId limit=1
```
![challenge 2f](images/splunk2_ch2f.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* action=purchase | top productId limit=1 by date_wday
```
![challenge 2g](images/splunk2_ch2g.png?raw=true)


## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count
```
![challenge 3a](images/splunk2_ch3a.png?raw=true)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart dc(clientip) AS UniqueIPs
```
![challenge 3b](images/splunk2_ch3b.png?raw=true)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart span=1h dc(clientip) AS UniqueIPs
```
![challenge 3c](images/splunk2_ch3c.png?raw=true)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count by source
```
![challenge 3d](images/splunk2_ch3d.png?raw=true)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count by productId
```
![challenge 3e](images/splunk2_ch3e.png?raw=true)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart count by productId limit=16
```
![challenge 3f](images/splunk2_ch3f.png?raw=true)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip
```
![challenge 3g](images/splunk2_ch3g.png?raw=true)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip useother=false limit=10
```
![challenge 3h](images/splunk2_ch3h.png?raw=true)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=* | timechart sum(bytes) span=h
```
![challenge 3i](images/splunk2_ch3i.png?raw=true)


## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET)" | table mymethod, method, _raw |  rex "(?<mymethod>POST)" | table mymethod, method, _raw
```
![challenge 4a](images/splunk2_ch4a.png?raw=true)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | rex "(GET|POST) /cart.do\?action=(?<myaction>(purchase|addtocart|remove|view|remove|changequantity))" | table myaction, action, _raw
```
![challenge 4b](images/splunk2_ch4b.png?raw=true)
