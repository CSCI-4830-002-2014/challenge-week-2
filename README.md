# Name

Logan Bates

# How many points have you earned?

60/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Use NodeJS and Arduino to build a weather display](http://www.node-disassemble.com/2014/09/04/lcd-weather-display/)

# Checkpoints

## Checkpoint 1 (5 points)

![image](Checkpoint1.png?raw=true)

## Checkpoint 2 (5 points)

![image](Checkpoint2.png?raw=true)

## Checkpoint 3 (5 points)

![image](Checkpoint3.png?raw=true)

## Checkpoint 4 (5 points)

![image](Checkpoint4.png?raw=true)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

Each www refers to a different web server that can be accessed. There are probably several to deal with heavy traffic on the web servers.

### Q2. (3 points)

This is an HTTP status code which represents a transaction that has successfully completed. 

### Q3. (3 points)

It helps when you want to add on to a search with new parameters, while maintaining your original train of thought. This also allows for easier modification of your search field.

### Q4. (3 points)

Server logs can handle requests from several different servers simulataneously. Additionally, server logs can be used if a database fails or is destroyed. If we save every behavior in a database, the database could become cluttered or too full and as a result, very slow.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](Challenge1a.png?raw=true)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count as "Events"
```
![image](Challenge1b.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count as "Events", count(eval(action="purchase")) as "Purchases"
```
![image](Challenge1c.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count as "Events", count(eval(action="purchase")) as "Purchases", count(eval(action="addtocart")) as "AddToCart", count(eval(action="remove")) as "Remove"
```
![image](Challenge1d.png?raw=true)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](Challenge1e.png?raw=true)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
Same as above

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX
```
![image](Challenge1g.png?raw=true)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX, min(bytes) as MIN, avg(bytes) As AVG]
```
![image](Challenge1h.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_* | dedup productId | stats values(productId) As "UniqueIds", count(productId) As "NumberOfUniqueProducts"| table NumberOfUniqueProducts, UniqueIds
```
![image](Challenge1i.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top clientipp
```
![image](Challenge2a.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | table action, date_wday | top date_wday limit=3
```
![image](Challenge2b.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | table action, productId | top productId
```
![image](Challenge2c.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday="friday" action=* | table action, productId | top productId
```
![image](Challenge2d.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

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
