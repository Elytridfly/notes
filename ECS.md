# Intro to Embedded Systems
- Embedded computer systems are special versions of computers we use daily
- ranging to remote controls to washing machines

## Typical Microcomputer organisation
- basics consists of CPU, memory, IO, buses

### Central Processing Unit (CPU)
- consist of 3 parts:
	- Arithmetic/Logic Unit (ALU)
		- ALU performs arithmetic and logical operations on binary data
	- registers
		- storing data, addresses, instructions
		- main register is called accumulator

![[Pasted image 20250519234020.png]]
 
- control units
	- control unit directs the operation of all other unit by providing timing and control signals
	- contains logic and timing circuits that generate proper signals necessary to execute each instruction in a program
	- capable of responding to external signals such as interrupts
	- interrupt request will cause control circuit to temporarily interrupt main program execution, jump to a special routine to service the device then back to the main program

#### Memory Unit
- contains large number of memory cells, usually RAM or ROM
- used to store instruction sequences or programs which the computer will execute, data that is to be processed by program, data resulting from program
- Operation of memory is controlled by control unit which signals for either READ or WRITE operation

#### Input/ Output Units
- Input devices are used to supply data needed for processing
- Output devices allow results of computer operations to be supplied to the user
- IO devices are known as peripherals
- common input are keyboard and mouse
- common output screens

- IO ports are simply interface circuits that provide appropriate electrical connections between IO devices and rest of computer system
- physically IO port is just a parallel set of buffers or D flip-flops which latch data when strobed by the CPU

### Bus Structure
- CPU is linked to other parts by buses
- a bus is a group of conductors that has connections to all system's main blocks
- 3 major busses : address bus, data bus, control bus

#### Address Bus
- used by CPU to send out address of memory location that is to be read from or written to
- address bus is unidirectional
- information moves in 1 direction only from CPU

#### Data Bus
- bidirectional as data can flow to and from CPU, memory, IO ports
- any device outputs connected onto data bus must have tri-state buffers so that they can be floated except when the device is being selected
- number of conductors in data bus is determined by no. binary digits CPU can handle
- quantity of data stored at each location depends on particular memory device, may be single bit, 4, 8, 16 bits per location

#### Control Bus
- used to carry signals which synchronise activities of separate blocks of the computer system
- tells memory and IO ports whether CPU is reading or writing data
- 2 conductors found in the control bus are the READ and WRITE lines
- READ line activated by CPU when CPU wants to retrieve data from memory or input device
- Eg, CPU wants to tread from memory locations, CPU place address on address bus and READ signal on control bus. memory then outputs the data from addressed location to data bus which is transferred to CPU data register
- when CPU wants to store data, it places data on data bus, then address, then activate write line

## History of microprocessors
- Electronic computers were developed in 1960's 
![[Pasted image 20250520000521.png]]

### need for more computing power
- Image, video/audio processing
- floating point data
- sophisticated control algorithms: fuzzy logic, neural network
- Real-time processing: need faster speed

### Increases in performance
#### processing speed
- older programs can be used due to faster speed
- not enough to deal with more complex data alone

#### Address
- manipulating data like sound, image, video need large storage and high speed
- they need to be placed in memory for efficient processing
- 16-bit address only have 2616 or 65536 bytes that can be accessed
- now we just 32 and 64 bit addresses

#### Data
- most of the times, unit of data is 8 bits / 1 byte
- more sophisticated math manipulations need many more bits to prevent loss of precision
- depending on whether fixed or floating point is used. 80 bits for math data is common
- instead of fetching 8 bits at once, its more efficient to fetch and manipulate them in 32 bits units, hence reference to 32 bit data

#### Architecture
- refers to how data flows within the processor, making it more efficient
- eg, having 2 or more processing units allow simultaneous fetching of data and actual processing of data
- may even pre-fetch data or code that is not required yet anticipating when it is used and place it in memory faster so it executes faster
- hardware also can be optimized so that certain common instructions can be executed much faster than others
- architectural changes may introduce subtle errors in the program if they are time dependent
- otherwise it should not change the running of program significantly

### Progression of Intel Microprocessors
- popular because of IBM PC released in 1982
- programs used back then can still run on today's desktop systems
- not true for 8080 or 8085 which are compatible with each other being 8/16 data/address bit processors
- 8088 was designed to help software developers bring their programs over to 8085
- done using segmented address scheme
- allowing 16 bit "logical" address within a 20 bit address space
- the 20 bit address quickly became inadequate leading to 24 and 32 bits


### Advantages of Intel PC architecture
- ARM  (Advanced RISC Machine) processor was introduced in 1983
- RISC was a design philosophy that emphasized simple machine instructions, large number of on-chip registers and the us of only load and store instructions to interact with memory, allowing for low power consumption
- ARM processors are designed by their parent company who license the design to other companies who customize the design by adding other hardware and peripherals
- unlike Intel who do all their manufacturing in-house, examples: Qualcomm (Snapdragon), Mediatek, Samsung (Exynos), Apple (M1)
- due to high level of integration and complexity, they are often referred to as SoC (Systems on a chip)
![[Pasted image 20250529171730.png]]

## Embedded Systems Characteristics
![[Pasted image 20250529171754.png]]
- inputs to a desktop system differ from those of an embedded system

#### Fixed use
- The systems are used for fixed purpose
- normally to control another device or process
- Desktop computers can be used for variety of purposes

#### Small size
- system must be relatively smaller than the system it is part of
- places constraints on the physical size of the embedded system

#### Limited resources
- related to small size
- amount of memory is limited and most of the time is in terms of RAM
- embedded systems mostly never use hard disks and programs are stored in ROM

#### Fault tolerance
- system should be capable of "failing gracefully" if it meets unpredictable circumstances
- preferable to the system "hanging"

#### Real time control
- speed is fast enough to affect the operation of the environment
- remote control device operates in terms of seconds
- but aircraft control system works in terms of thousandths of a second
- complexity of calculations required for such a system plays a major part in determining what kind of system to use
- many cases, especially involving human interactions,it does not make sense for computers to work in millionths of a second if humans only respond in thousandths of a second

#### Guaranteed response time
- Closely related to real time control 
- need for embedded system to respond to a device or user request in minimum time
- especially true when systems are running several tasks at the same time
- important processes have stringent conditions on this

#### reliability
- especially when human lives are involved
- embedded systems often work in environmentally hostile environments
- aircrafts are subject to extreme head and cold and mechanical vibrations and shock
- other factors may be electromagnetic interference, radiation and chemical pollutants
- being part of a larger system, they may be installed in physically inaccessible places
- and may be difficult to perform software updates and have to run continuosly for years

#### Simple input and output
- does not need elaborate input devices like keyboard or mouse or display or sound system
- most it will read from switches, sensors, or small size keypads
- may output to motors, relays, buzzers, LEDs, LCDs
- sometimes a touch sensitive screen is used for IO

#### Power
- shld not consume too much power relative to host systems

#### Low cost
- so it does not add appreciably the total cost of the host system

## Hardware features of embedded systems
- frequently have to work with devices external to itself
- eg, it receive an input from keyboard, move an object and display the results of its processing to a LED display
- Mechanical control has to be in a precise manner
- system oftenhas to service several devices at the same time
- some devices have large amounts of data to be transffered in short time
- various hardware techniques have been built into the  processor to help perform these tasks
- such as :
	- Interrupts
	- hardware timers
	- direct memory access
- emerging trend is to increasingly incorporate embedded systems into everyday life
- such as smartphones, fitness tracers and so on

### Interrupts
- embedded systems work at high speeds, but often it interfaces to devices which operate slower than it
- data input from humans occur at millisecond rates
- for processor to wait for IO is time consuming and inefficient
- one way to improve is to use interrupts

### Timers
- to control external devices in precise manners, its important to have source of precise time events
- while software delay loops may work and are simple but there are problems:
	- normally involve loops with a high count and does not allow processor to perform any other tasks
	- execution time of an instruction can vary depending on various instruction pre-fetch schemes like caching
	- proper multitasking operating system cannot work on software loops as this makes task management very difficult
- Thus timers, external to CPU but which may be on or off-chip are essential
- timers may be used in many ways:
	- set a value to the timer
	- allow it to count down then cause an interrupt
	- frequency of interrupts can be set so that a user can call up a delay using convienient units like milliseconds
- its possible to directly read the values of the timer register for short duration events

### Direct memory access
- Direct Memory Access (DMA) is a method where peripheral device transfer data to and from memory without data going through the processor
- faster than using software

![[Pasted image 20250529180805.png]]

### Power Management
- availability of  low cost and low powered embedded processors led to the widespread use of the smartphone
- now data is transferred over today's mobile phones are heavily compressed digital data not analog signals
- networks that enable the widespread use of such phones are well equipped for handling data
- cellular networks that use large numbers of base stations which transfer data between them have large numbers of wireless end points which allow devices with low transmission power to communicate with the base stations
- concurrently, the use of Internet has expanded from proprietary, scientific and military data sharing networks to encompass a very wide range of applications such as business , commerce and personal mail
- in 1990's there were effort to equip consumer devices with the ability to be controlled remotely and also to report their status over the internet
- these 2 factors joined together to give us the current state of connectivity the IoT
- today, data is being "mined" to obtain info about trends, anomalies to better predict and thus plan for the future
- a device with IoT technology can collect how much personal info simply from the user's interactions with it
- thermostat can know ur sleep/wake cycle and when ur home is empty
- by correlating multiple info sources, it is possible to infer a great deal abt ur habits, preferences and activities
- However a large propotion of embedded devices run on their own power and this there is a great need to conserve this resource
- this is emphasized with the world wide realisation of the earth's dwindling enegery reouseces and of global warming due to energy production 


#### Program Design
- since energy used by system is proportional to number of instructions executed, it makes sense to use least possible number of instructions to accomplish a task
- however it should be noted that high level languages like C generate several lines of assemblt code and thus a good knowledge of the processor architecture is needed
- 2 low power modes are possible. CPU is turned off but contents of the working memory are preserved according to the mode:
	- Standby - contents of memory are still present using battery power
	- Hibernate - contents of memory are saved to non-volatile memory
- In context of interrupts, the main task consists of a "Standby" command and a timer or peripheral interrupt will wake up the processor for processing data which can be done at high speed
- The speed at which the processor can restore it's working state is important  and will decide the low power mode to use
- ![[Pasted image 20250529175101.png]]
- as shown above, greater power saving can result if an algorithm can be implemented without using a processor and RAM which takes up the most power
- Field programmable gate array (FPGA) or ROM based code in a separate piece of hardware would use very little power

#### Power Supply
- Current electronic devices need a stable voltage to operate
- standard 7805 voltage regulator IC has been used for decades to supply a stable 5V power supply to logic circuits that operate TTL logic levels
- ![[Pasted image 20250529175710.png]] 
- dropout or forward voltage of a device is often ignored waste of power
- eg, a normal diode is around 0.6V and larger than 0.2 V for a transistor
- in design of 7805 dropout voltage of 2.5V is needed to keep it operational
- if current of 1 A  is passed thru, 2.5 W is needed which will need a heat sink attached to the device

- clearly a waste of power and now low drop out (LDO) voltage regulators are used. they only need 0.6V to operate properly
- however, input voltage to LDO must be supplied
- difficult to always find a transformer with the needed voltage and voltage may vary with load
- another way is to use switching regulator
- incoming DC Voltage is converted into pulse wave using oscillator and inductor is used to step voltage up (boost) or down (buck)
- the device measures the difference between Vref and Vout and changes duty cycle to maintain the output voltage
- up to 90% efficiency can be achieved, but it adds cost and complexity and high noise level and poorer regulation
 ![[Pasted image 20250529180249.png]]
 - wide variety of batteries available and technology is changing
 - there are also primary (non-chargeable) and secondary (chargeable) technologies and various charging techniques
 - however it is also possible to replace batteries with energy harvesting like solar, wind, water

#### Processor hardware
- standard 5V used to power IC and embedded  systems in the past
- now 3.3V is common and some even 1.8V
-rate which a software executes is a factor
- lower frequency, lower power consumption
- eg, CPU that executes 100000 instructions get a job done but needs to be performed every second
- if CPU were running at a clock frequency that allow it to execute a million per second, it will be capable of doing 10X the amount of work required
- so lowering the frequency to the needed performance will optimize power consumption
