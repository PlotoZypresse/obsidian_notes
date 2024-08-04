## Key words
- Interrupts
- Systemcalls
- USer and kernel mode
- Interprocess comunication
- Direct memory access
- OS structure
- Services
- OS Instalation
- Boot process


## Notes
- interrupts
	- interrupts are used to interrupt the CPU
	- Interrupts can be triggerd by hardware or software
	- When interrupted the cpu transfers execution to a fixed location
	- As interrupts are time critical they need to be handeld fast
	- Often a table of pointers to interrupt routines are used
	- This is called the interrupt vector
	- Every routine is indexed by a unique number for easy access
	- Software intterupts are done by system calls
	- Traps are software generated interrupts caused by an error or user request
	- hardware interrupts have a wire called the interrupt-request line that the cpu checks after every instruction
	- ![[Screenshot 2024-06-14 at 17.17.54.png]]
	- 
- system calls
	- interface made available by the OS for services
	- Example copying a file
		- the specific system calls that are needed  are called 
		- like: opening the input and output files, reading from the file, writing to the file and more
	- for ease of use there is an  api. So instead of making all these system calls by them selves in the code we can call the copy command that then calls all the system calls for us![[Screenshot 2024-06-14 at 12.57.45.png]]
	- types of Syscalls
		- Process controll: fork(), exit(), wait()
		- File managment: open, read, write close
		- Device managment: ioctl, read, write
		- Information maintenance: getpid, alarm, sleep
		- Communitcations: pipe 
		- Protection: chmod, umask
- user kernel mode
	- For saftey reasons we have User mode and kernel mode. This is to prevent unauthorized code execution. But we must be able to distinguish between OS code that needs all the priviliges and user code that doesnt need these priviliges. To differentiate between these two modes, that are called user mode and kernel mode we use a mode but. For safety reasons this is actually a implemented in hardware.
	- In easy words when the OS executes on behalf of the user it is in user modes and when the user code request services from the OS, like sys calls it switches to kernel mode
	- ![[Screenshot 2024-06-14 at 14.31.02.png]]
	- User mode
		- when user code is executed
	- Kernel mode
		- when user code needsd acces to the system via systemcalls
- interprocess communication
	- Message passing
	- Shared memory
- Direct Memory acces
	- Direct memeory access (DMA)![[Screenshot 2024-06-14 at 14.07.46.png]]
	- Moving small amounts of  data using interrupts is not a problem. But when there are large amount of data being moved there would be a lot of unecessary interrupts
- 
- os structure
	- monolithic 
		- everything is in one file
	- layerd
		- Different layers from hardware up to user interface
	- micro kernels
		- as much as possible is moved away from the kernel into user space
		- comunication through message passing
		- easy to extend
		- easy to port to new architectures
		- more secure
		- more reliable as less code runs in the kernel
		- slower
		- ![[Screenshot 2024-06-14 at 15.52.20.png]]
	- most OS are a combination of all of those

- services
	- OS services
		- system programs
	- System Services
		- UI
		- Program execution
		- Filesystem manipulation
		- Communications
		- Error detection
		- Resource allocation
		- Logging
		- Protection and security
- OS Instalation
	- Write or get the OS source code
	- Configure OS for the system it will run on
	- Compile
	- Install
	- Boot
- boot process
	- A small piece of code called the boot strap program or the boot loader locates the kernel
	- The kernel is loaded into memory and started
	- The kernel initializes hardware
	- the root filesystem is mounted




[[Semester_4/OS/Chapters 1-2/Review|Review]] [[Etime 09.02 chapter 1 and 2]]
