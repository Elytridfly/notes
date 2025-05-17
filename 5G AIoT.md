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


#### gNodeB (gNB)
- biggest change in 5G Radio Access Network (RAN), aka Next Generation RAN or NG-RAN, architecture is the distributed concept
- gNodeB (5G base station) is split into gNodeB- Central Unit (CU) and gNodeB-Distributed Unit(DU)
- CU can be placed in cloud infrastructure
- CU and DU control data transmission and radio access
- lower-level RF processing and data plane processing are purview of DU
- higher-level operations and control plane signalling are handled by CU
- they interact with each other allowing for distributed radio access and centralised control
- gNodeB communicate with each other to improve network performance through coordination and optimisation


#### Access and Mobility Management Function (AMF)
- responsible for managing access and mobility aspects of UE 
- terminates control plane interface from gNB 
- manages reachability, registration, and connection signalling
- interacts with UDM to retrieve subscription data and AUSF to validate UE credentials
- AMF communicates with PCF to impose policy decisions and work with SMF to establish and manage sessions


#### User Plane Function (UPF)
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


#### Session Management Function (SMF)
- user session management (establishment, modification, and release of sessions) and IP address allocation (for IP PDU sessions) are centrally orchestrated by SMF of 5G core network
- works in tandem with Access and Mobility Management Function (AMF) to create and preserve user equipment's network connectivity
- SMF collaborates with unified Data Management (UDM) to handle authentication and subscription data
- SMF works with Policy Control Function (PCF) to impose charge controls and policy regulations
- SMF interfaces with UPF to control packet forwarding and routing, ensuring efficient data flow through the network


#### Authentication Server Function (AUSF)
- user security and authentication are handled by Authentication Server Function (AUSF)
- it interfaces with AMF to provide secure communication between the user and network
- it  interfaces with Unified Data Management (UDM) to validate and store user credentials
- primary roles of AUSF are to authenticate user equipment (UE)
- throughout procedure, AMF sends authentication request to AUSF
- AUSF responds by processing info obtained from UDM, including access authorisation and authentication credentials
- user can access it and that their data is safe while they are using the network


#### User Data Management (UDM)
- provide critical information (data for access authorization, user registration, and data network profiles)
- carries out vital tasks such as managing data network profiles, registering users, granting access
- to ensure secure access and authenticate users, UDM communicates with AUSF 
- to support user mobility and session management throughout the network, it communicates with AMF
- Session Management Function (SMF), essential for assigning IP addresses and overseeing user sessions, receives subscriber data from UDM
- operation and delivery of services in 5G network depend on coordinated interaction between UDM, AUSF, AMF, and SMF


#### Policy Control Function (PCF)
- governs network behaviour
- enables smooth mobility management and guarantee effective handover procedures
- communicates with AMF to provide dynamic session management based on real-time policy rules
- PCF and SMF collaborate to establish, maintain, and terminate network sessions
- PCF works with Application Function (AF) to ensure QoS throughout the network to implement policies that correspond with the requirements of various applications
- PCF, AMF, SMF, and AF interact to ensure intelligent and adaptive management of network resources which improves 5G service performance and dependability



#### Application Function (AF)
- AF interfaces with PCF 
- in charge of tasks like contacting PCF for policy control and gaining access to Network Exposure Function for resource retrieval
- serves as effective gateway between application layer and 5G network resources by facilitating routing of application traffic and exposing services to end users
- decisions based on real-time data, usage patterns, policy governing QoS, billing, all depend on interaction of AF and PCF
- this allows the network to dynamically adjust and offer best possible service levels to different application and users



### 5G Spectrum and its Frequency Bands
#### What is 5G New Radio (NR)
![[Pasted image 20250510202346.png]]
- phones use RF waves to facilitate communications
- 5G NR stand for 5th Generation New Radio interface
- uses 2 frequency ranges:
	- FR1 : 6GHz and below
	- FR2 : mmWave - 20 to 60 GHz


### 5G Spectrum and its energy bands
![[Pasted image 20250510202604.png]]
- Singapore use n78 : 3.3 - 3.8 GHz and n257 26.5 - 29.5 GHz


### 5G Radio Access Technology (RAT) and its Evolution
![[Pasted image 20250507124751.png]]
1. **Orthogonal Frequency Division Multiplexing (OFDM)**
	- Encoding more digital data onto multiple carrier frequencies
	- used for wired communication networks, later adapted for LTE and WiMAX networks
	- optimised for 5G for greater bandwidths, larger data speeds, improved spectral efficiency

2. **Multiple Input Multiple Output (MIMO)**
	- Using many antennas to make many signal paths
	- originally for wireless communication with IEEE 802.11n standard 
	- Massive MIMO used by 5G dramatically increases no. antennas at base stations to several dozen or even hundreds
	- leading to better coverage, capacity, spectral efficiency by improving beamforming, spatial multiplexing and interference suppression
	
3. **Beamforming**
	- Concentrate radio waves to make narrow beams 
	- increase signal strength and lower interferences
	- used for radar and satellite communications 
	- phased array antennas used to improve coverage, capacity, User experience
	- beamforming algorithms further optimised to support dynamic beam management, beam tracking and beamforming in both up and downlink
	
4. **Dynamic Spectrum Sharing (DSS)**
	- dynamically split 5G and 4G LTE spectrum based on demand
	- allow for more seamless 5G transition
	- make it possible for 5G NR and 4G LTE to exist at the same time in the same frequency range
	- allow for seamless transition to 5G while optimising network capacity and spectral efficiency
	- allow for flexible spectrum allocation and traffic demand 

5. **Millimeter Wave (mmWave)**
	- high-frequency band above 24GHz utilised in 5G deployments
	- extremely high data rates 
	- limited coverage and prone to attenuation by obstacles
	- large bandwidth and capacity advantages
	- advanced antenna arrays and beamforming used to overcome propagation issues related to mmWave
	- allow for multi-gigabit data rates and supports new application like fast wireless broadband and fixed wireless access


### 5G Core Network and its Services
![[Pasted image 20250507130706.png]]

- brain and heart of 5G mobile network is called 5g Core (5GC)
- handle different critical tasks like policy management, authentication and authorisation, mobility management and connectivity
- 3G and 4G LTE are hardware-based and hard to adjust based on changing traffic patterns, service requirements
- this leads to cloud-native designs or all-cloud architecture
- this change entailed virtualization and deployment of network functions such as software instances on cloud infrastructure
- Benefits of this include:
	- flexibility
	- agility
	- scalability
	- cost-effectiveness
	- support for new services and applications
- to move everything into a all-cloud architecture the following are needed


#### Software-Defined Networking (SDN)
- increases programmability
- automation
- agility in network administration
- by enabling operators to optimise and dynamically allocate resources in response to real-time demand, SDN enhances responsiveness and efficiency


## Fundamentals of AIoT

### basics of AI and ML
- AI gained widespread attention in 1997 when IBM Deep Blue defeated world best chess play Garry Kasparov
- 2011, chatbot tricked people into thinking its real person, and also completed the Turing Test
- Weak AI aka Narrow AI carry out single task for what its created for
- Strong AI can think learn and adapt like people


#### Reactive Machines AI
- earliest kind of AI
- incapable of learning or having grasp of past experiences
- limited to the core activities which it was designed for
- cannot grow

#### Limited Memory AI
- can learn from past data
- brief window of time they can look back on past and draw lessons from it
- large amounts of relevant training data are used to train
- data from memory is utilized to build a reference model that is used to solve issues in the future
- drives contemporary AI applications

#### Theory of Mind AI
- sophisticated system that can comprehend the entities it interacts with more fully
- recognise the entities needs, emotions, beliefs, and thought process
- development is currently ongoing
- able to quickly identify facial and eye movements and adjust actions to suit the situation

#### Self-aware AI
- theoretical system that is the most sophisticated AI 
- when it is self-aware, robots or machines understands their own intrinsic characteristics and are completely aware of who they are
- capable of perceiving human emotions and comprehending a variety of situations and state


### Types of AI and relation between AI, ML, DL

![[Pasted image 20250517010932.png]]

- machines can carry out tasks that require human intelligence such as reasoning, self-correction, and learning
- Machine learning is used by AI to imitate human intelligence
- process for reacting to select few particular actions must be taught to the system
- thus creating a propensity model by combining algorithms with past data

- ML is automated search for significant patterns in data
- AI that enables system to learn from data instead of explicit programming is called ML
- using variety of methods ML improves, describes, and predicts results by iteratively learning from available data
- accurate models based on that particular data can be generated as the algorithms process the training data

- Deep Learning (DL) is a subnet of ML 
- part of ML that concentrates on how "abstractions and concepts" are formed
- Massive amounts of data are usually ingested by DL algorithms which then use supervised or unsupervised learning to generalize the characteristics/ features and categories associated with that data
- neural networks are foundation of deep learning systems

###  Key AI Terms and Definitions

![[Pasted image 20250517104951.png]]

- ML is the class of algorithms that automatically get better with experience and data usage
- DL is a significant subset in ML that use multi-layered neural networks
- Convolutional Neural Networks (CNN) and Deep Neural Networks (DNN) are 2 examples of DL models

- ML has recently evolved into a common tool for nearly any activity involving extraction of data from big data sets
- Search Engines that provide us relevant results, anti-spam software learns to filter our emails, software that detects fraud learns to safeguard credit card transaction, all this are ML based technology
- ML Algorithms are also used by cars to prevent accidents, digital cameras to detect faces, phone personal assistants to recognise voices
- Application of ML are also frequently used in astronomy, medicine and bioinformatics


- using many methods/algorithms, ML improves, describes, and predicts results by iteratively learning from available data
- by feeding them with training data, exact models based on that particular dataset can be generated
- when data is used to train the ML algorithm, the resulting output is actually the ML model
- a predictive algorithm will provide a predictive model
- a prediction based on data will be sent when model receives it
- ML is a combination of the following:

``` Data + Model -> Compute Prediction```

- model comprises of our expectation based on prior info, which can come from transfer learning or can just be out convictions/beliefs
- humans have biases built into our "models"
- the prediction can be a classification, a course of action, or a quality rating

- programs that learn and get better based on experience need ML due to the intricacy/complexity of the given situation and need for adaptation
- tasks that are highly complex like driving, picture recognition, speech recognition are not easy to code and need ML
- manually coded tools will limit its characteristic/features as it will stay the same once deployed and will not change despite the task varying over time
- ML trains programs to change how they behave in response to incoming data, allowing them to adapt 

- Supervised, Unsupervised, Reinforcement 
- 3 most popular techniques in ML
- Supervised uses manually labeled data
- Unsupervised looks for patterns and structures in data automatically
- Reinforcement combines rewards or penalties with trail-and-error method

### Supervised Learning
![[Pasted image 20250517110719.png]]

- A data set with certain observations and labels of them is needed for supervised learning
- they can subsequently be used with observations that were not know previously
- when new unseen data is supplied, the algorithm generates an inference function to make predictions
- by comparing actual output with intended output, the model can further refine, aka "backwards propagation" of errors

- 2 main types of supervised models:
	- Classification : output variable is category
	- Regression : output variable is real continuous value

- examples:
	- Linear regression - mainly for regression problems
	- Random forest - mainly for classification and regression problems
	- Support vector machines - mainly for classification problems


### Unsupervised Learning
![[Pasted image 20250517111841.png]]

- learns patterns from unlabeled data
- finding patterns in data that were previously unknown

- typical application of Unsupervised Learning:
	- Clustering : auto split data set into groups according to similarity
	- Anomaly detection : used to auto discover unusual data points in dataset 
	- Association mining : used to identify sets of items that frequently occur together
	- Latent variable model: used for data pre-processing (reducing no. features in data set - dimensionality reduction)

### Reinforcement Learning
![[Pasted image 20250517114236.png]]

- Reinforcement Learning (RL) 3 common technique
- "Agent" learns to accomplish the objective/goals
- it will be rewarded or penalised for actions that it executes
- objective is to maximize agent's reward

- creation of appropriate simulation environment is 1 of the primary a challenges in RL
- to train autonomous driving algorithms, RL environment ned to accurately mimic scenarios like breaks and crashes
- advantage is that training model in simulated environment is typically less expensive than utilising immature models


### Machine Learning Cycle
![[Pasted image 20250517114545.png]]


### Artificial Neural Networks and Deep Learning
![[Pasted image 20250517114623.png]]

- ANN are specialised field within ML
- loose inspiration for ANN comes from neural networks that make up the brain
- group of interconnected nodes called neurons serves as representation of ANN
- "edges" allude to connections like synapses in the human brain
- each edge can send messages to other neurons
- after processing incoming signals, receiving neuron notifies its associated neurons
- Signals are numbers, and statistical functions are used to compute them

- there is a weighted relationship between neurons and edges that either increase or decrease a signal strength 
- you can change the weights as you continue to learn
- neurons are typically grouped into layers with each layer altering the input in a different way
- these layers allow signals to pass through possibly several times 
- employment of numerous layers in these networks are indicated by adjective "deep" in the context of deep learning

![[Pasted image 20250517121249.png]]

- CNN are popular way that ANN are implemented
pg 19