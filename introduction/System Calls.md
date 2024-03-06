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
}
```
## File management
 TODO...