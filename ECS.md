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


# Bus Systems and Devices

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