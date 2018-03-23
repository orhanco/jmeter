# jmeter

This script is intended to call requests continuously.
The goal is not to load in from a performance testing perspective.
Results being sent to influx and visualized through a Grafana dashboard.


This JMeter script contains some config elements:
 - HTTP Cookie Manager: default
 - HTTP Authorization Manager: default
 - HTTP Cache Manager: default
 - HTTP Header manager: default
 - HTTP Request Defaults: https + default server name
 - User Defined Variables; the application URL as a parameter
 - Backend Listener; rocks.nt.apm.jmeter.JMeterInfluxDBBackendListenerClient

There is one simple Thread Group which has;
 - a Loop controller
 - 3 api calls:
 	- a POST request
 		- with a response assertion
 		- a specific HTTP Header Manager
 		- a Random Variable
 		- and a JSON Extractor
 	- a GET request
 		- with a response assertion
 	- a DELETE request
 		- with a response assertion

The action to be taken after a sample error is to continue.

The load distribution is set a below:
	- Number of Threads = 1
	- Ramp-up period in seconds = 1
	- Loop count = Forever

The script has been tested in JMeter 3.1, 3.3 and 4.0.

