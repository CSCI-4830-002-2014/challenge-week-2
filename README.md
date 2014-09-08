# Name

Marc Simpson

# How many points have you earned?

90/100


# Show and tell (10 points)

[Build a Wireless Home Security System With an Arduino](http://lifehacker.com/build-a-wireless-home-security-system-with-an-arduino-1619435213)

# Checkpoints

## Checkpoint 1 (5 points)

![image](http://i.imgur.com/y8HCvxi.png)

## Checkpoint 2 (5 points)

![image](http://i.imgur.com/TUGSXhi.png)

## Checkpoint 3 (5 points)

![image](http://i.imgur.com/8xU3BOM.png)

## Checkpoint 4 (5 points)

![image](http://i.imgur.com/0gssNYC.png)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

Different servers so that traffic is managed a lot better.

### Q2. (3 points)

Entering in 200 would help eliminate the warning and error signs in your code.

### Q3. (3 points)

It helps connect multiple queries together to help input into different applications significantly easier.

### Q4. (3 points)

With the amount of data that could possibly be collected, the database would never end and it would almost be impossible to find what you are looking for. So using logs would be the easiest way to look at the data collected in real time.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://i.imgur.com/brh5TRT.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
![image](http://i.imgur.com/WWJbtwK.png)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events", c(eval(action="purchase")) AS "Purchases"
```
![image](http://i.imgur.com/eKKLoVn.png)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events", c(eval(action="purchase")) AS "Purchases", c(eval(action="addtocart")) AS "Add to Cart",c(eval(action="remove")) AS "Remove"
```
![image](http://i.imgur.com/7VIrXRA.png)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/e9lEbUm.png)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/UaAdNcA.png)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX"
```
![image](http://i.imgur.com/KtTj6ph.png)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX", min(bytes) AS "MIN", avg(bytes) AS "AVG"
```
![image](http://i.imgur.com/tGIltRL.png)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats distinct_count(productId), values(productId) as "UniqueProducts"
```
![image](http://i.imgur.com/IywrdxM.png)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top clientip
```
![image](http://i.imgur.com/HQ1ICyc.png)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | top date_wday limit=3
```
![image](http://i.imgur.com/gQdt62N.png)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | top productId
```
![image](http://i.imgur.com/MPb46mC.png)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday | top productId
```
![image](http://i.imgur.com/JaPKD3j.png)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday action=purchase| top productId
```
![image](http://i.imgur.com/CK2UZCr.png)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action=purchase| top productId limit=1
```
![image](http://i.imgur.com/lc4w52M.png)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId=* | timechart count(action) BY dates
```
![image](http://i.imgur.com/t078mqb.png)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count(action) BY dates
```
![image](http://i.imgur.com/mjZE1OO.png)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) by days
```
![image](http://i.imgur.com/WFGKgwY.png)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) span=hours
```
![image](http://i.imgur.com/59GioRC.png)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart c(action) by host
```
![image](http://i.imgur.com/HldeQGX.png)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by productId
```
![image](http://i.imgur.com/iCCPIVS.png)

## Challenge 3-f (2 points)
```
sourcetype=access_* | timechart count(action) by productId useother=f usenull=f limit=16
```
![image](http://i.imgur.com/Qc1GpoB.png)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by clientip
```
![image](http://i.imgur.com/0soIWO4.png)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by clientip useother=f limit=10
```
![image](http://i.imgur.com/eYEIb2S.png)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=* | timechart sum(bytes) span=hours
```
![image](http://i.imgur.com/o39Bncs.png)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET)" | table mymethod, method, _raw |  rex "(?<mymethod>POST)" | table mymethod, method, _raw
```
![image](http://i.imgur.com/WIy69Gf.png)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | rex "(GET|POST) /cart.do\?action=(?<myaction>(purchase|addtocart|remove|view|remove|purchase|changequantity))" | table myaction, action, _raw

![image](http://i.imgur.com/OOhFtOh.png)
