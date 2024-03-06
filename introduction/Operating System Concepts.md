## Processes
- A key concept in all operating systems is the **process**.
- A process is basically a program in execution. 
- Each *process* has an **address space**, the memory part that the process can read an write.
- The address space contains the **executable program**, the **program’s data**, and its **stack**.
- A process is fundamentally a container that holds all the information needed to run a program.
- When a process is suspended temporarily, it must later be restarted in
exactly the same state it had when it was stopped.
- The information about each process, other than the contents of its own address space, is stored in an operating system table called the **process table**, which is an array of structures, one for each process currently in existence.
- A *suspended* process consists of its address space, usually called the **core image**, and its process table entry.
- If a process can create one or more other processes (referred to as **child processes**)![[process_tree.png]]
- **ICP** (Inteprocess Communication): Related processes that are cooperating to get some job done often need to communicate with one another and synchronize their activities.
- When the specified number of seconds has elapsed, the operating system sends an **alarm signal** to the process.
- Each person authorized to use a system is assigned a **UID (User IDentification)**
- A child process has the same UID as its parent. Users can be members of groups, each of which has a **GID (Group IDentification)**.
## Addres Space
- In a very simple operating system, only one program at a time is in memory. To run a second program, the first one has to be removed and the second one placed in memory.
## Files
- It abstracts the I/O devices read an write operations.
- **Directory** is a way of grouping files.
- Every file has a path name, that is the path from the root to the file itself.
- Every process has a **current working directory**
- Shell working directory can be seen with the following command:
	$ pwd
	/usr/bin/
- To be read or written, it must be opened. To access it the system uses a **file descriptor**(integer) to provide access to the opened file, if permited.
- UNIX uses a concept called mounted file system. 
- `mount(...)` system call is used to  mount a removable drive to the root file system
- **Special file** is provided to make I/O to look like files.
 - **Pipe** is a way of two process to communicate through a pseudo-file.
## Input/Output
- Many kinds of input and output devices exist, including keyboards, monitors, printers, and so on. It is up to the operating system to manage these devices.
## Protection
- Files in UNIX are protected by assigning each one a 9-bit binary protection code.
- In addition to file protection, there are many other security issues. Protecting the system from unwanted intruders, both human and nonhuman (e.g., viruses) is one of them.
## Shell
- Command interpreters definitely are not part of the operating system.
- Although is not part of the O.S, it is the main interface between the user and the O.S.
- **<, >** -> Redirect standard input/output
- **|** -> Pipe to another process
- **&** -> Make processes run in the background


