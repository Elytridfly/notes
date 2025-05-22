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












