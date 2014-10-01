# Name

Sam Korn

# How many points have you earned?

0/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)


# Splunk

## Checkpoint 1 (5 points)

![image](D3Checkpoint1.png)

## Checkpoint 2 (5 points)

![image](D3CheckPoint2.png)

## Checkpoint 3 (5 points)

![image](D3Checkpoint3.png)

## Checkpoint 4 (5 points)

![image](D3Checkpoint4.png)


## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)


### Q2. (3 points)
The HTTP status code 200 means that the request was OK and succeeded.

### Q3. (3 points)
In terminal commands the pipe character is often used when moving data between multiple commands. In Splunk the pipe serves a similar role to narrow down search results and visualize data.

### Q4. (3 points)
The reason why this information has to be retrieved through a raw search of logs is because for large companies keeping this information would take up a lot of data in a structural database. This way the information is always up to date when you are looking for data.

## Challenge 1 (2 points x 8 = 16 points)

### a.
![image](D3Challenge1a.png)

Splunk Command: sourcetype=access_* | stats count

### b.
![image](D3Challenge1b.png)

Splunk Command: sourcetype=access_* | stats count AS "Events"

### c.
![image](D3Challenge1c.png)

Splunk Command: sourcetype=access_* | stats count as Events, count(eval(action="purchase")) as Purchases

### d.
![image](D3Challenge1d.png)

Splunk Command: sourcetype=access_* | stats count as Events, count(eval(action="purchase")) as Purchases, count(eval(action="addtocart")) as AddToCarts, count(eval(action="remove")) as Removes

### e.
![image](D3Challenge1e.png)

Splunk Command: sourcetype=access_* | stats max(bytes)

### f.
![image](D3Challenge1f.png)

Splunk Command: sourcetype=access_* | stats max(bytes) as MAX

### g.
![image](D3Challenge1g.png)

Splunk Command: sourcetype=access_* | stats max(bytes) as MAX, min(bytes) as MIN, mean(bytes) as MEAN

### h.
![image](D3Challenge1h.png)

Splunk Command: sourcetype=access_* | stats dc(productId) as NumberOfUniqueProducts,values(productId) as UniqueProductIds


## Challenge 2 (2 points x 7 = 14 points)

### a. 

![image](D3Challenge2a.png)

Splunk Command: sourcetype=access_* | top clientip

### b. 

![image](D3Challenge2b.png)

Splunk Command: sourcetype=access_* date_wday!="sunday" date_wday != "saturday"| top date_wday limit=3

### c. 

![image](D3Challenge2c.png)

Splunk Command: sourcetype=access_* | top productId

### d. 

![image](D3Challenge2d.png)

Splunk Command: sourcetype=access_* date_wday="friday" | top productId

### e. 

![image](D3Challenge2e.png)

Splunk Command: sourcetype=access_* date_wday="friday" action="purchase"| top productId

### f. 

![image](D3Challenge2f.png)

Splunk Command: sourcetype=access_* action="purchase"| top productId limit=1

### g. 

![image](D3Challenge2g.png)

Splunk Command: sourcetype=access_* action="purchase" | top productId limit=1 by date_wday

## Challenge 3 (2 points x 9 = 18 points)

### a. 

![image](D3Challenge3a.png)

Splunk Command: sourcetype=access_* productId=* | timechart count

### b. 

![image](D3Challenge3b.png)

Splunk Command: sourcetype=access_* productId=* | timechart dc(clientip)

### c. 

![image](D3Challenge3c.png)

Splunk Command: sourcetype=access_* productId=* | timechart dc(clientip) span=1h

### d. 

![image](D3Challenge3d.png)

Splunk Command: sourcetype=access_* productId=* | timechart count by host

### e. 

![image](D3Challenge3e.png)

Splunk Command: sourcetype=access_* productId=* | timechart count by productId

### f. 

![image](D3Challenge3f.png)

Splunk Command: sourcetype=access_* productId=* | timechart count by productId limit=16

### g. 

![image](D3Challenge3g.png)

Splunk Command: sourcetype=access_* productId=* | timechart count by clientip

### h. 

![image](D3Challenge3h.png)

Splunk Command: sourcetype=access_* productId=* | timechart useother=f count limit=10 by clientip

### i. 

![image](D3Challenge3i.png)

Splunk Command: sourcetype=access_* productId=* | timechart span=1h sum(bytes)

## Challenge 4 (4 points x 2 = 8 points)

### a.

![image](D3Challenge4a.png)

Splunk Command: sourcetype=access_* | rex "(?<mymethod>POST)"| rex "(?<mymethod>GET)"|
     table mymethod, method, _raw

### b.

![image](D3Challenge4b.png)

Splunk Command: sourcetype=access_* action | rex "(GET|POST) /cart.do\?action=(?<myaction>\w+[^&])" | table myaction, action, _raw