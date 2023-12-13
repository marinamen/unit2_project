
<img src="https://github.com/marinamen/unit2_project/blob/main/images/funny-luxurious-paragliding-63q706iov1yzal2m.gif" width=100% height=100%>

*Figure 1 (https://gifdb.com/paragliding)*

# Unit 2: A Distributed Weather Station for ISAK

*Marina Mendieta and Keeler Schriber*

<img src="https://github.com/marinamen/unit2_project/blob/main/images/download.png" width=10% height=10%>

*Figure 2*

## Criteria A: Planning

## Problem definition

*Our client, a local Karuizawa paraglider, seeks safe storage for their equipment, aware that diverse temperature and humidity levels impact storage safety. Employing an Arduino-powered DHT11 sensor, our mission is to precisely measure temperature and humidity. The aim is to advise the client on the suitability of their paragliding storage within the storage room of their Karuizawa house based on these measurements.*

<img src="https://github.com/marinamen/unit2_project/blob/main/images/download%20(1).png" width=10% height=10%>

*Figure 3*


## Proposed Solution
Considering the client requirements an adequate solution includes a low cost sensing device for humidity and temperature and a custom data script that process and anaysis the samples acquired. For a low cost sensing device an adequate alternative is the DHT11 sensor[^1] which is offered online for less than 5 USD and provides adequare precision and range for the client requirements (Temperature Range: 0°C to 50°C, Humidity Range: 20% to 90%). Similar devices such as the DHT22, AHT20 or the AM2301B [^2] have higher specifications, however the DHT11 uses a simple serial communication (SPI) rather than more eleborated protocols such as the I2C used by the alternatives. For the range, precision and accuracy required in this applicaiton the DHT11 provides the best compromise. Connecting the DHT11 sensor to a computer requires a device that provides a Serial Port communication. A cheap and often used alternative for prototyping is the Arduino UNO microcontroller [^3]. "Arduino is an open-source electronics platform based on easy-to-use hardware and software"[^4]. In additon to the low cost of the Arduino (< 6USD), this devide is programable and expandable[^1]. Other alternatives include diffeerent versions of the original Arduino but their size and price make them a less adequate solution.

Considering the budgetary constrains of the client and the hardware requirements, the software tool that I proposed for this solution is Python. Python's open-source nature and platform independence contribute to the long-term viability of the system. The use of Python simplifies potential future enhancements or modifications, allowing for seamless scalability without the need for extensive redevelopment [^5][^6]. In comparison to the alternative C or C++, which share similar features, Python is a High level programming language (HLL) with high abstraction [^7]. For example, memory management is automatic in Python whereas it is responsability of the C/C++ developer to allocate and free up memory [^7], this could result in faster applications but also memory problems. In addition a HLL language will allow me and future developers extend the solution or solve issues proptly.  

**Design statement**

*Our team is developing a program using Arduino and DHT_11 sensors to monitor room humidity and temperature, vital for a paragliding client's equipment storage. Data will be uploaded in real-time to a server for 48 hours and accessed through a secure login. This reliable, validated system aims to complete within four weeks, meeting our client's needs for optimal storage conditions.*

## Success Criteria

[^1]: Industries, Adafruit. “DHT11 Basic Temperature-Humidity Sensor + Extras.” Adafruit Industries Blog RSS, https://www.adafruit.com/product/386. 
[^2]: Nelson, Carter. “Modern Replacements for DHT11 and dht22 Sensors.” Adafruit Learning System, https://learn.adafruit.com/modern-replacements-for-dht11-dht22-sensors/what-are-better-alternatives.   
[^3]:“How to Connect dht11 Sensor with Arduino Uno.” Arduino Project Hub, https://create.arduino.cc/projecthub/pibots555/how-to-connect-dht11-sensor-with-arduino-uno-f4d239.  
[^4]:Team, The Arduino. “What Is Arduino?: Arduino Documentation.” Arduino Documentation | Arduino Documentation, https://docs.arduino.cc/learn/starting-guide/whats-arduino.  
[^5]:Tino. “Tino/PyFirmata: Python Interface for the Firmata (Http://Firmata.org/) Protocol. It Is Compliant with Firmata 2.1. Any Help with Updating to 2.2 Is Welcome. the Capability Query Is Implemented, but the Pin State Query Feature Not Yet.” GitHub, https://github.com/tino/pyFirmata. 
[^6]:Python Geeks. “Advantages of Python: Disadvantages of Python.” Python Geeks, 26 June 2021, https://pythongeeks.org/advantages-disadvantages-of-python/. 
[^7]: Real Python. “Python vs C++: Selecting the Right Tool for the Job.” Real Python, Real Python, 19 June 2021, https://realpython.com/python-vs-cpp/#memory-management. 

1. The solution provides a visual representation of the Humidity and Temperature values inside a dormitory (Local) and outside the house (Remote) for a period of minimum 48 hours. 
1. ```[HL]``` The local variables will be measure using a set of 3 sensors around the dormitory.
2. The solution provides a mathematical modelling for the Humidity and Temperature levels for each Local and Remote locations. ```(SL: linear model)```, ```(HL: non-lineal model)```
3. The solution provides a comparative analysis for the Humidity and Temperature levels for each Local and Remote locations including mean, standad deviation, minimum, maximum, and median.
4. ```(SL)```The Local samples are stored in a csv file and ```(HL)``` posted to the remote server as a backup.
5. The solution provides a prediction for the subsequent 12 hours for both temperature and humidity.
6. The solution includes a poster summarizing the visual representations, model and analysis created. The poster includes a recommendation about healthy levels for Temperature and Humidity.

_TOK Connection: To what extent does ```the use of data science``` in climate research influence our understanding of environmental issues, and what knowledge questions arise regarding the ```reliability, interpretation, and ethical implications``` of data-driven approaches in addressing climate change_

1. How does our use of technology shape our understanding of the environment
2. What responsibilities do we have as technologists when it comes to handling personal data related to our living spaces?
3. What cultural and contextual factors might impact our interpretation of the results, especially when comparing our local readings with those from the campus? 

# Criteria B: Design

## System Diagram **SL**

![SL](https://github.com/comsci-uwc-isak/unit2_2023/assets/53995212/6161f2f6-67c5-4742-9961-e46475376370)

**Fig.1** shows the system diagram for the proposed solution (**SL**). The indoor variables will be measured using an Arduino microprocessor and one sensor DHT11 conencted to the local computer (Laptop) located inside a room. The outdoor variables will be requested to the remote server using a GET request to the API of the server at ```192.168.6.153/readings```. The local values are stored in a CSV database locally.


![HL](https://github.com/comsci-uwc-isak/unit2_2023/assets/53995212/4891d5e9-b8ab-46ed-bd75-b606e25e3383)

**Fig.2** shows the system diagram for the proposed solution (**HL**). The indoor variables will be measured using an Arduino and three DHT11 sensors located inside a room. Three sensors are used to determine more precisely the physical values and include measurement uncertainty. The outdoor variables will be requested to the remote server using a GET request to the API of the server at ```192.168.6.153/readings```. The local values are stored in a CSV database locally and a backup copy will be store in the remote server using the **Weather API**. 


## Record of Tasks
| Task No | Revised Planned Action                                                                                                                                                                                                                      | Revised Planned Outcome                                                                                                                                                                                                          | Time estimate | Target completion date | Criterion |   |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|------------------------|-----------|---|
| 1       | Formulate and document the problem definition on Github  | Clear articulation of the problem on Github           | 15 minutes    | Nov 22                 | A         |   |
| 2       | Compile a comprehensive list of required materials                                                                                                                                                                                            | Complete inventory of necessary materials                                                                                                                                                                                        | 5 minutes     | Nov 24                 | B         |   |
| 3       | Develop and document the design statement                                                                                                                                                                                                     | Concise design statement addressing client needs                                                                                                                                                                                | 20 minutes    | Nov 29                 | A         |   |
| 4       | Justify the chosen solution through a written rationale                                                                                                                                                                                      | Well-explained justification catering to client and developer needs                                                                                                                                                             | 10 minutes    | Nov 29                 | A         |   |
| 5       | Build a device for recording temperature and humidity data                                                                                                                                                                                   | Functional device for accurate temperature and humidity data collection                                                                                                                                                        | 45 minutes    | Nov 30                 | B         |   |
| 6       | Program a system for effective data display from the device                                                                                                                                                                                  | Reliable program for continuous data collection and logging over time                                                                                                                                                          | 20 minutes    | Nov 30                 | B         |   |
| 7       | Develop a signup protocol for server access                                                                                                                                                                                                   | User-friendly server signup process with username and password creation                                                                                                                                                        | 30 minutes    | Dec 2                  | B         |   |
| 8       | Engineer a login mechanism for server access                                                                                                                                                                                                  | Secure and efficient user login system for previously created accounts                                                                                                                                                         | 30 miinutes   | Dec 2                  | B         |   |
| 9       | Establish 8 servers, split between humidity and temperature data                                                                                                                                                                              | Organized network of 8 servers for bi-minute data transmission over a 48-hour period                                                                                                                                            | 15 minutes    | Dec 4                  | B         |   |
| 10      | Code for data transfer to the server                                                                                                                                                                                                         | Seamless server connection for data transmission                                                                                                                                                                               | 25 minutes    | Dec 6                  | B         |   |
| 11      | Program for refined data collection and CSV file export, initiating data collection                                                                                                                                                           | Begin data collection with CSV file integration                                                                                                                                                                                | 40 minutes    | Dec 7                  | B         |   |
| 12      | Enhance coding efficiency within the program                                                                                                                                                                                                  | Streamlined, faster, and more organized program using loops over multiple if statements                                                                                                                                        | 20 minutes    | Dec 9                  | B         |   |
| 13      | Illustrate and explain flow diagrams for solution components                                                                                                                                                                                  | Comprehensive flow diagrams with detailed explanations for various solution aspects                                                                                                                                            | 45 minutes    | Dec 9                  | B         |   |
| 14      | Draft a detailed test plan including functional and non-functional aspects                                                                                                                                                                    | Structured testing procedures with expected outcomes listed on Github                                                                                                                                                          | 45 minutes    | Dec 9                  | B         |   |
| 15      | Focus on criteria C development related to temperature and humidity data recording                                                                                                                                                            | Detailed explanation and process behind data recording and server upload                                                                                                                                                       | 20 minutes    | Dec 10                 | C         |   |
| 16      | Retrieve external sensor data concurrent with internal room recordings                                                                                                                                                                        | Range-specific data extraction from the external sensor corresponding to the 48-hour internal recording window                                                                                                                 | 35 minutes    | Dec 10                 | B         |   |
| 17      | Elaborate on criteria C development related to the setup and sensor locations                                                                                                                                                                 | Visual and descriptive representation of the Raspberry Pi setup and sensor placements                                                                                                                                          | 10 minutes    | Dec 10                 | C         |   |
| 18      | Program for graphical representation of mean temperature and humidity data                                                                                                                                                                     | Graphical outputs for poster and section C inclusion                                                                                                                                                                           | 60 minutes    | Dec 10                 | B         |   |
| 19      | Code a comparative analysis graph of indoor and outdoor temperature and humidity                                                                                                                                                              | Aesthetic and practical graphs depicting indoor-outdoor temperature and humidity correlations using quadratic equations                                                                                                       | 30 minutes    | Dec 11                 | B         |   |
| 20      | Develop visuals and explanations for criteria C, addressing client's first criterion                                                                                                                                                          | Comprehensive visual and textual representation fulfilling client's first criterion                                                                                                                                            | 20 minutes    | Dec 11                 | C         |   |
| 21      | Code for 12-hour temperature prediction post-recording period                                                                                                                                                                                 | Predictive temperature graph for the subsequent 12 hours using specified formula and concepts                                                                                                                                  | 40 minutes    | Dec 11                 | B         |   |
| 22      | Expand on criteria C development for data prediction techniques                                                                                                                                                                               | Clear visual and explanatory content on data prediction methods for the subsequent 12 hours                                                                                                                                    | 30 minutes    | Dec 11                 | C         |   |
| 23      | Code for 12-hour humidity prediction post-recording period                                                                                                                                                                                   | Predictive humidity graph for the following 12 hours post-recording using defined methods and concepts                                                                                                                         | 20 minutes    | Dec 11                 | B         |   |
| 24      | Assemble a comprehensive project and experiment poster                                                                                                                                                                                       | Informative and visually appealing poster depicting the project process and experiment details                                                                                                                                 | 1 hour        | Dec 11                 | D         |   |
| 25      | Detail the use and rationale of CT techniques in code segments                                                                                                                                                                                | Updated Criteria C development part with rationalized use of CT techniques for each client-specific criterion                                                                                                                  | 40 min        | Dec 11                 | C         |   |
| 26      | Develop a program for calculating key statistical values and plotting temperature variation graphs                                                                                                                                           | Informative graph showing temperature variation with standard deviation indicators                                                                                                                                              | 25 min        | Dec 12                 | B         |   |
| 27      | Discuss the logic behind mathematical tool usage for data comparison in criteria C                                                                                                                                                            | Rational explanation of mathematical tools applied for inside-outside temperature and humidity data comparison | 15 min        | Dec 12                | C      |   |                                                                                                                 | 
| 28      | 	Construct an accurate system diagram representing all project components                                                                                                                                                           | Fully-realized system diagram detailing all project elements | 18 min        | Dec 12                 | B         |   |                                        
| 29      | Finalise Poster details                                                                                                                                                            | Rational explanation of mathematical tools applied for inside-outside temperature and humidity data comparison                                                                                                                  | 20 min        | Dec 12                 | A,B,C         |   |
| 30      | Record Video                                                                                                                                                             | Rational explanation of mathematical tools applied for inside-outside temperature and humidity data comparison                                                                                                                  | 15 min        | Dec 13                 | A,B,C        |   |
| 31      | Finalise github repository and details                                                                                                                                                           | To have a finished and successful github repository                                                                                                                | 30 min        | Dec 1                 | A,B,C         |   |
## Test Plan
| Test Type                         | Target                                                                                                                                                                                                          | Procedure                                                                                                                                                                                                                                                                                                                                                                   | Expected Outcome                                                                                                                                                                                                                                                                                                                                                          |
|-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Functional: Integrational testing | Connect to server                                                                                                                                                                                               | 1. Open the program file containing the code developed in order to connect to the server and extract or send data from/to a suitable place 2. Run the program in the terminal 3. Check if data is being collected and uploaded to the .csv file and to the server by looking at the adequate sensor id and see if it matches the id of sensors used for the data collecting | The program should run and print data into the remote server. It should make sure that all sensors are collecting data, and uploading it onto both a .csv file and the remote server.                                                                                                                                                                                     |
| Functional: Integrational testing | Connect to Arduino and Server                                                                                                                                                                                                          | 1. Open crontab terminal 2. Set the desired interval of time between each time the program runs. 3. Wait for the response from the program in order to see if it was succesfully executed.                                                                                                                                                                                  | The program contains a return that is visible and which is stored in a file in order to have proof that the program ran successfully. The program should be able to run in the background even though it is closed. The pogram should continue to run the program without stopping in the middle until crontab is disabled, and the data should continue to be collected. |
| Functional: Integrational testing | Sensor connectivity                                                                                                                                                                                             | 1. Connect all sensors to breadboard which is conneceted to the rasberry pi model 4 connected to the power source 2. Run get_readings function which collects humidity and temperature levels from all 4 sensors and returns a message if they are not properly connected                                                                                                   | The program should return readings for all sensors connected, and if there is an error within any of the sensors, an error message should appear.                                                                                                                                                                                                                         |
| Non-functional: Load testing      | Testing if the program has little lag or glitches due to the amount of time the program is ran for (48 hours). Additionally, see if continously added data (readings) influence the proccessing of the program. | 1. Run the program. 2. Continously check up on the code, every 2-3 hours.                                                                                                                                                                                                                                                                                                   | All data is up to date, and the program is still continously running and recoridng data wihtout any glitches or lag.                                                                                                                                                                                                                                                      |
| Non-functional: Response time     | Testing if the sensor responds quickly to the running program and see how long it takes for the sensor to register and print out the current temperature and humidity                                           | 1. Run the basic program that aims to print the current temperature and humidity the sensor collects.                                                                                                                                                                                                                                                                       | The program returns the swiftly returns the current temperature and humidity the sensor collects without any lag or delay.                                                                                                                                                                                                                                                |
| Non-functional：Code review       | Reviewing if the code has adequate comments, function name, and variable name.As this reviews the quality of the code, there are no inputs.                                                                     | The procedure included a review of the code from a external developer who is not familiar with techniques used in it. The developer then gave feedback on which parts are not understandable and names of which variables are not logical when looking at the purpose of the variable.                                                                                      | The code will include comments explaining what is occuring within the code. Furthermore, the names of variables are simple and it is easy to understand what is their usage in the program     |                                                                                                                                

## Flow Chart
*Simple*
*Medium*

<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-13%20at%2011.50.20.png" width=75% height=75%>
Figure 4: The flow diagram above illustrates the program that is downloaded to the Arduino in C++ code. The program defines the three DHT11 sensors as output devices. Since there aren’t three five-volt outputs pin 12 is set to high to keep sensor 1 powered. It then registers each sensor to allocated ports (4, 7, and 13). The data from the sensors is then collected every five minutes and is displayed in the serial monitor before repeating. 

<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-13%20at%206.05.40%20PM.png" width=75% height=75%>


Figure 5: The flow diagram above illustrates the Python function that retrieves sensor data from the local server. The function uses a known sensor ID value to take that sensor's specific values. It requests the sensor readings from the API using the IP and HTTP get from the server. It creates a dictionary with the readings as the key and an empty list. Then for every value in the sensor readings, it appends the data ti the corresponding list in the dictionary. Finally, if there are no values left it returns the list.

# Criteria C: Development

## List of techniques used
1.Functions

2.Dictionaries & Lists

3.For loops

4.While loops

5.Try and Accept Commands

6.File reading

7.Modifying CSV files

8.Registering and Login into API

9.Sending data to API servers

10.Accessing API data and reading

11.Use of Matplotlib Library and Modificiations

12. Use of Requests Library

## Development
## 1.Client Requested use of 3 sensors placed in different locations within the chosen Room



## 2.Client Requested mathematical representations of the data collected, both the local and remote data collected



## 3.Client Requested a program that worked under low connection to network without major malfunctioning



## 4.Client Requested two copies of Data Collected, one in a local CSV and the second uploaded realtime to API Server.


## 5.Client Requested a 12 hour prediction sampled from the Data Collected the previous 48 hours.

## 6.Client Requested a visual representation of Data collected, both locally and remotely.




## 7.Client Requested a deep research onto Paragliding equipment storage viable conditions


# Criteria D: Functionality

A 7 min video demonstrating the proposed solution with narration
