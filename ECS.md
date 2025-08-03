# Intro to Embedded Systems
---
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


# Bus Systems and Devices
---

## Intro
 - embedded processors have hundreds of kB size on-chip memory
 - run at GHz speeds and high level of integration with other functional blocks with other chips aka SoC
 - memories used for programs and data executing within the processor and are optimized for speed so that busses in the processor are not easily accessed
 - the processors need to interface external devices which have grown in complexity
 - common situation is to aquire and store data or interface with large displays
 - external bus interface is needed for such situations 
 - the external bus interface is used for :
	 - specialized memory needs, static RAM, NAND, and NOR type flash memory
	 - controlling large graphic LCDs
	- many vendors provide external bus interface and most of the time a high speed bus is not needed
	- using a few low cost TTL chips are enough for interfacing
	- protcols used in simple bus interfaces still lives on in modern systems, which build upon the protocols with advanced techniques in Comp Arch

## ARM based Hardware Architecture
- ARM have versions that have a more open interface
- such as RPi which is widely used in set top boxes in TVs
- RPi is the size of a credit card and can run linux OS
- hardware can interface with low-levell electronics so that high-level linux software can analyse and control external devices
- thus it has been successfully used in IoT applications as well as robotics, cyber-physical systems, 3D printing
- designers came up with Compute Module 3 (CM3) for industrial uses
- which has less built in peripherals than the RPi but more processor pins available making it cheaper and more flexible for custom designs

## Hardware of the SoC
- Broadcom SoC used in CM3 has a CPU which uses an ARM Cortex A core following ARMv8-A architecture
- hardware blocks that make up a typical SoC
	- GPU
	- Memory
	- Timers
	- DMA
	- Interrupt Controller
	- GPIO
	- USB
	- PCM (Pulse Code Modulation)
	- I2S (Inter-IC Sound)
	- PWM
	- Serial Communication
		- I2C (Inter-Inter Circuit)
		- SPI (Serial Peripheral Interface)
		- UART (Universal Asynchronous Receiver/Transmitter)


- on broadcome SoC on-chip bus transfers data between various blocks using hardware based on bus architecture design by ARM called AMBA (Advanced Microcontroller Bus Architecture)
- this in turn specifies other interfaces to external devices such as Advanced eXtensible interface (AXI) which allows interfacing to external memory devices 

![[Pasted image 20250529201356.png]]

- AXI specification allows connections to external memory using external bus interface 
- for broadcom devices, this is known as Secondary Memory Interface (SMI)
- NAND flash memory interface requires smaller number of address pins and six are specified in the SMI with the requisite control pints
- 8080 or 6800 bus interface is used cos of their simplicity and modest hardware requirements
- 8080 from intel and 6800 from Motorola are the first microprocessors on the market in 1970s
- their interfacing protocol is still very much in use today
- 8080 was electrically cumbersome due to its multiple voltage and support chips and an improved version 8085 was introduced
- the bus timing signals of the 8085 is common refferred to as the "8080 bus" in current sure
- currently, there are several variations on the specifications

## 8080 mode bus
- earliest microcomputer systems, vendors have always provided an interface bus
- 8080 interface specifies a 16 bit address bus, an 8 bit data bus and use of separate read and write signals for control
- current devices that interface using 8080 mode are LCDs and various types of flash memories 
- in these devices, the address and data bus sizes can vary but the timing of control signals have a common sequence

### Description of bus
- 8080 and 8085 originally specified the following bus widths and control signals

![[Pasted image 20250529202826.png]]
![[Pasted image 20250529202834.png]]

- for devices in current use, full widths of address and data busses may vary. eg, data bus may be 8,9,16 or 18 bits
- timing of a typical instruction of the 8080 and 8085 is that it executes over 3 clock cycles 
- the data bus is multiplexed allowing more pins to be available for control purposes thus full width of address bus only appears at cycle T2

![[Pasted image 20250529202847.png]]

### Memory and I/O mapped addressing
- 8080 bus makes a distinction between addressing memory and I/O devices by having an IO/M signal 
- as 8080 and 8085 have different instructions, this allows greater flexibility in accessing IO
- firstly memory mapped IO allows the use of interfacing devices as if it were a memory device sing standard load/store/move instructions in the assembler or high level language assignment statements
- displays are a typical example of this sort of device
- second IO mapped instructions take the form of "input" or "output" instructions
![[Pasted image 20250529203253.png]]


## Memory devices on 8080 mode bus

### intro to types of memory devices
- there are many different types of semiconductor memories
- we focus on RAM and ROM

#### RAM 
- memory device where data can be stored as well as retrieved
- process of storing data at a particular location takes the same time as process of retrieving from that location
- most RAMs are volatile however, there are non-volatile RAMs 

####  ROM
- logic function is stored in circuit permanently without need of electrical power to sustain the memory
- input combination has no effect on how long it takes to read the output combination
- ROM can be defined as fixed memory whose contents cannot be altered during normal operation
- number of types of ROM, based on methods of storing data in the ROM and whether it can be erased
- in ROM, the data stored as part of manufacturing process can never be changed after that
- thus it requires costly manufacturing process and is not economical unless high demand

#### RAM vs ROM
![[Pasted image 20250529203621.png]]


##### Applications for ROM
- ROMs used to store unchanging data like user prompts, error messages, character generators for video displays or bootup program for computers
- but widely used for simpler forms such as 4 line to 16 line decoder or BCD 7 segment decoder

#### EPROM - Erasable PROM/ One Time Programmable ROMS
- EPROM or Erasable PROM is a device in which data can be erased after it has been stored so it can be reused many times
- erasing is done by shining UV light on the chip through a quartz window for 20 to 30 mins
- the chip has to be made of ceramic due to the quartz window
- in order to make use of existing processes and lowering cost of the package, manufacturers offer EPROMs in plastic packaging that cannot be erased aka One Time Programmable ROMs (OTPROM)

##### Applications for EPROM/OTPROM
- for design testing and development
- necessary to revise and test program many times before its error free
- as PROM can only be programmed once, its too expensive for development
- thus EPROM can be used despite higher initial cost of the IC package
- and since they are now relatively cheaper, EPROMs are replacing PROMs in many applications

#### PROM - Programmable ROM
- overcome expense when only small quantities are needed, PROMs are produced
- the data is not stored during manufacturing but instead by the ser with necessary programming equipment
- once stored the data cannot be changed
- process involves "blowing" of small nichrome fuses or links in the device
- often also called fusible link PROMs
- normally bipolar devices

##### Application of PROMs
- main use is for small-scale production where economies of scale are not available
- as chip manufacturer can produce basic (unprogrammed) devices in large quantities, they are comparatively inexpensive
- but the user of the PROM must then pay the additional costs of programming the device
- a custom-made address decoder is a very useful application of a small Field-programmable ROM


#### EEPROM - Electrically Erasable PROM
- EEPROMM or E^2ROM is special type of erasable semiconductor memory where data can be erased and re-written electrically in a circuit
- recently became very important as storage devices
- unlike RAM, process of storing data take much longer than reading it
- usually 30 ms writing time
- a later type is FLASH memory
- main difference is FLASH updates contents in terms of groups of bytes or sectors 
- EEPROM does so byte at a time
- FLASH can store large amounts of data relatively quickly
- EEPROM is available with a serial interface, making it smaller both physically and storage capacity
- Parallel devices are larger on both areas this addressing different applications
- FLASH memory can be purchased as bare memory chips which generally use NOR gate technology used to store programs as memory can be access randomly
- Interfacing to the chip involves hardware design and it may not be possible to remove the bare chip but it can take very little space
- in terms of software, little effort is needed 
- NAND gate technology, flash memory is commonly available as "memory cards" 
- eg, Compact Flash (CF), Secure Digital (SD), MultiMedia Card (MMC) formats and others
- this is because NAND flash memory favor sequential access of data within blocks of memory such as in these devices
- hardware on the cards make interfacing easier
- eg, CF cards appears like hard disks while SD/MMC cards use SPI, a commonly used protocol to interface it. this makes transfer of data easier as card readers are common, but interfacing is more complicated
- Flash memory also appears in standalone portable storage devices
- eg, portable music platers can appear as a hard disk when attached through USB interface

##### Applications of EEPROM
- FLASH memory kind is dependent on application
- as part of a system, its natural to use flash memory for updates to programs as data stored within can be done easily and automatically
- eg, the ability of modern equipment to update their firmware by "flashing" an update from the manufacturer
- however, if we use flash memory for storing large amounts of data, it mores more sense to use a CF card and access it like a hard disk
- Serial EEPROM is mainly used to store settings and config info
- where its low cost, low power consumption and small size are advantages
- RAM the process of storing and retrieving takes around the same time while EEPROMG can rad from in the same time as RAM, it takes way longer to store

![[Pasted image 20250529215545.png]]

#### RAM devices
- RAM devices can be classified as Static and Dynamic RAM
- RAMs are manufactured using both MOS and bipolar technologies
- MOS uses NMOS and CMOS
	- usually simpler devices and yield higher densities than bipolar process
- Bipolar devices include Schottky TTL, ECL, and IIL types 
	- usually faster than MOS and accordingly have higher power dissipation

##### SRAMs - Static RAM
- SRAM use flip-flops as the storage elements
- one F/F per bit of data storage
- 8K Ram has 8192 F/F plus necessary decoding and IO buffering circuits
- Info is retained in the FF as long as power is applied


##### DRAMs - Dynamic RAM
- DRAM uses MOS capacitors to store charge as storage element
- 1's and 0's are indicated by presence o absence of charge on the capacitor
- if capacitor is charged above certain level, it represents 1, otherwise its 0
- ideal capacitor once charged maintains constant voltage but practically, charge will leak away
- - capacitor voltage (data) must be read regularly 
- if logic is 1, it must be refreshed to full voltage before too much charge leaks (refreshing)
- if DRAM is not refreshed often enough, voltage will fall below threshold and revert data to 0
- eg, 8K DRAM contains 8192 MOS capacitors, plus associated decoders, buffers
- all capacitors must be refreshed regularly, typically every 2 ms


## IO Devices on ISA bus
- more common use of plug-in cards is to provide many more ports to be used for interfacing with external devices
- ports normally interface with devices that are much slower than the main processor so that the relatively slower data transfer speed is not an issue
- intel architecture uses 16 bit addressing for IO
- on PC only 10 address pins are actually used, to reduce hardware decoding requirements

### Basic Input/Output Hardware
- vairous hardware elements can perform some functions of the IO section
- Flip flops (latches) and buffers  

#### Buffers
- most microprocessors are MOS products
- capabilities are restricted to at most 1 TTL load or 5 MOS loads
- this severely restricts operation of microprocessor in driving other devices like RAMs, ROMs and other support devices
- in order to increase driving power, or driving current, buffers are used

- buffers are TTL ICs which allow signal to pass through without altering the logic value of the signal
- buffer increase the DC drive characteristics of the signal
- microprocessors with the aid of a buffer is capable of driving many more circuits

- another advantage of using buffers is that microprocessor is isolated from any outside signals
- if theres change in voltage, the buffers are first affected,, thus preventing damage to the microprocessor
- being mainly TTL ICS, they introduce a small delay in the transmission of  data

- 2 variations of the buffer
	- 1 in 1 out buffer which take input and increases the driving current of signal at output for all logic level
	- Tri-state buffer with a additional control signal. when control is active, device performs exactly as a buffer. when deactivated, it prevents any output. the output turns into high-impedance state giving neither 1 or 0
		![[Pasted image 20250529221228.png]]


#### Latches
- mainly made of D Flip flops
- takes a signal via strobe (clock pulse)
- holds signal until another pulse is applied or until power is removed
- advantage over buffer in sense that signal held at particular logic until change is required
- buffer only holds logic level as long as signal is also at that level
- thus latches used in preference to buffers in situations where receiving end requires a little more time to process the signal
 ![[Pasted image 20250529221429.png]]
 - Latches can be level-triggered (change output as long as strobe is active) or edge-triggered (changes output only on rising or falling edge of strobe signal)
 - in cases where ambiguity is avoided, edge-triggered latches are used

#### Input/Output Ports

##### Basic Input Ports
- tri-state buffer connected to data bus line
- control signal of buffer is usually combination of IORD and selected port address which is obtained using address decoding
![[Pasted image 20250529221734.png]]


##### Basic Output Ports
- latch 
- CPU places the necessary data to be output on data bus lines and then clocks the data into the latch with the control signal which is usually combination of IOW and selected port address obtained using decoding
 ![[Pasted image 20250529221857.png]]


## BIOS and boot up process
- 8080 following given sequence when it is RESET
- as ROM is non-volatile, the processor is guaranteed to have valid code when it starts and jump to the location
- most other microprocessors, after start is dependent on what the programmer puts into the ROM code
- early systems, vendors would put basic routines in a so called "Monitor Program" and include it in the ROM
- These allowed users to do fundamental tasks like simple output to the screen, keyboard handling, output to printer, serial communications and so on
- this allowed users to quickly bring up their systems to productive use and allowed a measure of standardization to programs as they use common routines to do IO
- typical PCs, monitor program is known as basic Input Output System or BIOS'more routines can be added for secondary storage devices like hard dishs
- BIOS may occupy as much as 64K or ROM which is not practical for small processors but monitor programs can be as small as 2K
- if system is simple enough, programmer can make do without any built in monitor program

#### boot up for 8080
Consider the boot up process for the 8080 processor: 
Microprocessor function 
i) Performs a jump to location 0H. 
ii) Executes the code found there, which is normally contained in ROM. 

Monitor program (BIOS) function:
i) It searches for a secondary storage device like a floppy or hard disk. 
ii) It reads in the boot sector (normally 512 bytes in length) for the device. 
iii) Puts the contents into RAM. 
iv) Jumps to that code and executes it. 
v) This code will have instructions to load other larger files which will continue to initialise the system. 

This process is called “bootstrapping”. Other processors will jump to other locations upon start up but the startup process follows the same sequence.


# Decoding on bus system
---
- although 8080 has 16 bits for addressing
- we consider these 16 bits for memory chips
- then first 6 bits for IO devices

## Accessing memory device
### Memory address, data , control bus
- memory address bus will tell a memory which particular location is being accessed
- no. memory address lines required depends on size of memory device (eg device with 2048 locations required 11 address lines)

- quantity of data stored at each memory location depends on particular memory device
- it may be 1 bit, 4 , 8 or 16 bits per location
- units of memory may be connected in parallel to meet processor data width
- eg, 4 8 bit memory devices may be connected in parallel to a 32 bit processor

### steps to access memory
![[Pasted image 20250529225200.png]]
1. address is placed on address bus, lower bits used by memory device for internal decoding higher bits go to decoder chip which will generate a chip select (CS) signal which will then select one of the several memory devices
2. READ. if doing a read operation, processor will generate read  signal (RD) which is connected to output enable (OE) of memory chip. memory device will place data from memory location after a short delay. the processor then reads in the data
3. WRITE . if doing a write operation, the processor will place data to be written on data bus then generate a write signal (WR) which is connected to write enable (WE) of memory chip. the memory device will then latch the data in

### Partial and Full Address Decoding
- in most practical situation, devices connected to processor address bus require fewer address bits than there are bits provided on address bus
- 8080 has 16 pin while 6116 RAM has only 11 pins for addressing
- Since 5 pins are unused by RAM chip, this is a case of partial address decoding
- if we have a memory system where all address pins are used in memory access, then it is full address decoding
![[Pasted image 20250529225658.png]]
- pins A0 to A10 are the 11-bit address into to 2048 locations in RAM
-  D0 to D8 are 8 data bits in each location
- CS1 is chip select input that enable the chip
![[Pasted image 20250529225757.png]]

- when 6116 is connected to 8080 address bus, A0 to A10 will determine the location inside the RAM 
- the other address lines will be ignored
- hence location 000 0000 0000 B can be accessed by the address XXXX X000 0000 0000B
- thus addresses from processor bus 0x0000, 0x0800, 0x1000 will all access the same memory location 0x0000H
- this is inefficient way of using address bus since even though 2^16 = 65536 locations can be selected individually, only 2K are used
- each responding to 65536/2048 = 32 different processor addresses

### **Memory Foldover**
- when memory address (or group of physical addresses) responds to several different processor addresses
- in small systems, it is tolerable, but there are 2 problems
	- first is that if more than 1 device needs to be attached to the bus. we cant fit it in
	- secondly programmer may access data from wrong memory location
- when connecting several memory ICs to an address bus, we can use logic gates as address decoders using K-maps or standard boolean logic
- however it is much easier to use demultiplexer or decoder due to the way memory is laid out which in many cases is in sequential block of address 

- commonly used is 74138 1 to 8 demux
- pin goes to low will correspond to binary input at pins A B C 
![[Pasted image 20250529233242.png]]
- 74138 can select 1 of 8 possible devices based on its ABC input
- if we add this to 13 inputs of 6116 now we have 14 inputs
- to take care of the last 2 we can choose to use logic gates or to use another 74LS85 4 bit comparator which makes decoding more versatile
- ![[Pasted image 20250529234433.png]]
- only A = B output when digital value at A inputs equal B and IA = B s high, OA=B pin will go low
- versatile as we do need inverted version

#### EXAMPLE : Design a 16K memory space starting from 8000H, using 6116 memory chips.
In designing a full decoding system using a 74138, we should note the number of address lines are used by the memory chip itself. This is because these lines cannot be used for decoding. Thus only the remaining lines on the host processor address bus is available. 

To summarize, we may use the following steps: 
1) Identify how many address pins the memory chip uses. 
2) Calculate the number of chips that are required in the design. 
3) Draw the memory map of the design. Do this by laying out the chips contiguously, that is, the starting address of a chip follows immediately after the last address of the previous chip. Write down the range of addresses of each chip in hexadecimal. 
4) Draw a truth table. This is the binary representation of the range of addresses. 
5) Looking at the bits, observe any pattern of numbers, for example, running binary numbers in the bits. 
6) Fit this pattern to the truth table of the 74138. First, see which address pins are to be assigned to inputs A, B and C. Then see how to assign the remaining address pins to the Enable inputs of the 74138. 
7) If there are unassigned processor address pins, assign them to the 74688. 
8) Finally, produce the schematic. 

Applying to the above example:
1) The memory device to be used is a 6116, which is a 2048 by 8 bit device. This device uses address pins A0 to A10. (211 = 2048). Each chip will take up 204810 or 7FFH addresses. 
2) Since we require 16K bytes in the design, we need 8 chips. (16K/2K). 
3) This 16K will occupy the range from 8000H to BFFFH. So the first memory chip will start from 8000H and occupy the address range 80000 - 87FFH. We continue until we get the following memory map: 
	RAM 1 - 8000H to 87FFH 
	RAM 2 - 8800H to 8FFFH 
	RAM 3 - 9000H to 97FFH 
	RAM 4 - 9800H to 9FFFH 
	RAM 5 - A000H to A7FFH 
	RAM 6 - A800H to AFFFH 
	RAM 7 - B000H to B7FFH 
	RAM 8 - B800H to BFFFH 
	
To draw the truth table, let us look at the first chip. It occupies the address range 8000-87FFH. Using binary, and noting that the MSB is address line A15:
![[Pasted image 20250529235730.png]]

In order to simplify the design process, we will introduce a notation. Instead of writing two lines with all the 0's and 1's, we will represent the above range by: 

A15 A10 A0 1 0 0 0 0 X--------X 8000 - 87FFH

"X" means that the value for the address line can be 0 or 1. The dashed line "X---X" means that address lines from A0 to A10 can be 0 or 1. So they are not available for general use. This highlights the fact that only address lines A15 to A11 are available for decoding. Proceeding in similar fashion for the other chips, we have the following truth table.

![[Pasted image 20250529235856.png]]

1. Looking at the truth table, we can see the address lines A13 to A11 taking on values that
increment, starting from 000 to 111. If we assign these lines to a 74138, we can enable
up to 8 devices one at a time, depending on the values of A13 to A11.
2. Comparing this with the truth table of the 74138, we see that A13 should be assigned to
input C, A12 to B and A11 to A. Note that this incrementing bit pattern is only true for
this situation. Other situations will have different patterns at different address lines. The
important thing is to look out for a pattern to fit to the truth table of the 74138.
3. It is convenient to let A15 to A14 be enabled by the 74LS85, so it activates when it has
the value 2H.

![[Pasted image 20250529235911.png]]

## Input / Output Decoding
- 8080 is able to access buffers and latches
- memory devices only use some of the available address line
- lower address lines will select single memory in memory device
- higher address lines from system are used by decode to select one of several memory devices
- also memory device will have Output Enable pin for a read and RAM device will also have a Write Enable pin

### Single address decoding
- buffers and latches have only a single address location
- PC architecture used up quite a few IO addresses so that there are few left for user
- other devices also may have used up other addresses
- thus we need to decode each device exactly to not activate other IO by accident
- since buffers have only 1 control pin and latches use clock pin, we need external gate to control access so processor reads are directed to buffers and writes are directed to latches

#### Example : Design an input port of address 30H and an output port of address 31H.

![[Pasted image 20250530003120.png]]

- 74LS85 is used with 74138  to decode individual IO address
- 74LS85 activate block of 8 devices through 74138
- starting address of this block will have A0-A2 at logic 0
- address is known as base address as all other IO addresses are simply added to base to get its address


# Keyboard interfacing
---
## Intro
- common input method from human to microprocessor is keyboard
- low cost, large amount o info may be input
- key works like single pole, single throw switch
- able to better detect presence of low voltage level, rather than high due to noise
- smaller keyboard have up to 16 kets or of a size that fits in a palm known as keypads
- consisting of pressure or touch activated switches arranged in a matric
- combination of software and hardware used to detect pressed key
- 2 basic types: 
	- encoded
		- include hardware necessary to detect which key is pressed and hold that data until new key stroke
	- non-encoded
		- no hardware and must be analyzed by software routine or by special hardware

### Reading from keyboard
- complexity of processor task when reading from a keyboard depends on number of keys detected
- input ports available on processor and amount of processor time dedicated to the task

#### Simple keyboard reading
- for small number of keys 1 to 8, we may assign one key to each buffer or port line
- to read, simply check for low level

![[Pasted image 20250530003806.png]]

#### Matrix organisation
- larger no. keys keyboard may be arranged in row and column fashion with n by m key organisation, aka matrix organisation
![[Pasted image 20250530003855.png]]
- 16 key device can be decoded with 4 input 4 output 
- optimal for 8 bit controller as it will use exactly 1 port
- port must be capable of splitting lower 4 bits in and upper 4  bits out

##### Scanning the keypad
- output column lines with "walking zero" pattern and sense the row lines to see if a low voltage is detected
- key identification technique is known as "row scanning"

![[Pasted image 20250530004110.png]]

- Let’s say the ‘3' key is pressed. If the processor did not output a “0" to pin 7, the
keypress will not be registered - that is, port pins 0 to 3 will still read “1". 
- Only when pin 7 outputs a “0" will pin 3 register a “0" as well.
- Larger keyboards require more select and sense lines. 
- First we can have latches to output the “walking zero” data to the column lines. Buffers are used to read the row lines. 
- When selecting the key organization, we should let the smaller number be
assigned to the row lines. 
- This is because we detect a key press through these lines,the status of which is read into a register. 
- Then software routines, most often rotates are used to detect which column has a “0". 
- This is time consuming.
-
(Note: The assignment of which lines are “rows” and “columns” is entirely arbitrary.
In this course we refer to the vertically oriented lines as columns purely for ease of
reference)

![[Pasted image 20250530004233.png]]

- since column line activated one at a time
- possible to substitute latches with decoders
- in this case N lines from processor will support 2^N columns
- shown below, 3-8 decoders can handle 24 column lines using 5 address lines but up to 32 rows can be decoded
![[Pasted image 20250530004311.png]]


### Interrupt Driven Keyboard
- simple solution is to make all column lines go to 0V
- if no keys pressed, it will present 1 level
- we would only need to AND all the row lines together
- a key pressed will then signal an interrupt and normal scanning can proceed to find out which was pressed

## Common Problems
- contact bounce
- key combinations
- type quickly

### Bounce
- when contact of a mechanical switch close, they bounce abit before staying together true when opening too
![[Pasted image 20250530005112.png]]
- solution is to wait for key to get stable ~ 20 ms
- can be done by hardware filtering or software-delay routine
- hardware is to use RC filter and requires same circuitry for each key
- useful if only a few switches

### Multiple key presses
- when 1 key is held down, essential to detect to prevent wrong codes from being generated
- 2 techniques are N-key rollover an N-key lockout

#### N-key rollover
- Software simply ignores reading until one key closure is detected
- last key to remain pressed is correct one
- used when software routines are used to provide keyboard scanning and decoding
- if order pressed is not crucial, is possible to store all closures with an internal buffer
- Hardware, second and later key closures are prevented from generating a strobe until earlier ones are released
- this is achieved with an internal delay mechanism which is latched as long as other key pressed

#### N-key lockout
- N-key lockout takes into account only 1 key pressed
- any additional keys pressed and released do not generate code
- the system is simplest to implement and most often used ]
- however might be objectionable to user as it slows down typing s each key must be fully released before next key is pressed down

#### Phantom Key
- most system need a diode in series with every key in order to eliminate problem creaeted when 3 adjacent keys at right angle are present
- increases cost significantly and is seldom used on low cost systems
- effect is that another key seems to be pressed in addition to the 3
- this is the "phantom key"
- consider 3,6,7 pressed at the same time and column 6 is scanned
![[Pasted image 20250530005843.png]]
- even though key "2" is not pressed, row 3 has "0" value appearing there due to flow of current in other 3 switches
-  key "2" is the phantom key

code to fix phantom key:

```

unsigned char ScanKey ();
unsigned char ProcKey ();

#define Col7Lo 0x7F               /* column 7 scan */
#define Col6Lo 0xBF               /* column 6 scan */
#define Col5Lo 0xDF               /* column 5 scan */
#define Col4Lo 0xEF               /* column 4 scan */
#define TRUE 1                    /* neater to use! */
unsigned char ScanCode;           /* hold scan code returned */ 


void main (void) {                /* main entry for program */
unsigned char i;
	 while (TRUE)
	 {
		i = ScanKey();
		if (i != 0xFF)            /* if key is pressed **/
			LEDPort = Bin2LED[i]; /* output to LED */

	 }
}                                 /* loop forever */

/* Check for key press: if none, return 0xFF */ 
unsigned char ScanKey()
{
	KbdPort = Col7Lo;            /* bit 7 low */
	ScanCode = KbdPort;          /* Read */
	ScanCode |= 0xF0;            /* high nybble to 1 */ ScanCode
	&= Col7Lo;                   /* AND back scan value */
	
	if (ScanCode != Col7Lo)      /* in<>out: get key & disp */
	return ProcKey();
	
	KbdPort = Col6Lo;            /* bit 6 low */
	ScanCode = KbdPort;          /* Read */
	ScanCode |= 0xF0;            /* high nybble to 1 */
	ScanCode &= Col6Lo;          /* AND back scan value */
	
	if (ScanCode != Col6Lo)      /* in <> out, get key */
	return ProcKey();
	
	KbdPort = Col5Lo;            /* bit 5 low */
	ScanCode = KbdPort;          /* Read */
	ScanCode |= 0xF0;            /* high nybble to 1 */
	ScanCode &= Col5Lo;          /* AND back scan value */
	
	if (ScanCode != Col5Lo)      /* in <> out, get key */
	return ProcKey();
	
	KbdPort = Col4Lo;            /* bit 4 low */
	ScanCode = KbdPort;          /* Read */
	ScanCode |= 0xF0;            /* high nybble to 1 */
	ScanCode &= Col4Lo;          /* AND back scan value */
	
	if (ScanCode != Col4Lo)      /* in <> out, get key */
	return ProcKey();
	
	return 0xFF;                 /* no key press rtn with FF */
} /* main */

/* Procedure here */ 
unsigned char ProcKey()
{
unsigned char i;                  /* index of scan code returned */

for (i = 0 ; i <= 12; i++)
	if (ScanCode == ScanTable[i]) /* search in table */
		return i;                 /* exit loop if found */

 if (i == 12)
	return 0xFF;                  /* if not found, return 0xFF */
}
```


# Top Down Design with UML
---
## Introduction
- microprocessors are fabricated using Large Scale Integration (LSI) technology 
- unit cost of each processor is very low
- however, development of systems using microprocessor tens to be hgih
- proper design techniques would help reduce development cost


### Why microprocessor-based
- microprocessor offer opportunities for products and features which are not achievable by other means
- its difficult to achieve range of features found in today's electronics
- eg, it would be almost impossible and not economical to design a compact disk player using logic gates alone

### Implications of incorporating a microprocessor
- testing the microprocessor based system is huge hurdle
- firstly, software needs to be extensively and thoroughly tested
	- underlying faults arise from OS, changing it is often impossible
- secondly, hardware of the system is almost as difficult to test as software
	- as hardware interacts with software and might be difficult to isolate whether error arises from hard or software
- microprocessor only deal with digital data
- interface must exist between it and its peripheral devices to convert data


## Product Development
**Trends in electronics industry**
- even though products have shorter product life
- every version needs to have high performance to price ratio due to competition in market
- resulting in the following:

1. Manufacturers shorten product design cycle using improved design methodologies
2. Manufacturers invest in tools and resources to improve and increase product features

## Product Design and Development Activities
- Product design is a human process
- design is a process that involves communication, creativity, negotiation and agreement
- System designers do not work alone
- theres a strong temptation to sit down and product the system asap
- hard and software designers need to understand each other so that final product meets requirements of the client
- often in design and production process, communication, negotiation and agreement aspects are left out
- a notation which is clear, consistent and able to communicate within a system development team, and with clients and other 3rd parties is needed

![[Pasted image 20250601003249.png]]

- systems were constructed using a "waterfall" approach traditionally
- as water flows down from the top, the approach starts off by having clients formally agree on a requirements document
- designers would then come up with a design which will be further agreed by the clients
- the system would finally then be implemented and followed by an endless process of maintenance

- modern ideas move away from waterfall
- many system developers use iterative method
- development cycles with each cycle making up of analysis, design and implementation
- each subsequent cycle builds on earlier cycles
- one method for visualizing this is Unified Modeling Language (UML)
- UML is used for specifying, visualizing, constructing, and documenting features of a system
- UML represents a collection of proven best engineering practices in modeling of large and complex systems

- UML represents an important part of system development process
- UML uses mostly graphical notation to express design of system projects
- UML helps project team communicate, explore potential designs, and validate architectural design of systems

## Product Requirement
- first stage in both methods is requirements gathering
- difference in 2 methods is that iterative is only interested in capturing most important features in the beginning and allowing subsequent cycles to handle less important ones
- waterfall starts off with intention of obtaining all features in the system
- initial description of product's intended functions are obtained from the customer

### Need for product requirement
2 reasons :
**Avoid "Creeping featurism"**
- there is always the desire to interfere continually with product specs during development as there are many choices available
- this will significantly alter cost and time needed

**Avoid "Missing features"**
- worst thing is to forget required features and by the time its noticed, its too late

### Goals and Constraints

**Goals**
- aspects of customer requirements which guide the system designer where freedom of choice exists
- eg, hardware cost of motor interface be minimized

**Constraints**
- aspects of customer requirements which limit the freedom of choice of system designer
- eg, should include particular type of component

- Constraints narrow the scope of the project
- Goals are customer preferences to be considered
- Goals and Constraints may affect the same design feature
- should not be any constraints that restrict freedom of designer unnecessarily
- avoid contradictions in list of goals

Types of Constraints:
<br/>

| Area of Constraints | Examples |
|---|---|
|Microprocessor |Particular type specified by customer|
|Other Hardware |Some or all of additional hardware specified|
|Field repairability |PCBs must be plug-in|
|Power Supply |Must run on batteries|
|Environment |Must be insensitive to radio interference|
|Size | Must fit within particular dimensions|
|Unit Component Cost | microprocessor and interfaces <br/> must cost less than particular limit|
|Development Cost |Amount of available for supporting<br/> equipment, consultation, etc|
|Development Time | Prototype available for demo at an exhibition|


## System Analysis
- consists of activities that include examination by system designer of initial customer requirements
- some considerations are:
<br/>
**Sub-system Identification**
- identify hardware components or sub-systems in the product
<br/>
**Dynamic Modeling**
- capture how the parts of the system behave and how they interact with each other
<br/>
**Feasibility Studies and/or simulation**
- if designer does not know whether the product can be designed to specs
- they can perform feasibility studies and/or simulation to remove uncertainty without expense of designing to prototype stage
<br/>

### Sub-system Identification
- identify componenets that would make up whole system
- components that perform a function and does not have to be extensively programmed by the designer
- advantage of subsystems are that they are complete products whose behavior and cost are known
- examples such as microcontroller, keypad, stepper motor

### Dynamic Modeling
- similar to a form of story telling
- a task is part of overall product function which is to be provided by suitably programmed microprocessor system
- obtained from customer requirement a statement of what the system needs to do
- use dynamic models to analyse the behavior of the system
- look at functions of  the system we are analyzing, thinking through them in terms of scenarios and see how each scenario affect each individual sub system
- output of this phase is the production of interaction and use case diagrams

### Feasibility Studies/Simulation
- important to have an idea whether particular algorithm has chance of working
- done without too much expense or hardware construction

#### Feasibility Studies
- special purpose activities aimed to answer a particular question or group of questions about an aspect of the customer requirement
<br/>
- some questions to ask are:
	- can it meet project constraints
	- is the performance of hardware systems sufficient
	- does algorithm work correctly

<br/>
- there may be abit of hard or software design but should be easily done
- compared to building a full prototype 
- prototype is designed to answer most of remaining questions about the product
<br/>
#### Simulation
- means of rapidly and easily exploring various alternative answers to more general questioons
- usually done in software

<br/>
- Simulation is used to build systems which in some ways behaves like actual product
- Various versions of proposed system can be tried without extensive redisgn
- Principal us of simulation in microprocessor-based product development is for evaluating competing algorithms
- if they are complex, we may not be able to evaluate them based on logic or manual calculations

## System Specifications
- produced  as a result of system analysis
- overall controlling document in a project
- UML diagrams that are produced will form part of this documentation
- find the following:
	- Specs of product function
	- Complete description of what the system should do
	- performance requirements it must meet
	- specific details of operator/system interaction
	- specs of system's interface with external environment
	- procedures for error handling and diagnostics
	- constraints on design and on development of project
	- Goals to aim for in design
- Specs of required behavior should include:
	- Identification of microprocessor tasks
	- description of how product as a whole is to interact with its environment
	- particularly for products with substantial human interaction
- useful way of providing specs is to product a USER'S MANUAL
- start of system design phase of a project marks an important transition for design engineers as they must make decisions without outside help

### Decision making in system design
- involves making important decisions on:
	- Build or buy parts
	- Choice of microprocessor
	- Hardware or Software

### Build or Buy
- Building from scratch may:
	- not work first try
	- need modification
- Commercially available parts will not suffer from problem above
- another advantage is cost and performance is known with a high degree of confidence at start of project
- compared to overestimating own abilities to design and build part
- good practice for beginner to use commercially available parts as must as possible in early design

### Choice of Microprocessor
- getting right processor can give strong market advantage
- but using wrong chip can weaken an architecture
- prolong design cycle or cripple a product
- Cost is the overriding factor
- Other factors to consider:
	- Software Availability - code used for the product
		- is there large source for code or old code to be reused?
		- software comprises 70% of one time engineering costs
	- Readily available in quantity  - reliable second sources
		- important for long term production
	- Experience of other 
		- training for new processor is long and costly

#### Development Tools
- developing/ programming is expensive 
- reduce time, microprocessor vendors provided info very quickly
	- such as data sheets and programmer's guide

- we also need to ask the following:
	- Does it have the features to do the task needed?
	- do we have adequate development time to overcome the deficiencies in that part?

<br/>
- Sometimes vendors also provide development support in terms of ready-made boards ( they include processor, memory and IO ports)
- similar, evaluation kits which have more hardware and facilities for software development may include monitor program to download and execute user programs through a serial port and even modify portions of memory
- these kits allow additional hardware to be added easily by providing additional connectors and sometimes a prototyping area

<br/>
- Software development tools should also be adequate
- assemblers, compilers with simulators and other debugging tools should make programming easier
- especially important if microprocessor architecture is inadequate in many areas

- Emulator support is of highest priority
- emulator makes hardware debugging more like software debugging
<br/>
#### Processor Capability
- processor should be fast enough to support application at hand
- especially for real time applications
- addressing space should be enough for program and data

### Software vs Hardware
- Processors can be programmed to perform many different tasks
- Engineer's tasks is to utilize available processor hardware by writing necessary software
- however there is still a need for some electronic hardware design in the interface

#### Software/ Hardware Trade-Off
- There are a number of task which can be achieve by both means
- especially those that interact with external environment and devices
- eg, serial port may be written by manipulating port pins or it may be purchased as a hardware component
- some deciding factors:
	- ``` Unit Cost  =  Component Cost + Production Cost + Development Cost / Total No. Units```
	- **Hardware Implementation**
		- has higher associated cost but has
			- less development effort
			- higher processing speed as processor does not have to work on this
	- **Software Implementation**
		- No component cost
			- but may involve large amount of development effort
			- in most cases, operation is much slower


<br/>
## System Design
- UML is a modern technique of system design 
- specified as documentation to be used for all systems proposed in project tenders submitted to British Government

### Unified Modeling Language (UML)
- language for specifying, visualizing, constructing, and documenting features of a system
- UML represents collection of best engineering practices that proven good for modeling of large and complex systems
- UML represents an important part of system development process
- UML uses mostly graphical notations t express design of system projects
- UML helps project teams communicate, explore potential designs, and validate architecture designs
<br/>
Primary Goals in design of UML:
1. Provide users with ready-to-use expressive visual modeling language to develop and exchange meaningful models
2. Provide extensibility and specialization mechanisms to extend core concepts
3. Be independent of particular programming languages and development processes
4. Provide formal basis for understanding the modeling language
5. Support higher-level development concepts such as collaborations, frameworks, patterns and components
6. Integrate best practices

<br/>
#### Types of UML Diagrams
- UML diagrams are designed to let developers and customers view a system from a different perspective and in varying degrees of abstraction
- altogether 6 diagrams to be drawn for UML conformant documentation
- we only draw 2 interaction and use case diagram

<br/>
- UML use case diagrams display relationship between actors and use cases
- similar to C switch case.
- To draw, must first imagine you as a user and would then come up with ways offered to you by system to interact with it

<br/>
- Interaction Diagram consist of:
	- Sequence Diagram : display time sequence of objects participating in the interaction, consisting of vertical dimension (time) and horizontal dimension (different objects)
	- Collaboration Diagram : display interaction organized around objects and their links to each other

#### Hardware Testing
- tested on a sub-system basis using simple programs designed to fully test out hardware
- test programs should be kept as simple as possible to eliminate possibility of software errors
- this assumes basic hardware is working correctly
 <br/>
 - Modern instruments have  been devised to cope with short-comings of simple test techniques
 - such as Logic Analyzers and In-Circuit emulators


#### Software Testing
- after all code has been written and converted into machine code, it must be tested to verify all functions correctly
- this requires a "protected" environment to test the software
- this allows us to control and monitor inputs and outputs of overall system precisely
<br/>
- eg, environment provided by monitor or debugger utility program in microprocessor development system where performance of system being tested can be examined in isolation
<br/>
- All possible conditions going thru the control surface is tested
- eg, "IF" type instructions should be tested for both condition 
- this is so that all instructions will be checked and do not cause errors later in the project
- the aim is to minimize number of untested software codes which have to be checked during system integration
- software that depends heavily on special features provided by actual hardware should be tested right away from the start

## System Integration
- process of bringing together individually designed and tested subsystems to form the full system
	- Normally begins by building whole system from the bottom upwards and implementing tasks as illustrated in the interaction diagrams
	- Extensively tested the tasks that needs to be performed by the system to verify that no problems have been introduced when linking subsystems together
- Ideally, top-down design has been rigorously applied then system integration should be straight forward
- however, despite being careful, there may still be inconsistencies that will appear only when integrating
- often caused by focusing only on one aspect of the design and neglecting interfacing issues
- if integration is done properly, complete system can be simply implemented as 1 series of subroutine calls within main loop

### Problem Resolution
- when testing the system, we need to check if system carries out every task as needed to find inconsistencies
- these bugs must be resolved if the system is going to work
- its essential to have access to the initial documentation and update it with list of bugs found
- if we patch bugs with an ad hoc method, we are likely to get more and more trouble especially if undocumented
- although its slower, its more cost effective in the long run to go back to a task to find out what and where went wrong and then make modifications which are consistent throughout the system
- when the list is more or less resolved, we have created a prototype of the needed system

**Prototype**
Initial version of the system
2 types:
	- Demonstrate validity of the system design
	- Show what the system will ultimately look like
		- should be very careful about satisfying other needs such as outward appearance or physical construction. these should only be done if it helps to confirm the original design concept works

<br/>
**System Prototype withou Hardware**
- The development system used as hardware, where input is a keyboard and output on a display
- when design has been proved, hardware can then be bought or constructed to make  2 with different goals
<br/>

**Hardware Prototype**
- Prototype system is separated from development system
- Software is transferred to prototype hardware by:
	- EPROM
	- In-Circuit Emulator (ICE)
- this marks transition from prototype to manufactured product
- it may involve changes in original design for the following reasons:
	- when product manufacture in quantity, assembly cost becomes a major factor in price
	- Need to ensure system can be assembled and tested by relatively unskilled staff
	- require documentation such as test specification, service manuals, and user's manual

### Testing of Products
- different from testing during development stage
	- need to perform fault-finding relatively quickly by use of special test jigs and/or sophisticated test instruments
	- Test procedures must be devised

<br/>

## SAMPLE DESIGN
<br/>
You are required to design a microprocessor based egg timer.
This device will show the egg type and boil it for a specified period of time depending on the egg type.
It will sound an alarm to signal when it finishes and show a message as well. 
It must be waterproof.

Perform System Analysis and System Design using UML. 
Draw a case and interaction diagram of the proposed system. 
Develop two of the sequential diagrams that you will use

<br/>
Firstly identify subsystems in proposed system
Note that we do not need a temperature sensor as boiling temperature of water is constant
breakdown of system into subsystems :
- Microprocessor
- Alarm
- Timer
- LCD
- Heating Coil
- Keypad

Draw UML use case diagram to express user requirements
diagram helps uncover user requirement that may not be stated earlier on

### Use Case Diagram
- Looking at example from user's perspective
- user uses egg timer for cooking egg
- so it should look like this:
![[Pasted image 20250601145614.png]]

- action marked "cook egg" is a function offered by the system
- the process of drawing such a simple diagram will help the designer identify functions that the system must purpose

<br/>

- Case diagrams are helpful in revealing requirements and planning the project
- in the beginning, most use cases should be defined but as the project continues, more functions might become visible as you explore how the system interacts with the user
- you might be able to uncover functions that the system should have but not explicitly written
- to cook an egg should have steps to "choose egg type" before we start to "cook egg"


![[Pasted image 20250601145914.png]]

- from this simple diagram, requirements  of egg cooker system can be easily derived
- the system will need to perform actions for all the use cases listed
- as project progresses, other use cases might appear and diagram can be easily expanded until a complete description of egg cooking system is derived, capturing all requirements that the system will need to perform

<br/>

### Interaction Diagram
- model the behavior of use cases by describing the way groups of objects interact to complete the task
- 2 kinds are sequence and collaboration diagrams

<br/>

- Interaction diagrams are used when you want to model behavior of several sub-systems in a use case
- they demonstrate how sub-systems collaborate with others
- hoever, interaction diagrams do not give an indepth representation of the behavior
- if you want to see specific object is doing for several use cases, we should use a state diagram - another component of UML
- to see particular behavior over many use cases or threads, use activity diagram - another component of UML

- To start drawing interaction diagram, first imagine how you would interact with the system
- the user, would select the egg type using key type and you would represent the interaction as in the left figure and note how the subsystem keypad is represented as:

![[Pasted image 20250601150444.png]]

<br/>

- In like fashion, other sub-systems will have similar diagrams
- the diagram shown below is often used to represent first interaction with the system in question
- in this case, first contact between system and you is the user selection of egg type for cooking either C(chicken) or D (Duck)
- ![[Pasted image 20250601150904.png]]

<br/>

- Develop interaction diagram further, after keypad is contacted, microprocessor would read key entered and display egg type selected
 ![[Pasted image 20250601151012.png]]
 
<br/>

**<u/>Developing User Case - "Cook Egg"**
- once microprocessor reads key entered and process it, it activates LCD display to show egg selected
- timer will start running for certain period of time depending on egg type selected and activate the heater coil

<br/>

- After time is reached, timer will then send a signal to microprocessor telling it time is up
- microprocessor will then send a signal to deactivate heater coil and update LCD display

![[Pasted image 20250601151504.png]]

- After egg is considered cooked, we need to activate the alarm 
- microprocessor will then reactivate timer for a shorter period of time
- then activates the alarm
- when timer runs out, microprocessor will deactivate the alarm
- finally microprocessor  would activate LCD to redisplay initial menu
![[Pasted image 20250601151711.png]]
complete interaction diagram :
![[Pasted image 20250601151731.png]]

- such a diagram would have helped implementation and would prove very useful in explaining implementation of your system to clients
- Should there be another way in which the user can interact with the system, you would need to repeat the method and produce a similar diagram depicting how the system would carry out the task



# Liquid Crystal Display LCD
---

## Intro
- widely used as output devices
- as they consume little current compared to LEDs
- also physically smaller and have color capabilities
- troublesome to interface with bare LCD
- LCD modules incorporate graphics processor and interface electronics
- modules have advantage of :
	- easily interface and control powerful display functions
	- not needing to refresh display
- Selecting LCD need 2 basic design decisions
	- size and format needed to display desired info
	- optical characteristics that look best in package, attract user to product

- Alphanumeric modules displays characters, numerals, symbols and some limited graphics
- normally connected to host processor through parallel data bus, although serial interfaces are available too

- various LCD modules are available from different manufacturers
-  LCDs come in many sizes, 1-4 lines, 16-40 chars per line, 5x7 or 5x10 dot display fonts
- Character heights spans 9.130" (3.31 mm) to 0.5" (12.71mm) 
- most formats are available in variety of packages to meet various mounting requirements
- multi line models offer best value when analysed by "cost per character" basis
- by using backlight models, they will be visible both in day and night
- extended temp modules can operate between -20 to +70 C

- >4 lines or >40 char across, graphic formatted module
- Graphic modules are also used for different sized chars, and when special fonts used like chinese or arabic


### LCD Fluid Types
- Fluid dye determines contrast ratio, viewing angle, temperature range
- 3 basic dyes:
	- TN (Standard)
	- NTN (High Contrast)
	- STN (Premium High Contrast)
- Many TN and NTN models are available in extended temp range


### Character LCD Controller
- Software determines what, how, where data is displayed on LCD
- Most char modules use Hitachi FD44780 IC or equivalent
- Features:
	- Built-in generator with 192 char modified ASCII char set
	- Ability to program up to 8 user defined chars
	- Bi-directional 8 or 4 bit bus interface
	- 80 char RAM
	- Auto reset on power up
	- Wide range of instructions such as:
		- Display Clear
		- ON/OFF
		- Cursor positioning
		- Display or cursor shift on data entry

## LCD Hardware Overview

![[Pasted image 20250803013527.png]]

<u>General Operation</u>
- module interfaces with host processor through data bus
- by controlling using RS pin, data goes to one of the 2 8-bit registers
	- Instruction Register (IR)
	- Data Register (DR)
- IR stores instruction codes such as display clear or cursor shift, address info for display data RAM (DDRAM)
- IR can only be written from host processor

- When host processor writes to DR, register will temporarily hold the data
- then it will auto transferred to DDRAM 

- When address info is written into IR, data is read then stored into DR from DDRAM 
- Data transfer from module is completed when host processor reads the DR

- When reading from module, DR will hold data read from DDRAM
- After host processor does a read, data at next address is auto read (Special feature of module)
- data will be sent to DR in preparation for next read

<u>Data Display RAM </u>
- used to start data to be displayed
- 8-bit chars "modified" ASCII codes
- can handle 80x8 bits or 80 chars
- if actual no. char are less than that, unused  DDRAM can be used as general data RAM

<u> Character Generator ROM/RAM </u>
- CGROM holds actual bit patterns to be shown on display
- patterns are constructed using 5 x 8 bit matrix
- internal logic in LCD module takes data from DDRAM
- then calculate where bit patterns for that data is stored in CGROM
- the patterns are shifted out to display drivers and then to individual LCD display elements

- CGROM in standard module has 160 char in 5x8 bit pattern format and 32 char in 5x10 pattern

- users can defined 8 special chars or symbols in 5x8 format (4 for 5x10)
- the bit patterns are stored in CGRAM
- once programmed, new chars may be accessed as if they are in normal CGROM
- it must be reprogrammed if power is interrupted

<u> Relationship between DDRAM and CGROM </u>
- eg, value 62H (ASCII 'b') is send to DR. from there it goes into DDRAM at address specified by Address Counter
- module logic will access bit pattern stored in CGROM
- then its shifted out and displayed on actual display
</br>
![[Pasted image 20250803123428.png]]
</br>

- '1' will turn on the pixel in the row
- char shown as 5 x 7 dot matrix but stored as 8 byte (8x8) array


<u> Busy Flag BF</u>
- when BF = 1, module is in internal operation mode
- next instruction will not be accepted
- if host processor performs a read, bust flag will output DB7
- next instruction must be written after ensuring BF = 0

<u> Address Counter AF </u>
- AC used to access data in DDRAM and CGRAM
- when "set address" instruction is sent  to IR, address info is sent from IR to AC
- type of instruction determines if DDRAM or CGRAM is addressed

- after writing to DDRAM, AC is auto incremented by 1
- when reading, AC auto decrease by 1
- AC contents are then output to DB0 - DB6
- AC register holds only 7 bits

- when addressing CGRAM, cursor/blinking effect will appear
- ignore as AC is pointing to CGRAM address and thus not affect DDRAM 

- through RS signal, 2 registers can be selected as shown

|RS |R/W | Operation|
|-|-|-|
|0|0|Write to IR to start internal operation (eg, display clear)|
|0|1|Read BF (DB7) and AC (DB0 to DB6)|
|1|0|Write to DR for display (DR to DDRAM)|
|1|1|Read from DR the contents of DDRAM (DDRAM to DR)|


<u>Timing Generation Circuit </u>
- generates timing signals for operation for internal circuits like DDRAM and CGROM
- RAM reads timing for display and internal operation timing by host processor access are generated separately to avoid interfering with each other
- thus when writing data to DDRAM, there will be no side effects such as flickering


<u> Cursor/ Blink Control Circuit </u>
- generates cursor or character blinking
- blinking cursor will appear with digit located at DDRAM address set in AC

- eg, when when AC is 08H, cursor position is displayed at DDRAM address 08H
- when char is written to DR, ASCII char will appear at cursor position
</br>
![[Pasted image 20250803124627.png]]
</br>

### Relation between DDRAM and Display Characters
- DDRAM has cap of 80 chars
- physical display has < 80 chars
- display is a "window" of the DDRAM
</br>
![[Pasted image 20250803125120.png]]
</br>

- when < 80 chars, display begins at starting position like above
- 00H corresponds to char position 1

- So when we write DDRAM address 00H, it will appear at display position 1

</br>![[Pasted image 20250803125408.png]]</br>

- in 2 line display, first char on the next line is not "one more" than the last char on previous line
- it is actually found at 40H
- to put data on second line, Set DRAM Address instruction must be sent

- its possible to shift display so that first char does not correspond to DDRAM location 0
- thus this can make some chars rotate thru the display when data is entered
- it also lets small displays (eg, 2x16) to have data stored in non-visible areas of DDRAM and have them shifted to be viewed

### Character code and bit patterns
![[Pasted image 20250803130850.png]]


## LCD Software Control
- Only IR and DR of LCD module is accessible to host processor
- by writing to them, we control how data is displayed

### General Considerations - Timing
- LCD module takes relatively long to execute instructions
- on average it is around 40 μs
- when instruction is being processed only BF read instruction can be executed
- BF is set to 1 and will go to 0 when done

<u> BF vs standard time delay </u>
- Most of time, data is written to LCD module and keeping tack of state is usually done by processor
- in this case its not necessary to read from LCD very often as we can just read BF and use a time delay of arnd 40 μs
- in most cases, it will save the need of buffer (or bidirectional port) to accommodate the read function

 4 Categories of instructions:
1. Setting of Modes of operations, such as display format, data length, etc

2. Set internal address for both DDRAM and CGRAM

3. Perform data transfer with internal RAM

4. Perform miscellaneous functions


- Normally most commonly used instructions are performing data transfer to DDRAM
- auto increase/ decrease feature of AC register makes it easier to program the module

### Default Initialization
- before programming, we must know initial state when power is turned on
- following instructions are executed during initialization period
- lasts for 15 ms after power supply rises to 4.5V
- BF = 1 until initialization ends
- following is internal initialization routine:

1. Clear Display
2. Function Set
	DL = 1 : 8 bit interface
	N = 0 : 1 line display
	F = 0 : 5x7 dot matrix
3. Display OM/OFF Control
	D = 0 : Display Off
	C = 0 : Cursor Off
	B = 0 : blink Off
4. Entry Mode Set 
	I/O =1 : +1 increment
5. DDRAM is selected

- if power is not applied successfully, routines will fail
- is different parameters such as 2 line display, host has to perform initializing
- after initializing, we should have clear display with flashing cursor in top left 
- cursor will then increase to right with each EERAM write command

### Instruction Table
</br>
![[Pasted image 20250803132509.png]]
</br>


### Special Operation Modes
<u> 4 Bit operation </u>
- LCD modules are able to receive bytes as 2 4 bit nybbles
- many cases it can save extra 8bit latch
- complexity increase can be hidden in host processor output routine
- main user program then calls the routine with standard 8 bit byte
- leaving 4 bit transfer to be handled by routine
- also need to initialize module into 4 bit mode

</br>
![[Pasted image 20250803133249.png]]
</br>


<u> Display Shift </u>
- DDRAM can be used for displays for advertising when combined with display shift operation
- when S =1, display is shifted
- what is displayed is depending on Entry Mode Set instruction
- display shift operation only changes display position with DDRAM contents unchanged



## Further Initialization considerations
</br>
![[Pasted image 20250803134305.png]]
</br>

- Set up 2 line LCD with 5x7 font, 8 bit data transfer with auto increment and shifting when writing


## LCD Hardware Design


### Power Supply Requirements
<u>power Supply to Module Connection </u>


- Modules require +5V at 1 to 10 mA
- Extended Temp and some high contrast modules need -5V also at low current
- inexpensive ICs convert +5V to -5V efficiently
- if display has backlight required power must also be budgeted

- module's logic ciurcuit have 3 connections to PSU
- VDD ( +5V DC)
- VSS (Ground)
- V<sub>o</sub> (View Angle adjustments/ contrast/ bias control)
- Contrast can also be controlled with DAC 

![[Pasted image 20250803141444.png]]


### Logic Connections
- LCD Module appears as 2 8 bit registers to a microprocessor system
- there are 3 control pins, making total 11 pins or 2 registers
- interfacing with the module to existing system involves
1. applying proper viewing angle voltage to displays V<sub>o</sub> pin
2. connecting module to host processor - directly to port or through buffers and latches
3. developing strobe signal for "E" signal
4. applying appropriate "RS" and "R/W" signals to modules


![[Pasted image 20250803144258.png]]

- 8 bit mode is more straightforward and control is simple
- we need 8 data bit and 3 control 
- we need 2 8bit devices to interface with it


![[Pasted image 20250803145517.png]]

<u> Timing Aspect of Alphanumeric LCDs </u>
- classified as slow peripherals
- Enable "E" signal is key signal
- this clocks the data and control signals into the LCD module
- E signal must be clean positive going digital strobe
- active while data and control information are stable
- 2 control lines RS and R/W must be set before activation of E
- must remain stable for 10 ns after fall of E

- choice of host connections are RD and WR strobes (or R/W line) 
- connect E pin as a chip select line
- E strobes must be 450 ns wide (PW) minimum
- most processors operate at higher speeds than this and its not practical to slow down the host for this purpose
- often we latch both data and control info toggling E signal this way
- or if a port is free, it may be used as well

- When parallel port supplies RS, R/W and E, all lines should not change  together
- it will result f a single instruction is employed, it would violate the set-up requirement
- instead second instruction must independently set the E bit high after other lines are set

- Another option is to tie R/W and RS pins to host address lines which are set up earlier in machine cycle
- data bus must set-up 195s prior to fall of "E" 
- the lines must hold for at least 10 ns after E falls
- most host strobes meet these requirements

- Normally E strobes would be approximately 40 ms apart
- which is maximum display thoughput


<u> 4 bit connection </u>
- iadvantage is that only needs 4 data lines and 3 control lines
- so 1 8bit port will be enough
- reduces no. of 8 bit devices used
- only slight increase in software complexity
- 2 ways to connect up:
	- directly to port
	- through latch

![[Pasted image 20250803150655.png]]

- data transfer between module and host processor is completed after 4-bit data has been transferred twice
- 4 high order bits (DB4 to DB7) first then low order bits (DB0 to DB3)
- if busy flag is used, it must be checked after 4-bit data tranffered twice
- one being instruction
- 2 more 4-bit operation ten transfer busy flag and address counter data


<u> 8 bit initialization </u>
![[Pasted image 20250803150842.png]]

- 15ms delay after power up before initialization starts
- then 4 1 ms and 100 μs delays where "3X" codes are sent
- following are sample init code for various configs (all in hex)



1 line display with 5x7 font 30, 30, 30, 30, 08, 01, 06

1 line display with 5x10 font 34, 34, 34, 34, 08 ,01, 06

2 line display with 5x7 font: 38, 38, 38, 38, 08, 01, 06

Of course, a 0E code should be sent to turn on the display!


<u> 4 bit initialization </u>

![[Pasted image 20250803151125.png]]

- modules will operate from 4-bit wide data bus
- data is transferred over data lines
- D7-D4, D3-D0 may float
- 8bit hex code is sent one nybble at a time
- higher nybble first
- function set in initialization routine must change to accommodate this mode:

2 line display with 5x7 font 28, 28, 06, 0E, 01