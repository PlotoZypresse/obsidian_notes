Why virtual machines
- Running a virtual machine gives the posibility of running multiple OS's on a single machine. Depending on the setup of the VM the VM will think it is running on a real computer and it does not know about the computer its running on.
Benefits and features
- Depending on the usecases VM can be very usefull. FOr example for researching how maleware behaves on a system. Because the VM is its own locked system the host system will not get infected with the maleware. Also we can freeze or suspend a VM at any given point. We could then for example copy the state of the machine or even move it. We can also take a snapshot of the machine. This can be usefull when researching maleware as we can take a snapshot of a clean machine. After we looked at the maleware we can return to that snapshot of a clean machine. This way we do not need to reinstall everything. We could also clone a machine and thus have two identical ones
- It is also possible to move a VM from one host to another
- Cloud computing runs on VMs. A company can provide the costumer with a VM and the costumer can do anything on it without affection the system its running on

Building blocks
- Most VM implement a virtual CPU or VCPU to represent the state of the CPU. Because it isnt a good idea to have the VM run in the hostsystems kernel mode the VM has virtual kernel and virtual guest mode. Both of those run in usermode on the host. A switch to kernel mode thus has to switch to virtual kernel code. 
- This is done just like normal by trying to switch to kernel mode, but this causes an error. The VMM takes over and executes the desired things before giving control back to host system
- User code runs just as fast as on a normal system but kernel code is slower due to the thing above
- The VMM maintains a nested page table for each Guest 

CPU Scheduling
- even a single cpu system acts like a multiprocessor system when virtualized
- Every guest has one or more virtual CPU. How many VCPUS can be configured
- The guest can be dedicate CPUS if there are enough
- VMM can use normal scheduling algorithms
- Because we demand more form the CPU than it can actually deliver the guest system will have worse performance

Memory Managment
- Here we also demand more from physical memory thant there actually is. This then requires extra managment from the CPU
- For example double paging. Here the guest system thinks a page is in memory when it actually is in backing store
- 

Types of VMS
- Type 0 hypervisor
	- We partiotion the hardware into multiple idenpendet machines that can not interact with each other. If every machine needs an ethernet port for example we need a physical ethernet port for each machine
- Type 1 hypervisor
	- Type 1 hypervisors ar most often found in data centers. They are a special purpose operating system that runs nativley on the hardware. But instead of providing system calls and other things for programms they create, run and manage guest OS's
- Type 2 hypervisor
	- A type to hypervisor is what most people will know as the VMM is simply a program running on the guest OS. They tend to have the worst perfromance. But they are still usefull as they run on basically everything
- Programming environment virtualition
	- Here a programming language is build to run in a custom build virtualized environment. Java is such a programming language. The java code is run in the JVM environment and the JVM is running as a native program. This means that the same java code can run on any machine that has a JVm
- Emulation
	- Emulation is when we imitate another system completely. This is for example used heavylie for old game consols. Here a program emulates the old gameconsols hardware and software to run oldgames on a newer machine. As emulation is not very efficient it is only feasable to do with older hardware

Live migration
- A running VM can be moved between systems. This is called live migration. This is especially usefull for cloud computing. When the physical machine needs to turn of or stop running the VM we can move it to another machine and the costumer will not expirience any downtime
- The VMM start by establishing a connection with the target VMM
- We create a new VCPU and so on just like on the home system
- We send all read only memory pages to the target
- We send all read write pages to the target
- We repeat the priviuos step as in the process the pages where probably altered
- When the cycles of the 2 previous steps become very short the VMM freezes and the final state of the VCPU memory pages and so on get send to the new VMM