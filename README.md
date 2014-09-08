# Name

Irfan Nadiadi

# How many points have you earned?

0/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Concrete 3D printer used to build castle](http://www.geekexchange.com/concrete-3d-printer-used-to-build-castle-134449.html)

# Checkpoints

## Checkpoint 1 (5 points)

![image](http://i.imgur.com/XAv3XnH.png)

## Checkpoint 2 (5 points)

![image](http://i.imgur.com/OzjIYK4.png)

## Checkpoint 3 (5 points)

![image](http://i.imgur.com/fnWHDBS.png)

## Checkpoint 4 (5 points)

![image](http://i.imgur.com/9gK2Csu.png)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

WWW1, WWW2, and WWW3 are subdomains of the Buttercupgames website, possibly to act as mirrors. This may be for load balancing to distribute operations between multiple websites, allowing for faster distribution of content.

### Q2. (3 points)

Status=200 represents the HTTP status code '200' which is the standard response for a successful HTTP request. This is in contrast to codes such as '404' - Not found, or '500' - Internal server error, to further describe the result of an HTTP request.

### Q3. (3 points)

Use of the pipe in Splunk queries allows chaining of search queries to allow for more dynamic results. In the tutorial example,  the use of the pipe allowed us to write 'one' query that first found the top customer, then queried for his/her purchases.

### Q4. (3 points)

Retroactively analyzing product purchase behaviors from the raw logs allows you to understand trends with sales, but also helps you better manage your website to ensure maximum uptime and that content delivery is successful. It wouldn't be practical to save every behavior in a structural database because (ideally) the website should be working as expected, so a large amount of the data would carry little significance. We are primarily concerned with finding the instances when something unexpected happened, so it is easier to parse through the raw logs to find those.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://i.imgur.com/4RfdGWr.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count AS "Events"
```
![image](http://i.imgur.com/cbKHGx8.png)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events" count(eval(action="purchase")) as "Purchases"
```
![image](http://i.imgur.com/ZHq374v.png)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events" count(eval(action="purchase")) as "Purchases" count(eval(action="addtocart")) as "AddToCart" count(eval(action="remove")) as "Removes"
```
![image](http://i.imgur.com/PMNAdEM.png)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/cmjSccD.png)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/cmjSccD.png)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX"
```
![image](http://i.imgur.com/OjViMSG.png)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) AS "MAX" min(bytes) AS "MIN" avg(bytes) AS "AVG"
```
![image](http://i.imgur.com/K1XEwJo.png)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats distinct_count(productId) AS "NumberOfUniqueProducts", values(productId)
```
![image](http://i.imgur.com/AnwnzcV.png)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | table clientip, action, productId, date_month, date_mday, date_wday | top clientip
```
![image](http://i.imgur.com/LlOTRAH.png)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | table clientip, action, productId, date_month, date_mday, date_wday | top date_wday limit=3
```
![image](http://i.imgur.com/WAnXkW3.png)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](http://i.imgur.com/WesTCa5.png)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday | table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](http://i.imgur.com/5EMkdAt.png)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday action=purchase | table clientip, action, productId, date_month, date_mday, date_wday | top productId
```
![image](http://i.imgur.com/yShHTCa.png)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action=purchase | table clientip, action, productId, date_month, date_mday, date_wday | top productId limit=1
```
![image](http://i.imgur.com/sNnjQiW.png)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do action=purchase | table clientip, action, productId, date_month, date_mday, date_wday | top productId by date_wday limit=1
```
![image](http://i.imgur.com/lPE4uKT.png)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count
```
![image](http://i.imgur.com/GqxAHUf.png)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) AS UniqueIPs
```
![image](http://i.imgur.com/qiy8atP.png)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart span=6h distinct_count(clientip) AS UniqueIPs
```
![image](http://i.imgur.com/9vWqHcQ.png)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count by host
```
![image](http://i.imgur.com/kNGTlVd.png)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count by productId
```
![image](http://i.imgur.com/vBeDBJX.png)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart count by productId limit=16
```
![image](http://i.imgur.com/o566CJq.png)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip
```
![image](http://i.imgur.com/WQAeRS7.png)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip useother=false
```
![image](http://i.imgur.com/TNRrNT3.png)

## Challenge 3-i (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](http://i.imgur.com/OvOCx3O.png)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET)" | table mymethod, method, _raw |  rex "(?<mymethod>POST)" | table mymethod, method, _raw
```
![image](http://i.imgur.com/BHNfrEA.png)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | rex "(GET|POST) /cart.do\?action=(?<myaction>(purchase|addtocart|remove|view|remove|changequantity|purchase))" | table myaction, action, _raw
```
![image](http://i.imgur.com/2eN3ezF.png)
