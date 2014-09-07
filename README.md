# Name

Peyman Mortazavi

# How many points have you earned?

100/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[title-of-the-article](http://link-to-an-interesting-article-about-a-cool-use-of-arduino)

# Checkpoints

## Checkpoint 1 (5 points)

![image](http://imgur.com/ILboudq.png)
![image](http://imgur.com/wnBK5gT.jpg)

## Checkpoint 2 (5 points)

![image](http://imgur.com/NycgF4U.jpg)

It is interesting, as you can see, on "view" and "purchase" actions, most (about 30%) of the errors (200s are filtered out) are 503 (Service Not Available).

## Checkpoint 3 (5 points)

![image](http://i.imgur.com/BSB9r5U.png)

## Checkpoint 4 (5 points)

![image](https://dl-web.dropbox.com/get/Public/Screen%20Shot%202014-09-07%20at%204.34.18%20PM.png?_subject_uid=44502811&w=AADj_FI02ycOZV1rqQ-pOPOTqFoqoGRITwPoIomqUBfwjA)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

They're just three different servers. we have five hosts. "www1-3", "mailsv" and "vendor_sales".
I think "www1-3" are just three different server instances serving online purchase requests. Why three of them? To handle fail-overs and high traffics. We have three instances of the same server application to make sure the web server remains responsive. In addition we have "mailsv" which I think stands for "Mail Service" and "vendor_sales" which represent the sales in stores.

### Q2. (3 points)

"status" field in our data represents the HTTP status code. 200 is "OK" Http status code meaning success. Thus, it lists only successful transactions. Obviously, it filters out vendor sales as well since they don't have "status" field.

### Q3. (3 points)

Simply to follow the convention, you can see the same behavior in other languages/tools, for instance, unix bash script. It's much easier to learn new tools if they all follow the same convention. I think Splunk did it to make it easier for us to learn it.

### Q4. (3 points)

Well, it sounds good if we have all these data structured in our databases BUT sometimes we have relative data from different sources. This actually was a good example, our data is not structured in the same way, how? we have vendor sales which have some information and we have www1-3 that are strucured differently. We have field "status" in www1-3 hosts but not in vendor sales because it simply does not make sense to have "HTTP Status Code" in vendor sales :)

Plus, it may be impossible to analyse these data in real time as it grows very fast. Not to mention, using the database in production may reduce the performance unless we setup a database just for the sake of analytics.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://imgur.com/3De3ICj.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count as "Events"
```
![image](http://imgur.com/30AdDhz.png)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count as "Events", count(eval(action="purchase")) as "Purchases"
```
![image](http://imgur.com/4vgkun9.png)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count as "Events", count(eval(action="purchase")) as "Purchases", count(eval(action="addtocart")) as "AddToCart", count(eval(action="remove")) as "Remove"
```
![image](http://imgur.com/hN5lHCt.png)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://imgur.com/meJlrqS.png)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://imgur.com/meJlrqS.png)

Exact same question is repeated! I suppose it was a mistake.

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as "MAX"
```
![image](http://imgur.com/CElDkxy.png)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as "MAX", min(bytes) as "MIN", avg(bytes) as "AVG"
```
![image](http://imgur.com/DbHNFaY.png)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId) as "NumberOfUniqueProducts", values(productId) as "UniqueProductIds"
```
![image](http://imgur.com/cQi2PfC.png)


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
