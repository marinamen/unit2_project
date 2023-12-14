

   
<img src="https://github.com/marinamen/unit2_project/blob/main/images/funny-luxurious-paragliding-63q706iov1yzal2m.gif" width=100% height=100%>

*Figure 1 (https://gifdb.com/paragliding)*
 
   ༘⋆ ❅ ･:*:｡ ❆༄༄
   
   *weather station*
   
   ༘⋆ ❅ ･:*:｡ ❆༄༄

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
## 1.Client Requested use of 3 sensors placed in different locations within the chosen Room.

In response to the client's request for comprehensive temperature and humidity monitoring within a designated room, we strategically deployed three DHT11 sensors at varied locations to ensure a broad and precise data collection. The DHT11 sensors, known for their reliability in measuring temperature and humidity, were placed in distinct parts of the room to capture environmental variations effectively.

Sensor Placement and Rationale:

*Sensor 1:* Located near the entrance of the room, this sensor is positioned to capture the temperature and humidity levels that might be influenced by external factors, such as air coming in from outside the room.

<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-14%20at%2001.20.36.png" width=35% height=35%>
Fig1.1


*Sensor 2:* Placed in the central part of the room, this sensor is intended to measure the average room conditions, providing a balanced view of the environmental factors at play within the space.

<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-14%20at%2001.20.30.png" width=35% height=35%>
Fig.1.2


*Sensor 3:* Situated near the window or another heat source, this sensor aims to detect any variations in temperature and humidity caused by sunlight or appliances, offering insights into how external elements can impact the room's climate.

<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-14%20at%2001.20.26.png" width=35% height=35%>
Fig.1.3




**Photographic Documentation:**

To complement our setup, we've included three photographs below, each depicting the precise location of one of the sensors. These images provide a visual reference to the strategic placement of the sensors, illustrating our methodical approach to capturing a comprehensive and accurate representation of the room's environmental conditions.

**Purpose and Benefits:**

This multi-sensor approach enables a thorough analysis of the room's microclimate. By comparing data from different parts of the room, we can identify patterns, anomalies, or environmental gradients, leading to more informed decisions about climate control and room utilization.
Through this setup, we not only cater to the client's specific requirements but also enhance the overall accuracy and reliability of our environmental monitoring within the room.




## 2.Client Requested mathematical representations of the data collected, both the local and remote data collected.

>Our team fulfilled this request for the following: comparison of the humidity and temperature levels inside and outside the student room, prediction of humidity level during the subsequent 12 hour period after the recordings took place. We did this in 2 differing methods:

The development of the part of the program that fulfilled this criteria was first decomposed into 2 parts. Showing relations using mathematical modeling, and showing predictions using mathematical modeling. The code for the relations between data (Code 1.3) was developed by decomposing it into two subplots showing the relation between humidities and temperatures separately. Quadratic formula was aquired using np.polyfit and then put into an algorithm which would collect it into the list allowing the cretion of non-linear graphs.
The first is shown below, we

The development of the part of the program that fulfilled this criteria was first decomposed into 2 parts. Showing relations using mathematical modeling, and showing predictions using mathematical modeling. The code for the relations between data (Code 1.3) was developed by decomposing it into two subplots showing the relation between humidities and temperatures separately. Quadratic formula was aquired using np.polyfit and then put into an algorithm which would collect it into the list allowing the cretion of non-linear graphs.

<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-14%20at%2008.08.08.png" width=65% height=65%>
Fig2.1 Displays the subsequent 12 hour Linear prediction for the Indoor Temperature


<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-14%20at%2008.07.59.png" width=35% height=35%>
Fig2.2 Displays the subsequent 12 hour using Polynomial fitting at 3rd degree for the Outdoor Humidity


<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-14%20at%2008.08.42.png" width=35% height=35%>

*Fig.3.6*

<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-14%20at%2001.20.36.png" width=35% height=35%>

*Fig.3.7*
<img src="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-14%20at%2001.20.36.png" width=35% height=35%>



## 3.Client Requested a program that worked under low connection to network without major malfunctioning
Since the program needed to run under low connection to the network without malfunctioning. We implemented some safe fails. So that if the network doesn’t work or the server times out the data has multipletries to upload the data. To make sure the data is configured correctly the code and not data points are missing we use try and except command. The try tests to make sure the decoded data string is a valid float. If it is valid the program continues. If it doesn’t it excepts the value error and prints that the line is in an invalid data line then continues pulling up the next line. Figure(4.1) To make sure the server doesn’t time out after logging in once we implemented within the if statement the login cookie again so that if the device has lost connection with the server, it can reconnect before appending the sensor data. Figure(4.2)

Figure (4.1) Checks if there is an invalid data format from the decode Ardunio data and skips that line or continues the program
```.py
try:
   temperature = float(decoded_data[temperature_start:temperature_end].strip())
   humidity = float(decoded_data[humidity_start:humidity_end].strip())
except ValueError:
   print("Invalid data format. Skipping line.")
   continue
```
Figure (4.2) Part of the code that Appends data specifically the part where the failsafe reconnect to the server is
```.py
if len(sensor_data) == 3:
   with open(fileName, "a") as file:
       file.write(f"{sensor_data['1'][0]},{sensor_data['1'][1]},"
                  f"{sensor_data['2'][0]},{sensor_data['2'][1]},"
                  f"{sensor_data['3'][0]},{sensor_data['3'][1]},"
                  f"{datetime.datetime.now()}\n")
   answer = requests.post(f'http://{ip}/login', json=user)
   print(answer.json())
   cookie = answer.json()["access_token"]


   record = {'sensor_id': 80, 'value': f"{sensor_data['1'][0]}"}
   answer = requests.post(f'http://{ip}/reading/new',
                          json=record,
                          headers={'Authorization': f'Bearer {cookie}'})
```



## 4.Client Requested two copies of Data Collected, one in a local CSV and the second uploaded realtime to API Server.
To ensure that the data from the indoor sensors is saved, the client requested that the data be kept in a CSV along with being uploaded to a local server API. Using the library date time we can track every time mark it uploads to the server. We did this by creating a user with the local server and gaining a cookie access token. The cookie allowed us to add data to the server. The purpose of using a cookie to log in was to maintain security and prevent unauthorized access. Figure (5.1) Next, we implemented a while loop in our program to continuously check for data from the Arduino. The data was decoded using a UTF 8 decoder that utilized the ASCII table.Figure(5.2) The program then used an if statement to check if the line contained any sensor data. The sensor data under the sensor ID was then stored in a dictionary where the keys were the sensor number, and the values were Temperature and Humidity. Now, using an if statement, for every sensor data length equal to three. The values of that sensor were put into the local server under that sensor ID, along with the sensor values being appended to the CSV file and with time stamps. Once those values are put into the server/CSV the dictionary resets and takes the next line of data from the Ardunio. See Figure(5.3)



Figure (5.1)
```.py
user = {'username':"keelarina","password":"iloveroky"}
#login


answer = requests.post(f'http://{ip}/login', json=user)
print(answer.json())
cookie = answer.json()["access_token"]
```
Figure (5.2)
```.py
while line <= samples:
 
   # Reads data from the serial port that connected to the Ardunio
   data = ser.readline()


   # Decodes the binary data into a string using UTF-8 
   decoded_data = data.decode('utf-8', errors='ignore').strip()


   # Prints decoded data
   print(decoded_data)
```
Figure(5.3)
```.py
if len(sensor_data) == 3:
   with open(fileName, "a") as file:
       file.write(f"{sensor_data['1'][0]},{sensor_data['1'][1]},"
                  f"{sensor_data['2'][0]},{sensor_data['2'][1]},"
                  f"{sensor_data['3'][0]},{sensor_data['3'][1]},"
                  f"{datetime.datetime.now()}\n")
   answer = requests.post(f'http://{ip}/login', json=user)
   print(answer.json())
   cookie = answer.json()["access_token"]


   record = {'sensor_id': 80, 'value': f"{sensor_data['1'][0]}"}
   answer = requests.post(f'http://{ip}/reading/new',
                          json=record,
                          headers={'Authorization': f'Bearer {cookie}'})
   record = {'sensor_id': 75, 'value': f"{sensor_data['1'][1]}"}
   answer5 = requests.post(f'http://{ip}/reading/new',
                          json=record,
                          headers={'Authorization': f'Bearer {cookie}'})
   print(answer5.json())
   record = {'sensor_id': 76, 'value': f"{sensor_data['2'][0]}"}
   answer1 = requests.post(f'http://{ip}/reading/new',
                          json=record,
                          headers={'Authorization': f'Bearer {cookie}'})
   print(answer1.json())
   record = {'sensor_id': 77, 'value': f"{sensor_data['2'][1]}"}
   answer2 = requests.post(f'http://{ip}/reading/new',
                          json=record,
                          headers={'Authorization': f'Bearer {cookie}'})
   print(answer2.json())
   record = {'sensor_id': 78, 'value': f"{sensor_data['3'][0]}"}
   answer3 = requests.post(f'http://{ip}/reading/new',
                          json=record,
                          headers={'Authorization': f'Bearer {cookie}'})
   print(answer3.json())
   record = {'sensor_id': 79, 'value': f"{sensor_data['3'][1]}"}
   answer4 = requests.post(f'http://{ip}/reading/new',
                          json=record,
                          headers={'Authorization': f'Bearer {cookie}'})
   print(answer4.json())


   # Resets the dictionary
   sensor_data = {}
```
Figure(5.4): CSV FILE Temp 1, Humidity 1, Temp 2, Humidity 2, Temp 3, Humidity 3, Time Uploaded/saved to CSV

<img src ="https://github.com/marinamen/unit2_project/blob/main/images/Screenshot%202023-12-14%20at%2010.32.10%20AM.png" width=35% height=35% >
## 5.Client Requested a 12 hour prediction sampled from the Data Collected the previous 48 hours.

## 6.Client Requested a visual representation of Data collected, both locally and remotely.




## 7.Login and Register System

The UWC ISAK Weather Station Server operates under specific rules and terminations. 

Our code implementation involved several steps: initially, we registered a new user and established a password. 
```.py
def register(ip="192.168.6.153",):
  new_user = {'username': '#####', 'password':'#####'}
  req = requests.post(url+"/register", json=new_user)
  print(req.json())
```
Following this, we logged into the server using the newly created credentials

```.py
def serverLogin(ip="192.168.6.153", user={"username": "keelarina", "password": "iloveroky"}):
    req = requests.post(f"http://{ip}/login", json=user)
    print(req.json())
    cookie = req.json()["access_token"]
    return {"Authorization": f"Bearer {cookie}"}
```

# Criteria D: Functionality

A 7 min video demonstrating the proposed solution with narration
