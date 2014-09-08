# Name

Daniel Nolan

# How many points have you earned?

100/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Sound Reactive LED Strip](http://www.instructables.com/id/Sound-Reactive-LED-strip/?ALLSTEPS)
My group in another class is going to make improvements to this concept for a project so if any of you have experience with this maybe you could give me some of your words of wisdom. Any thoughts on this idea would be greatly appreciated!
# Checkpoints

## Checkpoint 1 (5 points)

![image](http://imgur.com/fqBR018.png)


## Checkpoint 2 (5 points)

![image](http://imgur.com/RccD6Dz.png)
![image](http://imgur.com/W8UmlNv.png)

## Checkpoint 3 (5 points)

![image](http://imgur.com/w1R05Ls.png)
![image](http://imgur.com/wrXC6bB.png)

## Checkpoint 4 (5 points)

![image](http://imgur.com/KkZayvp.png)
![image](http://imgur.com/WTLTi3a.png)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

The www1-www3 host names exist in the domain name and are used to seperate a website into subdomains. The www2 and www3 websites can be mirrors or used for server load balancing also.

### Q2. (3 points)

The "Status=200" part of the code makes sure we are searching for non-error data in our queries. This is equal to "success" in our search data, meaning there should be no data with errors.

### Q3. (3 points)

The pipeline function allows us to run more than one function at a time per search. This greatly helps us find specific data when there are large amounts of data to search through. 

### Q4. (3 points)

We need to analyze “product purchase” behaviors from raw server logs retroactively because websites that have not created a database yet only have raw server logs to access. In some cases, if there is new data, we must use the raw server logs to check and see if these files are new and must be input into our database.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://imgur.com/6sAUlMp.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count as "Events"
```
![image](image.png?raw=true)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events", c(eval(action="purchase")) AS "Purchased"
```
![image](http://imgur.com/yC6JJXl.png)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events", c(eval(action="purchase")) AS "Purchased", c(eval(action="addtocart")) AS "Add to Cart",c(eval(action="remove")) AS "Remove"
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
sourcetype=access_* | stats max(bytes) AS "MAX", min(bytes) AS "MIN", avg(bytes) AS "AVG"

```
![image](image.png?raw=true)

## Challenge 1-i (2 points)
```
sourcetype=access_* stats  dc(productId) as NumberofUniqueProducts ,values(productId) AS UniqueProductIds
```
![image](image.png?raw=true)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top date_wday limit=3
```
![image](.png)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | top productId
```
![image](image.png?raw=true)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday | top productId
```
![image](image.png?raw=true)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday action=purchase | top productId
```
![image](image.png?raw=true)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do action=purchase | top productId limit=1
```
![image](image.png?raw=true)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action=purchase| table clientip, action, productId, date_month, date_mday, date_wday | top limit=1 productId
```
![image](image.png?raw=true)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do action=purchase | table clientip, action, productId, date_month, date_mday, date_wday | top limit=1 productId by date_wday
```
![image](image.png?raw=true)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by host
```
![image](image.png?raw=true)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart dc(clientip) AS "UniqueIPs"
```
![image](image.png?raw=true)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart span=1h dc(clientip) AS "UniqueIPs"
```
![image](image.png?raw=true)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count by host
```
![image](image.png?raw=true)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count by productId
```
![image](image.png?raw=true)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart limit=0 count by productId
```
![image](image.png?raw=true)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip
```
![image](image.png?raw=true)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip useother=false
```
![image](image.png?raw=true)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=* | timechart span=1h sum(bytes)
```
![image](image.png?raw=true)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>(GET|POST))" | table mymethod, method, _raw
```
![image](image.png?raw=true)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | 
    rex "(GET|POST) /cart.do\?action=(?<myaction>[a-z]*)" |
    table myaction, action, _raw
