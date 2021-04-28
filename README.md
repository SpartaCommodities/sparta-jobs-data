# Data Exercise

The goal of this exercise is to design the data storage to store and organise the data we receive from some feeds and that we generated from our own app, to be used by our system to plot historic charts.

Our final need is to feed a Trading charts library to plot the data our system is generating, the client will send the following data configuration for the system to provide the data:

    - Key to be ploted
    - Segment of time to be ploted:
        - End: timestamp of the hour to start ploting
        - Time_ploted: duration to be shown of data, in hours (minimum one hour)
    - The ranges of time to plot the data can be: 5 minutes, 15 minutes, 1 hour, 4 hours, 1 day.


The values that the system needs to return for every segment of time are: 

    - Timestamp: Time the read was generated
    - Open: First value of the time segment
    - Close: Last value of the time segment
    - Max: Maximum value of the time segment
    - Min: Minimum value of the time segment

**Example: **
The client could request the following configurations to the Backend:
    - Key: Crude market value
    - Time to be shown: From now to 1 year in the past
    - Ranges: Per day

Data to be sent:

    - Timestamp: 27th April 2020
    - Open: 100.0 (value of crude at the begining of the day of 27th April 2020)
    - Close: 150.0 (value of crude at the end of the day of 27th April 2020)
    - Max: 170.0 (maximum value of crude of the day of 27th April 2020)
    - Min: 90.0 (minimum value of crude of the day of 27th April 2020)

    - Timestamp: 28th April 2020
    - Open: 170.0 (value of crude at the begining of the day of 28th April 2020)
    - Close: 150.0 (value of crude at the end of the day of 28th April 2020)
    - Max: 190.0 (maximum value of crude of the day of 28th April 2020)
    - Min: 80.0 (minimum value of crude of the day of 28th April 2020)

...

    - Timestamp: 27th April 2021
    - Open: 270.0
    - Close: 350.0
    - Max: 362.0 
    - Min: 240.0 

The keys to store into the data storage, comes from different sources:

    - The live market data is feeded into a Kafka Topic, and this is received in almost real time, around 500 readings, per key, per second. There are around 3000 different keys being received.
    - Our Blender calculated data is generated every 15 minutes for 300 different keys.
    - Out Freight information, is generated every 6 hours for 200 keys.

The work to be done for this exercise is:

    1. Provide a Data Storage solution that can organise the data into the most efficient way, for the reading to be as fast as possible for the backend system. If there are different options available with pros and cons, please, define them for us to take a decission on the best system to chose.

    2. Provide a Data flow design to connect our systems to the Data Storage solution, so we are sure that no data is ever lost, and in case of live data the lag is the minimum possible.

    3. Provide a Data Structure for the prefered Data Storage system chosen in the first step, so the querying of the data is the fastest as possible for the backend to retrieve the data given the parameters given by the client.


To give your answer, generate a report in your favourite format for us to decide a solution for the system. Over that report we will discuss in a pair-session about the solution chosen, and the thoughts to reach that solution.




