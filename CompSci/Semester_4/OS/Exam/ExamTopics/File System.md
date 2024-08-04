File Concept
- Files have different attributes that can vary from OS to OS but often there are some basic ones. The file control block or in unix Inode holds this information
	- Name: For some filesystems the name is very important for others not. Often the the file extension is importatn. It shows what type of file it is. Is it an executable, an image a text file and so on
	- Identifier: a unique tag. In Linux its the inode number
	- Type: what type of file. So again exe, txt and more
	- Location: A pointer to a device and the location of the file on that device
	- Size: the current size of the file
	- Protection: Access control to determine who can read write execute and so on
	- TImestamps and user identification: For example creation time, last acces, last modification or last use time.

File Operation
- Creating a file: We need to find space for the file and a new entry must be made in a directory
- Opening a file: Opens a file
- Writing a file: We make a system call to open and write the desired into to the file. If the write is sequential the system must keep a write pointer to the location in the file where the next write is to take place.
- Reading a file: We again open the file and the system needs to keep a read pointer where the next read should take place. For efficency mos OS use just one pointer for read and write called current file position pointer
- Repositioning within a file: As we only have one pointer we need to be able to move it around
- Deleting a file: We search for the file. When found we release all of the file space so it can be used again
- Truncate: Edeting the contents of the file so we dont need to delete the file and create a new one

Open file table
- So we dont need to search after a file everytime we want to do something with it many operations require us to open the file. The OS then keeps all open files in an open filetable. We can than simply reference the file there instead of searching for it again and agian
- The open file table typicaly also has an open count to keep count of how many processes have opended the file

An open file has severel pices of information that are associated with it
- File pointer: FOr reading and writing
- File open count: to keep track of how many processes have opend the gile
- Location of the file: So we can read and write to it
- Access rights: So we know who can do what with the file

File Strucure and types
- We ahve differnt file types that indicate what funciton the file has. These file types often also have different internal structures so the OS knows how to use them. An executable file will need a specific structure so the OS knows how to execute the code in it correctly

File Access methodes
- We need to access the information stored in the file somehow. THis can be done in several ways. ANd man OS support different ways. Choosing which to use is not always easy
- Two of the simplest methodes are:
	- Sequential Access
		- This is the simplest one: The information of the file is processed in order one after the otehr. When reading the readpointer just moves along the file. The write pointer just appends to the end of the file. The pointer can be reset to the beginging and in some OS there can be skips with a defined length. Its kinda like an old tape
	- Direct Access
		- Here the file is made up of fixed length records. This allows us to jump to a desired record and read or write it

Directories
The directory holds and orders the differnet files on the system. The directory itself can be implemented in different ways but it must allow some basic functions. For a directory to work it  needs to provide the following function to be able to be performed on a directory
- Searching for a file: We need to find a particular file in the directory structure
- We need to be able to create a file and add it to the directory
- We need to be able to delete a file
- List all the files in a directory
- Rename a file
- We need to acces every directory and file within the directory structure

- Directory Structure
	- Single level
		- All files are contained in the same directory. This can lead to confusion reagrding file names espacily of there are multiple users
		- ![[Screenshot 2024-06-19 at 12.53.29.png]]
	- Two level
		- In this approach each user gets its own directory that only lists the files of the user
		- ![[Screenshot 2024-06-19 at 13.12.00.png]]
	- Tree Strucuture
		- As the name implies this is a tree directory structure. The tree has a root directory and everfile has a unique path name. A directroy can hold a directroy and so on. Path names can be absolute so from the root to the file or directory or realtive which is from to current directory to the desired destination
	- Acyclic graph directories
		- A tree structured directory does not allow files to be shared. For this to be possible we can use an acyclic graph, that is a graph without cycles, As our structure. Now bot users can have their own directories but they can also share files or directories.
	- Graph directory
		- A problem with acyclic graph directories is ensuring that there are no cycles this is solved by using normal graphs where cycles are allowed. but this can lead to other problems for example could we get stuck in a loop when traversing the directories
Protection
- access types
- access  controll


Allocation methods
- How do we allocate space for the files so that we utilazie the storage space efectively
- Contiguous
	- Contiguous allocation stores files as contiguous blocks on the device. So if a file is 4 blocks long it occupies block b, b+1, b+2 and b+3. Contiguous allocation can just like memory allocation suffer from external fragmentation. And we kinda need to now the size beforehand![[Screenshot 2024-06-19 at 15.07.23.png]]
- Linked allocation
	- this is basically a linked list each block has a reference to the next block and the last has a null pointer. This method does not suffer from ext![[Screenshot 2024-06-19 at 15.07.15.png]]ernal fragmentation. and we do not need to know the file size beforehand
- FAT
	- This is a version of linked allocation where the links are stored in a separate table. At the begining of the disk. This table can be cached in memory which improves random access speeds![[Screenshot 2024-06-19 at 15.07.05.png]]
- Indexed allocation
	- Here we use an entire block to store all the used blocks. But this approach wastes diskspace as we use an entire block for it even if we just use it to index 2 blocks which is not optimal and the block would also not be large enough for big files
	- We can also use multilevel indexing where the first index block links to other index blocks which then point to file blocks or more index blocks. The number of index blocks can change depending on the desired maximum file size![[Screenshot 2024-06-19 at 15.06.53.png]]

Free space managment
- Bitmap
	- each block is represented by 1 bit and if the block is free the bit is 1 and if it is not its 0
	- ![[Screenshot 2024-06-19 at 15.06.44.png]]
- Linked list
	- Here we have a linked list of all the free blocks