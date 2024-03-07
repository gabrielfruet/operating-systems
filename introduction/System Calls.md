We are thus forced to make a choice between (1) vague generalities (‘‘operat-
ing systems have system calls for reading files’’) and (2) some specific system
(‘‘UNIX has a read system call with three parameters: one to specify the file, one
to tell where the data are to be put, and one to tell how many bytes to read’’).

```c
count = read(fd, buffer, ndbytes)
```

We have chosen the latter approach. It’s more work that way, but it gives more
insight into what operating systems really do. Although this discussion specifically
refers to POSIX (International Standard 9945-1), hence also to UNIX, System V,
BSD, Linux, MINIX 3, and so on, most other modern operating systems have sys-
tem calls that perform the same functions, even if the details differ.
## System Calls for Process Management
- ***Fork*** is a good place to start the discussion.
  ### *Fork*
  - The only way to create a new process in POSIX
  - It creates an exact copy of the original process. 
  - the `fork(...)` call returns a value, which is: 0 for the child or child's PID for the parent, that is equal to 
  - Using the returned PID, the two processes can see which one is theparent process and which one is the child process.
  - **Shell case**: It reads a command from the terminal, forks off a child process, waits for the child to execute the command, and then reads the next command when the child terminates.  
  - For waiting the child to finish it call `waitpid(...)` syscall, which waits until the child terminates.
  ```c
	#define TRUE 1

	while (TRUE) {
		type prompt( );
		read command(command, parameters);
		if (fork( ) != 0) {
			waitpid(−1, &status, 0); // parent
		} else { 
			execve(command, parameters, 0); // child
		}
	}```
## File management
- For **reading** or **writing** a file it must be opened.
- When opened if need to be specified if its being opened for **read only**, **write only** or **read and write**.
- The file descriptor returned can be used for a future open after closing.
- `lseek(...)` changes the file pointer position.
- `stat(...)` syscall can be used for getting the status of a file. Last modification, size, mode and etc.
## System Calls for Directory Management
- `mkdir(...)` create a directory.
- `rmdir(...)` remove an empty directory.
- `link(...)` purpose is to allow the same file to appear under two or more names, often in different directories. **Not a copy**.
- Link is related to dynamic linking.
- For creating a link, the O.S basically copies the file identifier and paste it on the directory, thus leading it to the original file.
- `mount(...)` allows two file systems to be merged into one.
- Suppose we are mounting a USB file system to our root system. In C, it would look like this:

```c
mount("/dev/sdb0", "/mnt", 0);
```

- How the root file system would look like after the mount:

 ![[mount_call_example.png]]
## Miscellaneous System Calls

A variety of other system calls exist as well. We will look at just three of them
here.

1. `chdir("/usr/ast/test");` changes the current working directory.
2. `chmod("file", 0644);` changes the file protections code.
3. `kill(...)` is the user's way of sending signal.