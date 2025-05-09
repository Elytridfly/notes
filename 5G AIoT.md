## Intro to 5G AIoT
### Roadmap to 5G
![[Pasted image 20250430093609.png]]
- 1G: Analog Voice
- 2G: Digital Voice, SMS
- 3G: SMS, MMS, www
- 4G: Mobile Broadband, LTE(faster data transmission)
- 5G: Allow for faster technology (self-driving car, AI IoT)

### 5G Global trends
- 5G introduces improved mobile broadband
- users' devices can establish 5G network connection
- applications like AI, AR/VR, IoT will be easily available

### 5G key areas
- Fifth Generation of mobile networking determined by part of $3^{rd}$ Generation Partnership Project (3GPP) 
- meet requirements of International Mobile Telecommunication-2020 (IMT-2020) under International Union Radio communication Sector (ITU-R)
- Addresses 3 key areas and put 4 different use scenarios:
  ![[Pasted image 20250430094446.png]]

- eMBB - Enhanced Mobile Broadband- high data rate and high capacity (mobile connectivity)
- mMTC - Massive Machine Type Communication- high volumes of data (many sensors, smart city)
- URLLC - Ultra Reliable and Low Latency Communication - low latency and high reliability (self driving cars, speed)


### Use scenarios of IMT-2020 and beyond
![[Pasted image 20250430094916.png]]


### 5G Technology Summary
- 5th generation of cellular network technology
- Bands:
	- Lower bands -<2.6GHz (LTE) : wider coverage
	- Mid bands - 3.5GHz : balance of coverage and capacity
	- Higher bands - 26/28GHz : provides ultra-high bandwidth
- Higher Speed
- Lower Latency
- Higher capacity and increased in data bandwidth
- Multi-access edge computing
	- bring high computational services from centralized cloud closer to end users
- easing need of having high performance device at end user for computational intensive use cases such as AR/VR
- Network Slicing enables various differentiated services across different industries with assured Quality of Service


### benefit of 5G
- speed
	- 100 times faster than standard 4G
	- 30 times faster than advanced 4G like LTE-A

|Network Type|Max download speeds| Time to download a full movie|
|---|---|---|
|3G|384 Kbps|Over a day|
|4G|100 Mbps|Over 7 mins|
|4G+|300 Mbps|2.5 mins|
|5G|1-10 Gbps (theoretical)|4-40 sec|

- low latency
- 50 times faster than standard 4G and 5 times faster than 4G standards like LTE-Adv, LTE-Adv-Pro

### Edge Computing
- "Edge" refers to the  part of infrastructure that is near to the sources of data
- edge computing means performing actions on data such as data analysis, decision making at the edge
- Advantages
	- reduce communication bandwidth between sensors and servers
	- faster access of data since data is stored "near" the source
	- fast data analysis, computing, and actions
- Disadvantages
	- creates duplicate system functionality
	- replicates fragments of info across distributed networks => increase redundancy


### Network Slicing
![[Pasted image 20250430102339.png]]

- 5G network slicing is the use of network virtualisation to divide single network connections into multiple distinct virtual connections that provide different amounts of resources to different types of traffic
- Providers have to move into a system that's more flexible and adaptable -- make the network more software centric
- to create a single highly flexible, virtualized, software-defined network instead of building multi purpose-built networks

### Limitations of 4G
- Limited Capacity
	- congested when many users try to connect at once
	- slower data rates experiences when many users present
- Limited Connection density
	- total number of devices fulfilling specific quantity of service per unit area is limited
	- connection to a network can be lost or verry slow in crowded areas
- Latency
	- not reliable when rapid responses are needed

### Difference in capabilities between 5G and 4G
![[Pasted image 20250430120733.png]]


### Features of 5G
Users:
- low battery consumption and better battery life for devices
- around 1 Gbps data rate easily possible
- very low network latency

System:
- more than 100 times more device handling capacity
- better coverage area and high data rate at edge of cell
- availability of multiple high data transfer rates
- 100 times higher data speed over the air
- multiple services can run in parallel
- custom made network slices
- better energy efficiency and spectral efficiency
- massive MIMO -- 10x more antennas than 4G
  
  
  
### What is IoT
- network of physical devices, vehicles, buildings and other items - embedded with electronics, software, sensors, actuators, and network connectivity that allow these objects to collect and exchange data

6C's
- Collect - collection of data through sensors
- Communicate - wired or wireless communication technologies 
- Connect - network connection
- Cloud - computing resources
- Comprehend - data analytics to make sense of the data
- Create - value creation through mobile apps

### Enabling Massive IoT
- cellular standards like 5G provide a network backbone for IoT services, supporting both high data rates and long-range communications
- ![[Pasted image 20250430121308.png]]

- Evolving IoT networks are being designed to accommodate devices through several new technologies such as:
	- Bluetooth and BLE
	- Cellular 3G, 4G, and 5G
	- LPWANs
	- Mesh protocol
	- WiFi/ WiFi HaLow
	- RFID

### What are AI and Machine Learning
- AI
	- science and engineering of making intelligent machines, especially intelligent computer programs
- Machine Learning
	- application of AI that provides systems the ability to automatically learn and improve from experience without being explicitly programmed
- ![[Pasted image 20250430121613.png]]

### What is AIoT
- AI evolved from algorithm approach into self-learning and big data management, processing, connectivity, sensing and actuating along with security are the key enablers of AI
- IoT is a popular technology trend, which in recent years has been joined with AI to form AIoT
- AIoT is IoT with embedded AI. without AI, the data pool created by IoT devices would fail to reach its full potential and without IoT, AI wont have the required data sets
- IoT benefits from AI's advanced data analytics capabilities, while AI applications receive real time info from extensive networks
- by merging both, it brings the best of both helping turn IoT connected devices from passive sensors into data learning machines
- eg, self driving cars and AI will help to augment our transportation
- 

## Fundamentals of 5G

### 5G Network Architecture and its components
![[Pasted image 20250430122629.png]]


![[Pasted image 20250430122643.png]]

#### gNodeB
- biggest change in 5G Radio Access Network (RAN), aka Next Generation RAN or NG-RAN, architecture is the distributed concept
- gNodeB (5G base station) is split into gNodeB- Central Unit (CU) and gNodeB-Distributed Unit(DU)
- CU can be placed in cloud infrastructure
- CU and DU control data transmission and radio access
- lower-level RF processing and data plane processing are purview of DU
- higher-level operations and control plane signalling are handled by CU
- they interact with each other allowing for distributed radio access and centralised control
- gNodeB communicate with each other to improve network performance through coordination and optimisation

#### UPF
- User Plane Function supports features and capabilities to facilitate user plane operations
- examples:
	- packet forwarding and routing
	- interconnection to the Data network(DN)
	- policy enforcement
	- data buffering
- all makes it possible for user equipment and external networks to transfer data efficiently
- for the purpose of managing user data flows, Next-Generation Node B (gNB) and the UPF collaborate closely to ensure optimised routing and QoS enforcement
- it works in tandem with Session Management Function (SMF) to create and oversee data sessions, constantly adjusting to evolving service needs and network conditions.
- UPF communicates with the Packet Data Network Gateway (PDN GW) to allow access to a variety of services and seamless data interchange by enabling connectivity to external networks
- UPF is a cornerstone of 5G architecture, guaranteeing improved connectivity and service delivery while permitting reliable and effective data transmission

#### SMF
- user session management (establishment, modification, and release of sessions) and IP address allocation (for IP PDU sessions) are centrally orchestrated by SMF of 5G core network
- works in tandem with Access and Mobility Management Function (AMF) to create and preserve user equipment's network connectivity
- SMF collaborates with unified Data Management (UDM) to handle authentication and subscription data
- SMF works with Policy Control Function (PCF) to impose charge controls and policy regulations
- SMF interfaces with UPF to control packet forwarding and routing, ensuring efficient data flow through the network

#### AUSF
- user security and authentication are handled by Authentication Server Function (AUSF)
- it interfaces with AMF to provide secure communication between the user and network
- it  interfaces with Unified Data Management (UDM) to validate and store user credentials
- primary roles of AUSF are to authenticate user equipment (UE)
- throughout procedure, AMF sends authentication request to AUSF
- AUSF responds by processing info obtained from UDM, including access authorisation and authentication credentials
- user can access it and that their data is safe while they are using the network

#### UDM
- User Data Management
- provide critical information (data for access authorization, user registration, and data network profiles)
- 
- 


### 5G Spectrum and its energy bands
- Singapore use n78 : 3.3 - 3.8 GHz and n257 26.5 - 29.5 GHz


### 5G Radio Access Technology (RAT) and its Evolution
![[Pasted image 20250507124751.png]]
1. Orthogonal Frequency Division Multiplexing (OFDM)
	- Encoding more digital data onto multiple carrier frequencies
2. Multiple Input Multiple Output (MIMO)
	- Using many antennas to make many signal paths 
3. Beamforming
	- Concentrate radio waves to make narrow beams 
	- increase signal strength and lower interferences
4. Dynamic Spectrum Sharing (DSS)
	- dynamically split 5G and 4G LTE spectrum based on demand
	- allow for more seamless 5G transition
5. Millimeter Wave (mmWave)
	- high-frequency band above 24GHz utilised in 5G deployments
	- extremely high data rates 
	- limited coverage and prone to attenuation by obstacles
	- large bandwidth and capacity advantages


### 5G Core Network and its Services
![[Pasted image 20250507130706.png]]

- 