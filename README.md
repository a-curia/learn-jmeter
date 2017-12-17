JMeter
======

 

### 14. Functions and Variables

functions : any method that can populate a field in any other element of a test
plan  


syntax :

\${__functionName}

\${__functionName(var1, var2, …..)}

 

variable : container that can store a value which can be referenced by any other
element within the thread. (local to a thread)

 

function - caseSensitive and camelCasing

 

Functions:

1. log - \${__log(“message”)}

2. time -

3. threadNum

4. intSum  


Options - Jmeter Function Helper  


 

 

### 15. How to setup realistic performance test - PACING

Pacing

\- controlled ramp-up and down of virtual users

\- control timing between iterations

\- achieve x iterations in y mins/sec

 

Step 1 - Add Plugin - Stepping Thread Group

Step 2 - Setup load with required settings

Step 3 - Run and validate

 

### 16. TIMERS(How to add Think Time)

Purpose

\- to pause thread (v.user) for some time

\- to add delay between threads

\- to avoid over flooding the server and achieve real time behaviour by pacing
the load

(to simulate v. user’s THINK TIME)

 

Constant Timer

Uniform Random Timer

 

Random Delay Max

Constant Delay Offset

 

formula: 0.X \* Random Delay Max + Constant Delay Offset

X : 0-9

example: 0.X \* 100 + 0

0 - 99 milli sec

 

### 17. Parameterize FTP test - to upload files with different names to FTP server

 

Step 1 : Config-\>add CSV Data Set Config

Step 2 : create a csv file and provide its location in CSV Data Set Config

Step 3 : parameterize FTP PUT request to take value from csv file

Step 4 : Run and Validate

 

### 18. How to run Scheduled + Sequential execution

 

HOW TO RUN A TEST FOR SPECIFIC DURATION

Thread Group - Forever - Scheduler - Duration

 

HOW TO RUN PERFORMANCE TEST SEQUENTIALLY

Test Plan - Run Thread Group Consecutively

 

HOW TO ADD WEBSITES SEQUENTIALLY TO A PERFORMANCE TEST

Thread Group - Forever - Scheduler - Duration + Startup Delay

\______________________________________________\_

 

HOW TO RUN A TEST FOR SPECIFIC DURATION

Thread Group - Forever - Scheduler - Duration

 

Step 1 : Thread Group - make loop count = forever

 

Step 2 : Select Scheduler checkbox

 

Step 3 : Add duration (sec)

 

———————————————————————————

 

HOW TO RUN PERFORMANCE TEST SEQUENTIALLY

Test Plan - Run Thread Group Consecutively

 

Step 1 : Test Plan - select Run Thread Groups consecutively

 

———————————————————————————

 

HOW TO ADD WEBSITES SEQUENTIALLY TO A PERFORMANCE TEST

Thread Group - Forever - Scheduler - Duration + Startup Delay

 

Step 1 : Add duration (max) to first thread group - 30 sec

 

Step 2 : To consecutive thread groups add delay

 

example (for a 30 sec test plan):

1st Thread Group : delay = 0 sec  \|  duration = max duration of the test = 30
sec

 

2nd Thread Group : delay = 10 sec  \|  duration = max - delay = 30 - 10 = 20 sec

 

3rd Thread Group : delay = 20 sec  \|  duration = max - delay = 30 - 20 = 10 sec

 

 

### 19. Correlation(with Regular Expression Extractor)

 

What is Correlation?: the process of extracting some value from the response of
a step and referring it into the request of other subsequent step is called
correlation; happens at runtime so we call it dynamic referencing

 

Extract dynamic value from the response of a step =\> refer the extracted value
in the request of a subsequent step

 

Why is it Required?: in a Test there may be needed to refer values from earlier
steps which cannot be determined prior to test execution as these are generated
at runtime; eg. session Id from one page to another

 

How to use Regular Expression Extractor for Correlation

Step 1 : Create a Test Plan where you want to do dynamic referencing in JMeter

Step 2 : Add Regular Expression Extractor in the Step from where response
value(s) needs to be extracted

Step 3 : Refer the extracted value (referred by Reference Name) into a
subsequent step

Step 4 : Run and validate

 

### 20. TEMPLATES

\- What are JMeter Templates

\- How to use Templates

\- How to create your own Template

 

1 What are JMeter Templates

 

Reusable project scripts

 

User can select any template and it will generate a Test Plan with basic and
necessary components

\___________________________________________\_

 

2 How to use Templates

 

File - Templates - select a template and start building over it.

\___________________________________________\_

 

3 How to create your own Template

 

Step 1 : save your test plan as .jmx file

 

Step 2 : place the .jmx inside jmeter/bin/templates

 

Step 3 : edit templates.xml file to add your template

 

Step 4 : restart JMeter and check

\___________________________________________\_

 

templates.xml

 

template

isTestPlan=”true”     :    template will create a new test plan

isTestPlan=”false”    :    templat will be merged into existing test plan

name : Name of the template

fileName  : location of .jmx file

description  : description will be displayed in html

 

 

### 21. How to use Test Script Recorder

 

1. What is Test Script Recorder

2. How to record your test with it

 

helpful tips

 

\_________________________________________\_

 

1 What is Test Script Recorder

 

is a workbench element

used to record user actions on browser

 

\_________________________________________\_

 

2 How to record with Test Script Recorder

 

Step 1 : Add Test Script Recorder in WorkBench

WorkBench - Non-Test Elements - HTTP(S) Test Script Recorder

 

Step 2 : In a Thread Group add

Logic Controller - Recording Controller

 

Step 3 : Add the values in Test Script Recorder parameters

 

Step 4 : Set Browser Proxy Configuration

 

Step 5 : Install the certificate in your browser (if required)

 

Step 6 : Start Recording

 

Step 7 : Run and validate

 

\_________________________________________\_

 

Helpful Tips:

 

Use JMeter’s inbuilt Recording template

You can use the in-built template - Recording

 

to start quickly

to save time and effort

 

 

### 22. Test File Uploads

 

1. How to create test for file upload

2. How to record test for file upload

\___________________________________\_

 

1  How to create test for File Upload

 

Step 1 : Create a Test Plan - Thread Group - HTTP Request

 

Step 2 :  Add values in HTTP Request sampler

 

Step 3 : Add File Upload details

 

Step 4 : Add Listeners to view results

 

Step 5 : Run and Validate

 

\___________________________________\_

 

2  How to record test for File Upload

 

Step 1 : Add Template - Recording

 

Step 2 : Provide a port number (e.g. 8181)

 

Step 3 : Set browser to listen to this port

 

Step 4 : Start Recording

 

Step 5 : Filter the samples you need from recorded samples

 

Step 6 : Run and Validate

\_________________________________________\_

 

Helpful Tips:

 

In case you face any issues..

Check the following :

 

Method is POST

Use multipart/form-data for POST Box is checked

File location \| Parameter \| Mime Type  are correct

Check the logs for any other error

 

 

### 23. How to test File Download

 

Today we will learn:

 

1. How to create test for file download

 

Step 1: Add Thread Group - HTTP Request sampler

 

Step 2 : Add values in HTTP Request sampler

 

Step 3 : Add Listeners to view results

 

Step 4 : Add Listener - Save Responses to a file

 

Step 5 : Add values to this Listener

 

Step 6 : Run and Validate

\_____________________________________\_

 

Helpful Tips

 

How to avoid overwriting downloaded files.

in a multi-user test

 

Use function : \${__threadNum} as Prefix

 

### 24. How to DEBUG

 

1. How to debug and fix errors

2. How to use Debug Sampler

\___________________________\_

 

Step 1 : Analyse with Listener - View Results Tree

 

Step 2 : Analyse information in Log Viewer

 

Step 3 : Add Listner - Debug Sampler

 

\___________________________\_

 

Helpful Tips

 

How to use Debug PostProcessor

Enable Debug for elements

Using external plugins for Debugging

 

### 25. How to record login test

 

Step 1 : add blazemeter plugin to chrome browser

 

Step 2 : start blazemeter plugin and login to blazemeter

 

Step 3 : Record your scenario - Stop Recording - Export .jmx

 

In case you find jmx option disabled export as json and use this link to convert
to jmx

http://converter.blazemeter.com/

 

Step 4 : Import imx file in JMeter

 

Step 5 : Add listeners

 

Step 6 : Run and validate
