# Name

Chris Wittenberg

# How many points have you earned?

56/100

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
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 1-d (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

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
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 2-b (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](image.png?raw=true)

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
