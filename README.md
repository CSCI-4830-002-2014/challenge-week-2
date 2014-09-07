# Name

Chris Wittenberg

# How many points have you earned?

94/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Lo-Fi Guitar Pedal](http://www.instructables.com/id/Lo-fi-Arduino-Guitar-Pedal/)

# Checkpoints

## Checkpoint 1 (5 points)

![image](C2Checkpoint1.png?raw=true)

## Checkpoint 2 (5 points)

![image](C2Checpoint2.png?raw=true)

## Checkpoint 3 (5 points)

![image](C2Checkpoint3.png?raw=true)

## Checkpoint 4 (5 points)

![image](C2Checkpoint4.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

These are the web servers that are being requested. There are three of them so that no one server is too busy, thus running transactions very quickly.

### Q2. (3 points)

The purpose of "status=200" is to filter out transactions that happened without error.

### Q3. (3 points)

My best guess as why the pipe character is used so much in Splunk Queries is because the result to the left of the queries are needed to complete the pieces of the query further to the right

### Q4. (3 points)

One would need to analyze "product purchase" behaviors from raw servers retroactively if there are errors in the purchase actions. If one tries to save every behavior in a structured database, it would take a lot of work to create, it would take up a lot of space, and it is unnecessary when you can look at raw server logs. 

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](C2Challenge1a.png?raw=true)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count As "Events"
```
![image](C2Challenge1b.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count As "Events", count(eval(action="purchase")) As "Purchases"
```
![image](C2Challenge1c.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count As "Events", count(eval(action="purchase")) As "Purchases", count(eval(action="addtocart")) As "AddToCarts", count(eval(action="remove")) As "Removes"
```
![image](C2Challenge1d.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes) 
```
![image](C2Challenge1e.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes) 
```
![image](C2Challenge1f.png?raw=true)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX
```
![image](C2Challenge1g.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX, min(bytes) as MIN, avg(bytes) As AVG
```
![image](C2Challenge1h.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_*   | dedup productId | stats values(productId) As "UniqueIds", count(productId) As "NumberOfUniqueProducts"| table NumberOfUniqueProducts, UniqueIds
```
![image](C2Challenge1i.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top clientip
```
![image](C2Challenge2a.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=3 date_wday
```
![image](C2Challenge2b.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](C2Challenge2c.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* date_wday=Friday productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday| top productId by date_wday
```
![image](C2Challenge2d.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* action=purchase date_wday=Friday productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday| top productId by date_wday
```
![image](C2Challenge2e.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* action=purchase productId  cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday | top limit=1 productId
```
![image](C2Challenge2f.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* action=purchase productId cart.do | 
	table clientip, action, productId, date_month, date_mday, date_wday|top limit=1  productId by date_wday
```
![image](C2Challenge2g.png?raw=true)

## Challenge 3-a (2 points)
```
sourcetype=access_* | timechart count(action)
```
![image](C2Challenge3a.png?raw=true)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=*| timechart count(clientip) As "UniqueID's"
```
![image](C2Challenge3b.png?raw=true)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=*| timechart span=1hr count(clientip) As "UniqueIDs"
```
![image](C2Challenge3c2.png?raw=true)

## Challenge 3-d (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](C2Challenge3d.png?raw=true)

## Challenge 3-e (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](C2Challege3e.png?raw=true)

## Challenge 3-f (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](C2Challenge3f.png?raw=true)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=*| timechart count(clientip) As "UniqueID's" by clientip
```
![image](C2Challenge3g.png?raw=true)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=*| timechart count(clientip) As "UniqueID's" by clientip useother=f
```
![image](C2Challenge3h.png?raw=true)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=*| timechart span=1hr sum(bytes)
```
![image](C2Challenge3i.png?raw=true)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET|POST)" | 
     table mymethod, method, _raw
```
![image](C2Challenge4a.png?raw=true)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | 
    rex "(GET|POST) /cart.do\?action=(?<myaction>purchase|addtocart|view)" |
    table myaction, action, _raw
```
![image](C2Challenge4b.png?raw=true)


