# Name

Michael Fyk

# How many points have you earned?

94/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Build a Wireless Home Security System With an Arduino](http://lifehacker.com/build-a-wireless-home-security-system-with-an-arduino-1619435213)

# Checkpoints

## Checkpoint 1 (5 points)

![image](http://i.imgur.com/oPhUAGO.png)

## Checkpoint 2 (5 points)

![image](http://i.imgur.com/dPOCEjD.png)

## Checkpoint 3 (5 points)

![image](http://i.imgur.com/nDsLYJZ.png)

## Checkpoint 4 (5 points)

![N/A Incomplete ("Could not find access_combined_wcookie" error)](image.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

Www1, www2, and www3 are all subdomains of the fictional online store. There are three because there are three separate host servers processing data, and each server can only have one domain.

### Q2. (3 points)

Status 200 indicates that the http request was a success. If an purchase is logged with a different status, it didn't succeed and should not be included in statistics for purchases.

### Q3. (3 points)

The | operator allows the user to perform commands on search queries. These commands, such as Top, Stats, etc. allow the user to make sense of and analyze the data rather than simply finding it.

### Q4. (3 points)

Behaviors can occur at a much faster rate and higher volume than is possible to store and analyze from a structured database.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://i.imgur.com/AdFqlsx.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
![image](http://i.imgur.com/e6iO6c0.png)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events" | join [search sourcetype=access_* status=200 action=purchase | stats count AS "Purchases"]
```
![image](http://i.imgur.com/Dib5yeJ.png)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events" | join [search sourcetype=access_* status=200 action=purchase | stats count AS "Purchases"] | join [search sourcetype=access_* status=200 action=addtocart | stats count AS "AddToCarts"] | join [search sourcetype=access_* status=200 action=remove | stats count AS "Removes"]
```
![image](http://i.imgur.com/VRzBPaQ.png)

## Challenge 1-e (2 points)
```
sourcetype = access_* | stats max(bytes)
```
![image](http://i.imgur.com/AfGh2q7.png)

## Challenge 1-f (2 points)
```
sourcetype = access_* | stats max(bytes)
```
![image](http://i.imgur.com/AfGh2q7.png)

## Challenge 1-g (2 points)
```
sourcetype = access_* | stats max(bytes) AS "MAX"
```
![image](http://i.imgur.com/YOYG7nL.png)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX" | join [search sourcetype=access_* | stats avg(bytes) AS "AVG"]| join [search sourcetype=access_* | stats min(bytes) AS "MIN"] |
```
![image](http://i.imgur.com/I9eEqKr.png)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId), values(productId)
```
![image](http://i.imgur.com/dCvayJp.png)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top clientip
```
![image](http://i.imgur.com/dvdnFAW.png)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=3 date_wday
```
![image](http://i.imgur.com/jOKcFbC.png)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId

```
![image](http://i.imgur.com/FGOrn5a.png)


## Challenge 2-d (2 points)
```
sourcetype=access_* date_wday=FRIDAY productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](http://i.imgur.com/yDo8FA7.png)

## Challenge 2-e (2 points)
```
sourcetype=access_* action=purchase status=200 date_wday=FRIDAY productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](http://i.imgur.com/GREU4Oo.png)

## Challenge 2-f (2 points)
```
sourcetype=access_* action=purchase productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=1 productId
```
![image](http://i.imgur.com/HvnBcdt.png)

## Challenge 2-g (2 points)
```
sourcetype=access_* action=purchase productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=1 productId by date_wday |
```
![image](http://imgur.com/7s05jVT)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count
```
![image](http://i.imgur.com/gEYVQpt.png)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart dc(clientip)
```
![image](http://i.imgur.com/bPURYUY.png)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=*| timechart span=1h dc(clientip)
```
![image](http://i.imgur.com/WbBgQEa.png)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=*| timechart count by host
```
![image](http://i.imgur.com/JwFKQdR.png)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=*| timechart count by productId
```
![image](http://i.imgur.com/Jg1CtYM.png)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=*| timechart count by productId useother=f limit=16
```
![image](http://i.imgur.com/cL4s1XY.png)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=*| timechart count by clientip
```
![image](http://i.imgur.com/iTOVziR.png)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=*| timechart count by clientip useother=false limit=10
```
![image](http://i.imgur.com/qtdIGTR.png)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=*| timechart span=1hr sum(bytes)
```
![image](http://i.imgur.com/khE2joE.png)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>(GET|POST))" | 
     table mymethod, method, _raw
```
![image](http://i.imgur.com/wUHO240.png)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | 
    rex "(GET|POST) /cart.do\?action=(?<myaction>.+?(?=&))" |
    table myaction, action, _raw
```
![image](http://i.imgur.com/Wz4QYxv.png)
