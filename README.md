# Name

Ian Ker-Seymer

# How many points have you earned?

100/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Build a Wireless Home Security System With an Arduino](http://lifehacker.com/build-a-wireless-home-security-system-with-an-arduino-1619435213)

# Checkpoints

## Checkpoint 1 (5 points)

![image](https://www.dropbox.com/s/7gva9czsfyzjtkk/Screenshot%202014-09-07%2019.44.11.png?dl=1)

## Checkpoint 2 (5 points)

![image](https://www.dropbox.com/s/2au4zft3s7nr91g/Screenshot%202014-09-07%2019.52.04.png?dl=1)

## Checkpoint 3 (5 points)

![image](https://www.dropbox.com/s/tkun8s6dg5bwj8k/Screenshot%202014-09-07%2019.56.06.png?dl=1)

## Checkpoint 4 (5 points)

![image](https://www.dropbox.com/s/i33923z0yu093vw/Screenshot%202014-09-07%2020.07.32.png?dl=1)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

It identifies which server was accessed. In large web applications, servers will often be
ditrubuted so this is used to identify which Apache2 server was used to respond to the request.

### Q2. (3 points)

status=200 is the HTTP response that Apache gave back to the client. A 200 status means 'OK'.

### Q3. (3 points)

Piping is typically used as a method of inter-process communication. When using command line tools,
this is a common practice as it opens a shared file/memory space for the processes. In Splunk, it
takes the output of one command (which will often be used to restrict the range of data), and
that output will be used as input for another command. Some of the commands remind me of a
refined version of 'grep.'

### Q4. (3 points)

One would analyze 'product purchase' to be able to confidently make judgements about product sales
Putting the data into a structured database can be a hassle in comparison to this method.
Firstly, the data is already somewhat structured in the form Apache logs, and can thus be parsed
relatively easily. Secondly, when you define schemas for data upfront, often you have to know
what type of queries you will be running on the data in order to optimize performance. So if you
build the wrong structured schema, you are out of luck. Secondly, the data does not need strict
validation, so creating a SQL table does not bring the benefit of having well defined data.
Thirdly, the data can change over time, and you do not want to have to update your scheme constantly
due to ever-changing inputs.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](https://www.dropbox.com/s/m8o71fr06hgwhy0/Screenshot%202014-09-07%2021.14.52.png?dl=1)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count as "Events"
```
![image](https://www.dropbox.com/s/a2rmisumhau3zh3/Screenshot%202014-09-07%2021.14.31.png?dl=1)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count as "Events", count(eval(action="purchase")) AS "Purchased"
```
![image](https://www.dropbox.com/s/awyoz955iio91kc/Screenshot%202014-09-07%2021.14.10.png?dl=1)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count as "Events", count(eval(action="purchase")) AS "Purchased", count(eval(action="addtocart")) AS "AddToCarts", count(eval(action="remove")) AS "Removes"
```
![image](https://www.dropbox.com/s/08nvo9rf27wgpvg/Screenshot%202014-09-07%2021.13.34.png?dl=1)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](https://www.dropbox.com/s/2iiar36rvleutc5/Screenshot%202014-09-07%2021.12.59.png?dl=1)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](https://www.dropbox.com/s/2iiar36rvleutc5/Screenshot%202014-09-07%2021.12.59.png?dl=1)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) AS MAX
```
![image](https://www.dropbox.com/s/9hb7f3rnzdfalts/Screenshot%202014-09-07%2021.16.17.png?dl=1)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as MAX, min(bytes) AS MIN, avg(bytes) AS AVG
```
![image](https://www.dropbox.com/s/ewaxapdk5sdh8db/Screenshot%202014-09-07%2021.17.19.png?dl=1)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats dc(productId) AS NumberOfUniqueProducts, values(productId) AS UniqueProductIds
```
![image](https://www.dropbox.com/s/7ck1pftqw8o3acs/Screenshot%202014-09-07%2021.26.47.png?dl=1)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do |
  top clientip
```
![image](https://www.dropbox.com/s/hhmxx8r37ky3efy/Screenshot%202014-09-07%2021.46.28.png?dl=1)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do |
  top limit=3 date_wday
```
![image](https://www.dropbox.com/s/ewbal4mmi8t8g0s/Screenshot%202014-09-07%2021.47.54.png?dl=1)

## Challenge 2-c (2 points)
```
sourcetype=access_* action=* | top productId
```
![image](https://www.dropbox.com/s/62ndg2yddz766ev/Screenshot%202014-09-07%2022.28.33.png?dl=1)


## Challenge 2-d (2 points)
```
sourcetype=access_* date_wday=friday action=* | top productId
```
![image](https://www.dropbox.com/s/tw0u1w99wsso5sg/Screenshot%202014-09-07%2022.21.13.png?dl=1)

## Challenge 2-e (2 points)
```
sourcetype=access_* date_wday=friday action=purchase | top productId
```
![image](https://www.dropbox.com/s/za1o4tvulp56h9n/Screenshot%202014-09-07%2022.31.30.png?dl=1)

## Challenge 2-f (2 points)
```
sourcetype=access_*  action=purchase | top limit=1 productId
```
![image](https://www.dropbox.com/s/5hihlzq67dcux72/Screenshot%202014-09-07%2022.33.31.png?dl=1)

## Challenge 2-g (2 points)
```
sourcetype=access_* action=purchase | top limit=1 productId by date_wday
```
![image](https://www.dropbox.com/s/m9d48k1en1rtvhs/Screenshot%202014-09-07%2022.44.33.png?dl=1)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count(action) BY dates
```
![image](https://www.dropbox.com/s/xzabeknjrcz899h/Screenshot%202014-09-07%2022.51.12.png?dl=1)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart dc(clientip) BY dates
```
![image](https://www.dropbox.com/s/u7nygv7lfpy7b39/Screenshot%202014-09-07%2022.53.31.png?dl=1)

## Challenge 3-c (2 points)
```
sourcetype=access_* [fill-in-the-rest]
```
![image](https://www.dropbox.com/s/i3x7ntp7fumb9ap/Screenshot%202014-09-07%2022.55.28.png?dl=1)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count(action) by host
```
![image](https://www.dropbox.com/s/zv6or56ggs5n3fi/Screenshot%202014-09-07%2022.59.58.png?dl=1)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=*| timechart count(action) by productId
```
![image](https://www.dropbox.com/s/2mu0rg265tpwi2i/Screenshot%202014-09-07%2023.08.13.png?dl=1)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=*| timechart count(action) by productId limit=16
```
![image](https://www.dropbox.com/s/y2aj7e4mznynkbo/Screenshot%202014-09-07%2023.09.24.png?dl=1)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=*| timechart count by clientip
```
![image](https://www.dropbox.com/s/tweicbahinwdndc/Screenshot%202014-09-07%2023.12.18.png?dl=1)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=*| timechart count by clientip limit=10 useother=false
```
![image](https://www.dropbox.com/s/xqsp7onomdsxy6g/Screenshot%202014-09-07%2023.14.06.png?dl=1)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=*| timechart sum(bytes) span=hours
```
![image](https://www.dropbox.com/s/bf8z9jci8x96br8/Screenshot%202014-09-07%2023.15.43.png?dl=1)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>(GET|POST))" |
     table mymethod, method, _raw
```
![image](https://www.dropbox.com/s/mvv3s5q1e1cjkaw/Screenshot%202014-09-07%2023.21.10.png?dl=1)

## Challenge 4-b (4 points)
```
sourcetype=access_* action |
    rex "(GET|POST) /cart.do\?action=(?<myaction>(addtocat|purchase|view|remove|changequantity))" |
        table myaction, action, _raw
```
![image](https://www.dropbox.com/s/fyqcwbv6u69hhbz/Screenshot%202014-09-07%2023.24.18.png?dl=1)
