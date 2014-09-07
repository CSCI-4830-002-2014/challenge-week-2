# Name

Alexia Newgord

# How many points have you earned?

100/100

# Show and tell (10 points)

[Build a Wireless Home Security System With an Arduino](http://lifehacker.com/build-a-wireless-home-security-system-with-an-arduino-1619435213)

# Checkpoints

## Checkpoint 1 (5 points)

![cp1](cp1.png?raw=true)

## Checkpoint 2 (5 points)

![cp2](cp2.png?raw=true)

## Checkpoint 3 (5 points)

![cp3](cp3.png?raw=true)

## Checkpoint 4 (5 points)

![cp5](cp4.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

In the tutorial data provided by Splunk, what do the host names www1, www2, and www3 mean? Why are there three?

The three different "www"s are different hosts.  There are three different names to specify which host to access.

### Q2. (3 points)

What is the purpose of including “status=200” in queries?

"status=200" indicates success, so it excludes failed processes.

### Q3. (3 points)

What is your best guess as the rationale behind the heavy use of the | (pipe) operator in Splunk queries?

The usage of the pipe sends the output of one command to the input of another, which allows query statements to be more specific on what we are accessing.  Without the pipe, we would likely need to run two separate queries, which could be a hassle.

### Q4. (3 points)

Why does one ever need to analyze “product purchase” behaviors from raw server logs retroactively? Why can’t we just save every behavior in a structural database?

We may need to analyze behaviors retroactively to identify issues throughout the user experience.  At the same time, using a structural database may be too heavyweight and potentially slow for the purposes and format of the raw server logs.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![c1-a](c1-a.png?raw=true)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count as Events
```
![c1-b](c1-b.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count as Events, count(eval(action="purchase")) as Purchases
```
![c1-c](c1-c.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count as Events, count(eval(action="purchase")) as Purchases, count(eval(action="addtocart")) as AddToCarts, count(eval(action="remove")) as Removes
```
![c1-d](c1-d.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![c1-e](c1-e.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![c1-f](c1-e.png?raw=true)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX
```
![c1-g](c1-g.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX, min(bytes) as MIN, avg(bytes) as AVG
```
![c1-h](c1-h.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats distinct_count(productId) as NumberOfUniqueProducts, values(productId) as UniqueProducts
```
![c1-i](c1-i.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top clientip
```
![c2-a](c2-a.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_*  productId cart.do | top date_wday limit=3
```
![c2-b](c2-b.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* action="*" | top productId
```
![c2-c](c2-c.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_*  date_wday=friday action="*" | top productId
```
![c2-d](c2-d.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_*  date_wday=friday action="purchase" | top productId
```
![c2-e](c2-e.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* action="purchase" | top productId limit=1
```
![c2-f](c2-f.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_*  action="purchase" | top productId by date_wday limit=1
```
![c2-g](c2-g.png?raw=true)

## Challenge 3-a (2 points)
```
sourcetype=access_*  productId=* | timechart count
```
![c3-a](c3-a.png?raw=true)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) as UniqueIPs
```
![c3-b](c3-b.png?raw=true)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) as UniqueIPs span=1h
```
![c3-c](c3-c.png?raw=true)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count by host
```
![c3-d](c3-d.png?raw=true)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count by productId
```
![c3-e](c3-e.png?raw=true)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart count by productId limit=16
```
![c3-f](c3-f.png?raw=true)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count(clientip) by clientip
```
![c3-g](c3-g.png?raw=true)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart count(clientip) by clientip limit=10 useother=0
```
![c3-h](c3-h.png?raw=true)

## Challenge 3-i (2 points)
```
sourcetype=access_*  | timechart sum(bytes) span=1h
```
![c3-i](c3-i.png?raw=true)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET)" | rex "(?<mymethod>POST)" | table mymethod, method, _raw
```
![c4-a](c4-a.png?raw=true)

## Challenge 4-b (4 points)
```
sourcetype=access_* sourcetype=access_* action | rex "(GET|POST) /cart.do\?action=(?<myaction>\w+)" | table myaction, action, _raw
```

![c4-b](c4-b.png?raw=true)
