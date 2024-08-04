What is a deadlock
- Dining philosophers problem
- A deadlock occuress if two process try to require each others mutex locks at the same time. Process one aquires lock one and then lock 2 and process 2 aquires lock 2 and then lock one. They now sit in an infinite loop where process 1 is trying to get lock 2 and process 2 is trying to get lock 1.
- A livelock is similar to a deadlock. as in both prevent two or more threads from proceeding. Where a deadlock occures when every thread in a set is waiting for an event that can be caused only by another waiting thread. A livelock occures when a thread continuously attempts an action and fails. Its similar to two people trying to pass each other in a hallway and always move in the same direction to move around each other. They are not blocked but also are not making any progress. A livelock can be avoided quite easy by retrying the operation in random time intervals for example.

What do we need for a deadlock
- For a deadlock to arise we need these for conditions to hold simultaneously
	- Mutual exclusion: 
		- Atleast one resource must be hold in a nonsharable mode. If a thread requests that resource it must wait until the resource has been released
	- Hold and wait:
		- A thread must be holding atleast one reasource and waiting to aquire additional ones that are currently hold by other threads
	- No preemption:
		- A resource can only be realeased by a thread after the thread is done with it
	- Circular wait:
		- A set of threads ${T_0,T_1,....,T_n}$ must exist where $T_0$ is waiting for a resource of $T_1$ and $T_1$ is waiting for a reasource from $T_2$ and so on
Deadlocks can be described Using Resource allocation graphs
- ![[Screenshot 2024-06-18 at 11.03.19.png]]
- A directed edge from a resource to a thread means the thread has aquired the resource. A directed edge from a thread to a resource means 
- If a graph has a cycle there can be a deadlock but its not always the case. If there is no cycle there is no deadlock

How to handle deadlocks
- The easiest way is to just ignore them and pretend they dont occure in the system. This is the methode used by most OS.
- We can use a protocol to prevent or avoid deadlocks, ensuring the system will never enter a deadlocked state.
	- This is done by providing methodes to ensure that one of the necesary conditions for deadlocks can not hold
		- The hold and wait condition can be prevented by only to execute a thread that has all its resources. THis is ofcurse not very practical. Another way is that a thread can only request resources if it has none. Both these methodes are not opotimal because of low resurce utilization and processes may starve
	- We can also introduce preemption.
		- This happens when a thread requests resources but there are some that are not accesible because another thread is using them. Then the thread preemptively releases all its resources again
	- we can avoid circular wait by imposing a total ordering of all resource types and require that each process only requests them in an increasing order of enumeration
	- **Deadlock avoidance**
		- THe general idea is to prevent deadlocks from happening, by preventing one of the 4 conditions. 
		- For this to work we need more information about each process. this tends to lead to low device utilization
		- When schduler sees a deadlock its not executed
		- **Safe state**
			- When all reasource can be allocated without problems
		- Using graphs we can avoid deadlocks by avoiding loops in the resource allocation graph
- We can let the system enter a deadlocked state, detect it and recover. This is often used by databases

Deadlock detection
- Performance hit if we constantly check for deadlocks
- Wait graph. Again when we detect cycles there can be deadlocks

Recovery
- Terminate all processes involved with the deadlock
- terminate processes one by one. Is more conservative but we need to check for deadlocks after every step
	- We can use some factors to decide wich processes to terminate
		- Priority
		- Runtime
		- resources the process holds
		- Interactive or batch