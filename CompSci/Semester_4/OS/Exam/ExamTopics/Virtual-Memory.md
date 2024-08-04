Code needs to be in memory to be executed. But we rarely use all of the code. Actually there is a lot of code that only gets used in very specific cases. So why should we waste memory on that. Also we can not run all the code at once. We are probably just using a small amount of it.

For this to become true we have something called virtual memory. The good thing with virtual memory is that our address space can be much larger than the physical address space. So now a process can exist in its virtual address space. We can even have our program in contiuous address space because it is in virtual memory. The MMU has to handle the mapping of our virtual addresses to physical page frames in memory. 

Due to virtual memory it is quite easy for processes to share resources. This is done throug page sharing. We can "simulate" that the C library for example is in each process virtual memory. But in reality the actual pages are only one place in the physical memory

**Demand Paging** 
As the name implies demand paging does not load all of the program into physical memory, because we probalby dont need it. We load all of the process pages into virtual memory and only load pages into physical memory if we need them. The other parts stay in secondary memory. This way if there are pages we never access they will never be in physical memory.

To keep track of everything we need a way to distinguish between pages that are in physical memory and those that are not. For this we can use a valid invalid bit scheme. If the bit is set to valid the page is legal and in memory. If the bit is invalid the page is either not in memory or not valid. 

If a process tries to acces a page that was not brought into memory, so access a page marked invalid, we get a page fault. So we need to load the page into physical memory
- We start by checking if the page actually exists or if its an invalid memory access.
- If the reference is valid we but not yet brought in we page it in. If it is invalid we terminate the process
- We find a free frame for the page
- We schedule a secondary storage operation to read the page into the frame
- When the page is read in we update the page table and the internal table of the process that the page now is in memory
- We restart the instruction that was interrupted by the page fault.
-  ![[Screenshot 2024-06-18 at 19.18.15.png]]
- **Free-Frame List**
	- Most operating systems maintain a free frame list to satisfy pagefaults. For security reasons the memory of the pages is zeroed so no old data is availabel

Copy in write
- The idea is that we do not need to copy the memory pages of the parent process for the child process until a process changes the page. Then we need to copy it

Page replacement
- If we encounter a page fault we have some options.
	- we find the page and load it into memory if there is a free frame
	- If there is no free frame we use page replacement. Where we find a victim frame that is written to disk and the desired page is written to the free frame.
- to do this effectively we need an algorithm that can choose the right page to replace
	- FIFO
		- As new pages ar brought in they are appended to the end of a queue and when a page has to be replaced the first page in the queue gets replaced
![[Screenshot 2024-06-18 at 21.00.35.png]]
- As we can se when the pages are fulle the first page to be replaced is the one that came in first so number seven
- With FIFO suffers from Beladys anomaly: This says that for some page replacement algorithms the page fault rate may increase as the number of allocated frams increases.

Optimal page replacement algorithm
- the optimal algorithm is ofcurse the one with the least pagefaults. But to implement the one that achives this consistantly requires knowledge about the future. which makes it realy hard to implement

LRU Page replacement
- As the name suggest we replace the page that has ben the least recently used.
![[Screenshot 2024-06-18 at 21.06.27.png]]
- As we can see because 0 gets used quite often it is swapped out much later than in the FIFO example
- LRU needs some more implementation to work right. Every page entry would need a counter. Every time a page is used we copy the time into the counter and when we need to replace a page we look at the smallest counter


Allocation of frames
- Each process needs a minimum number of frames
- The maximum number of frames that can be allocated is of course the number of frames in the system
- There are to major allocation schemes
	- Fixed allocation
		- Fixed allocation is for example that we divide the number of frames equally between the processes 100 frames and 5 processes gives 20 frames for each
		- **Proportional allocation** We can also use the size of the process to decide how many pages the process should get
		- Also a good idea to keep some as a buffer
	- priority allocation
		- uses a proportional allocation sceem but instead of size of the process we use the priority of the process
	- We can also choose between global and local allocation.
		- When using global we can take a page from everywhere
		- When using local a process can only take one from within its process

Thrashing
- Thrashing occures when a process does not have enough pages and there are many page faults. We get low cpu utilization because we need to replace pages the whole time. So thrashing is when a process is busy swapping pages in and out instead of doing something useful

Allocating kernel memory
- Kernel memory is always allocate in power of 2 size. So if the kernel requests memory its if necesary rounded up to the nearest power of 2
- The buddy system
	- If we have chunk of memory that is to big we split it into to equal parts until we get the desired size
	- For example the kernel requests 21KB of memory. We round up to 32 to get the block size we want. Lets say we have a 256KB block availible. This gets split into two 128KB blocks, one of those gets split to two 64KB blocks and one of those into two 32KB blocks, one of those is now used.![[Screenshot 2024-06-18 at 21.36.18.png]]
	- Another strategy is SLAB alocation