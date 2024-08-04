HDD Scheduling
- FCFS
	- As the name implies the FCFS serves the first request first. The algorithm is very fair but it does not provide the fastest service due to how harddrives work. Because HDD have moving parts its quite ineffective to move to different parts of the disk for each request. This results in A very high Seek time as this is effective by seek distance
	- ![[Screenshot 2024-06-19 at 19.21.13.png]]
- SCAN scheduling
	- Instead of moving "randomly" to the blocks the scan algorithm Moves the disk arm to one end of the disk and then towards the other end. While moving the queue is serviced.
	- ![[Screenshot 2024-06-19 at 19.21.53.png]]
	- Because we move from somwhere in the  middle to one end the other end will have a higher densitiy and a longer wait time because of the time the disk head needs to get to a part that hasnt been read
- C-SCAN scheduling
	- Also called circular scan is almost the same as SCAN. C-SCAN provides a more uniform wait time. Like SCAN C-SCAN also moves the head from one side of the disk to the other but unlike SCAN when we hit the end we move back to the start of the disk instantly instead of servicing requests underway
	- ![[Screenshot 2024-06-19 at 19.39.08.png]]

NVM Scheduling
- HDD disk scheduling algorithms try to minimize the amount of head movement and thus seek time. Because NVM do not have moving parts We can simply use a simple FCFS policy

Storage managment
- bad blocks
	- Because disks can have inacuries and are prone to failure it could happen that blocks on the disk do not work as intended. this is called a bad block. On older disks we scan the disk to find bad blocks when formatting the disc and the blocks are flagged as unusable. When blocks go bad during use we have to run a special program manually
	- Newer disks are smarter. The controller keeps a list of bad blocks on the disk. The lsit is initialized during formatting at the factory. The list is the update through the life of the disk. A disk can also have spare sectors. The controller can then say to use them instead

RAID Quick overview
- Redundant array of independent disks. Raid is often used when there is "a lot" of data and we want the data to be restorable incease of disk failure. THis is especially important for things like data centers. Or NAS storage in companies where the disks are running 24/7/365
- There a differenet raid levels that use different methods to provide redundancy.
	- Raid 0: This is like combining all the drives into one drive. So the data written is scattered among them and there isnt any real redundancy
	- Raid 1: Here we mirror each drive. This is pretty effective put also costly as we halve the storage or need double the amount of drives.
	- these can also be combined

I/O hardware
- Devices need to communicate with the computer. This can happen through a  connection point like a port or over wifi. If the devices share a common set of wires its called a bus. In most computer today the PCI bus is used for communication inside the computer.
- Most devices are connected through the PCIe bus. Espacilly the devices that need high fast communication like with other parts like cpu and disk. For slower things we have the expansion bus which connects things like USB ports. Disks are connected through the SAS controller(serial atteched SCI)
![[Screenshot 2024-06-19 at 21.35.42.png]]
Interrupts
- The cpu has a physical wire called the interrupt request line. The cpu senses the wire after every executed instruction. If the cpu senses an interrupt it does a state save and jumps to interrupt handler routine. The interrupt handler determines the cause of the interrupt and executes the necesary things before performing a state restore and returning the cpu to the executoin state before the unterrupt. An example could be a device wanting to transfer data from disk into memory.
-  We split the interrupts in maskable and unmaskabel interrupts. Maskable interrupts can be ignored by the cpu until critical execution is finished. Unmaskable interrupts can not be ignored
![[Screenshot 2024-06-19 at 19.07.24.png]]

Direct Memory access(DMA)
- DMA is usefull for transfering larger amounts of data. Instead of many interrupts we only get a single one for all of the data. For that to work we need a DMA controller so we can bypass the cpu to transfer data directly between the device and memory.

