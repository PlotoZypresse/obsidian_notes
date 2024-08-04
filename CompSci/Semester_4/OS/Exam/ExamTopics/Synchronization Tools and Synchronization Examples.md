- Background
- Critical section Problem
- Petersons Solution
- Hardware support for synchronization
- Mutex lock
- Semaphores
- Monitors
- Liveness
- Problems of synchronization
- Synchronization within the kernel
- POSIX Synchronization
- Synchronization in java
- Alternative approaches
- Consumer porodcer
- Raceconditions
- Atomic variable
- Deadlocks

Because the CPU scheduler switches between processes to provide concurrent execution it could happen that a process only partly executes. For example if we increment a  counter but the scheduler switches before we get to increment it and the operation after that decrements the counter before returning to our previus iteration we maybe have counter =5 insted of = 6 

Race conditions
- a race condition is where several processes access and manipulate shared data and where the outcome of the executen depends on the order of which the processes take place. To solve this we need syncronisation

Critical section Problem
- the critical section in a process is the place where the code updates data that is shared with atleast one other process. This could leed to problems as mentioned before. There for when a process is in its critical section no other process is allowed to access the data the original process is accessing to prevent data being wrong. The critical section problem is to design a protocol that processes  can use to syncronize their activity. Each process must request acces to the critical section
- A solution must satisfy these requiremnts
	- Mutual exclusion: if process $P_i$ is executing in its critical section thn no other process can be executing in their critical section
	- Progress: If no process is executing in its critical section and a process wants to enter its critical section. Then only the processes that are not executing in their remainder section can decide which process can enter its critical section and a decision cna not be postponed indefenitly
		- In other words, processes that are in the entry or exit sections (but not currently in their remainder sections) can help in the selection process.
	- Bounded waiting: The "Bounded Waiting" principle states that there must be a limit on how many times other processes are allowed to enter their critical sections after a particular process has made a request to enter its critical section and before that request is granted.



Hardware Support
- Atomic 
	- this means that for example an Atomic variable can not be interrupted when being incremented
- test and set
	- 

Mutex Locks
- Mutex stands for mutual exclusion. Mutex locks are software tools to protect the critical section and prevent race conditions. A process must aquire a mutex lock before entering its critical section. The lock is then released when the process exits its critical section. A mutex lock as a boolean value to indicate if it is available. A process that tries to aquire the lock even though its not availible is blocked until the lock is released
- The main disadvanteges is that they require busy waiting. While a process is in its critical section another process must loop continuesly in the acquire call.  Busy waiting can be avoided
- This type of mutex lock is called a spinlock as it spins while waiting for the lock to become availible
- The advantage of a spin lock is that they dont require context switches. So when the wait time is low it is much faster to wait and avoid the context switches
Semaphores
- A semaphore is an integer variable that apart from initilization is only accessed throug two atomic operations wait() and signal() wait decreses the value of the semaphore and signal increases it. For this to work the increment and decrement must of course be executed atomicaly
- Often there are two types of semaphores: counting and binary semaphores. As the name suggest a countiong semaphore can have range over a unresticed domain, where as a binary semaphore can only have values of 0 and 1
- Counting semaphores can be used if there are a number of processes that can have access, where as binary semaphores are used when only one process should have access
- To avoid busy waiting we suspend the process if the wait operations finds that the semaphore is not positive. The suspend operation places the process in a waiting queue and the process is switched to the waiting state. When the semaphore is ready the process is awaken and put into the ready queue for the cpu to process it. When that happens depends on the cpu scheduling algorithm
Monitores
- Because varius types of error can be generated when programmers use semaphores or mutex locks incorrectyly to solve the critical section problem. We introduce the monitor type, which incorperates simple synchronization tools as high level constructs
- A monitor is an Abstract data type which encapsulates data with a set of funtions to opreate on thet data. A monitor type is a set of programmer defined operations that are provided with mutual exclusion within the monitor
- Because of this the programmer does not need to program syncronization explicitly
- A monitor is a high-level synchronization construct that provides a convenient and safe way to manage access to shared resources in concurrent programming. It encapsulates the shared variables, the operations that manipulate them, and the synchronization between concurrent processes.
Liveness
- Liveness refers to a set of properties that a system must satisfy to ensure that processes make progress during their execution life cycle. A process waiting indefinitely under the circumstances just described is an example of a "liveness failure. "
- A situation that can lead to a liveness failure is a deadlock. A deadlock is a situation where two processes are waiting indefnitly for an event that can be caused only by one of the waiting processes. An example of a deadlock is the dining philosophers problem


Classic Problems
- Dinning philosopher problem