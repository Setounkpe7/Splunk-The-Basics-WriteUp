# Splunk: The Basics | TryhackMe WriteUp
Splunk is one of the most used SIEM tools to collect, analyze and correlate logs from network and machines in realtime. In this room, we explore the basics of Splunk and its functionalities, and how it provides better visibility of network activities and helps speed up detection. This room and most of the information below come from the room [Splunk: The Basics](https://tryhackme.com/room/splunk101) of TryHackMe.

We start by connecting to a virtual machine which create a Splunk instance that we'll use in the lab.
![Connecting to Virtual Machine](assets/images/splunk_basic_connect_virtual_machine.png)


## Task 3: Splunk Components
Splunk has three main components: Forwarder, Indexer, and Search Head. 

### Splunk Forwarder
Splunk Forwarder is a lightweight agent installed on the endpoint intended to be monitored, and its main task is to collect the data and send it to the Splunk instance.

### Splunk Indexer
Splunk Indexer plays the main role in processing the data it receives from forwarders. It parses and normalizes the data into field-value pairs, categorizes it, and stores the results as events, making the processed data easy to search and analyze.

### Search Head
Splunk Search Head is the place within the Search & Reporting App where users can search the indexed logs. The searches are done using the SPL (Search Processing Language), a powerful query language for searching indexed data. When the user performs a search, the request is sent to the indexer, and the relevant events are returned as field-value pairs.


Answer the questions below

**Question**: Which component is used to collect and send data over the Splunk instance?

**Response**: Forwarder


## Task 4: Navigating Splunk
Let's look at each section of the home screen.

### Splunk Bar
The top panel is the Splunk Bar as shown below: 
![Splunk Bar](assets/images/splunk-bar.png)

In the Splunk Bar, we have the following options available:

- **Messages**: View system-level notifications and messages.
- **Settings**: Configure Splunk instance settings.
- **Activity**: Review the progress of search jobs and processes.
- **Help**: View tutorials and documentation.
- **Find**: Search across the App.

### Apps Panel
This panel shows the apps installed for the Splunk instance. The default app for every Splunk installation is Search & Reporting. 

### Explore Splunk
This panel contains quick links to add data to the Splunk instance, add new Splunk apps, and access the Splunk documentation. 
![Explore Splunk](assets/images/explore-splunk.png)

### Splunk Dashboard
The last section is the Home Dashboard. By default, no dashboards are displayed. You can choose from a range of dashboards readily available within your Splunk instance. You can select a dashboard from the drop-down menu or by visiting the dashboards listing page.

Answer the questions below.

**Question**: In the Add Data tab, which option is used to collect data from files and ports?

**Response**: Monitor


## Task 5: Adding Data
For this task I opened an attack box in TryHackMe, opened Firefox browser and use the created link from the virtual machine to access to a Splunk instance. I then clicked on **Add data**, selected **Upload** to upload the file VPNlogs.json in the folder `/root/Rooms/SplunkBasic/`. Next, I selected _json as **source type**, clicked on next, in the options I clicked on **create new index**, created the index VPN_Logs and selected vpn_logs in the index's drop-down.

Answer the questions below.

**Question 1**: Upload the data attached to this task and create an index "VPN_Logs". How many events are present in the log file?
After uploading the log file I clicked on **Start Searching** and i've been redirected to the search page with those default query in the search bar :

```bash
source="VPNlogs.json" host="ip-10-10-40-195" index="vpn_logs" sourcetype="_json"
```

Below the search bar we can see that 2862 events have been returned.
![Question 1 screenshot](assets/images/splunk_lab_question_1.png)

**Response**: `2862`


**Question 2**: How many log events are captured by the user Maleena?
I wrote the following query in the search bar and it returned 60 events:

```bash
UserName="Maleena"
```

![Question 2 screenshot](assets/images/splunk_lab_question_2.png)

**Response**: `60`


**Question 3**: What is the username associated with IP 107.14.182.38?
I wrote the following query in the search bar: 

```bash
Source_ip="107.14.182.38"
```

![Question 3 screenshot](assets/images/splunk_lab_question_3.png)

It returned 26 events, all associated to the username "Smith".

**Response**: `Smith`


**Question 4**: What is the number of events that originated from all countries except France?
I used the following query : 

```bash
Source_Country!="France"
```

![Question 4 screenshot](assets/images/splunk_lab_question_4.png)

It returned 2814 events.

**Response**: `2814`


**Question 5**: How many VPN events were associated with the IP 107.3.206.58?
I used the following query in the search bar:

```bash
Source_ip="107.3.206.58"
```

![Question 5 screenshot](assets/images/splunk_lab_question_5.png)

It returned 14 events.

**Response**: `14`


## Conclusion
I found this room really interesting, and I was grateful for the opportunity to learn and explore some functionalities of Splunk. It helped me understand how it works and helped me to learn foundational knowledge about Splunk. I'm looking forward to work on more advanced projects to improve my familiarity and experience in Splunk.







