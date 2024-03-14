![[Screenshot 2024-02-29 at 16.08.35.png]]
- Many computers have interrupt driven timing where the systemclock is updated by interrupts. When interrupts are disabled the system could lose track of time

![[Screenshot 2024-02-29 at 16.08.49.png]]
- busy waiting is that when a process tries to enter its critical section but another process already is in theirs. They will loop continuisly because of the implementation of acquire() function. We can avoid busy waiting by putting the process to sleep and waking it once it can access its criticalsection.
- Types of waiting: sleeping

![[Screenshot 2024-02-29 at 16.09.05.png]]
- Spin locks are usefull on multiprocessor system because they can "spin" a process. THis means that there is no need for context switches when the lock becomes available. On mutlicore systems the if the spinlock is only held for a short amount of time a core can keep the thread spinning while another thread. carries out the critical section on another core.
- as older systems only have one core this is obviusly a problem

![[Screenshot 2024-02-29 at 16.09.18.png]]
- wait and siganl increase or decrease the semaphore value so if there not executed atomically it could end with a race condition
- wait checks if the semaphore is 0 ain this process another process can come in and do things

![[Screenshot 2024-02-29 at 16.09.28.png]]
- 

![[Screenshot 2024-02-29 at 16.09.42.png]]
- both withdraw and deposit update the account balance so if both processes acces the account balance at the same time both processes get the start amount and operate on that ending with both function returning two different values.
- Preventing a race condition could be done by blocking access to the account balance while a process operates on it and then releasing it again after its doen

![[Screenshot 2024-02-29 at 16.09.59.png]]
- if we want to push and pop at the same time we need to get the top item of the stack resulting in a race condition
- this could be solved by not allowing push and pop to be executed at the same time

![[Screenshot 2024-02-29 at 16.10.16.png]]
- because no core acceses the same index at the same time there would not be any race conditions
- as we can not guarantee of the order of execution we can not say 100% that it would give the right result

![[Screenshot 2024-02-29 at 16.10.32.png]]
- yes we check twice to see if we got context switched

![[Screenshot 2024-02-29 at 16.10.47.png]]
- 

![[Screenshot 2024-02-29 at 16.10.57.png]]
- 

![[Screenshot 2024-02-29 at 16.11.15.png]]
a) spinlock a short block of a few recourses is not that bad
b) mutexlock because else resources would be blocked for a long time
c)

![[Screenshot 2024-02-29 at 16.11.30.png]]
- an atomic intiger is easier to increment but may cause more error potential

![[Screenshot 2024-02-29 at 16.11.43.png]]
We can increase the counting semaphore value up to n for each connection and decrease it when a connection is terminated

![[Screenshot 2024-02-29 at 16.11.53.png]]


![[Screenshot 2024-02-29 at 16.12.05.png]]
- if all the philosophors pick up their chopsticks and all of them wait for another to place theirs on the table agian

![[Screenshot 2024-02-29 at 16.12.15.png]]
- its in place to not do busy looping so the processor can do other things. 