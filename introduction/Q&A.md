1. **What are the two main functions of an operating system?**
- Manage computer resources and provide a cleaner abstraction for the user.
3. **What is the difference between timesharing and multiprogramming systems?**
- Timesharing is a logical extension of multiprogramming where the process session is defined by it's run time.
- Multiprogramming is the ability of a O.S to execute multiple processes.
4. **To use cache memory, main memory is divided into cache lines, typically 32 or 64
bytes long. An entire cache line is cached at once. What is the advantage of caching an
entire line instead of a single byte or word at a time?**
- It's faster and will probably get useful information that is close to the request byte word.
5.  **On early computers, every byte of data read or written was handled by the CPU (i.e.,
there was no DMA). What implications does this have for multiprogramming?**
- The CPU will have to spend more time copying memory than executing instructions, cause a memory copy is slower than a instruction execution. 
6. **Instructions related to accessing I/O devices are typically privileged instructions, that
is, they can be executed in kernel mode but not in user mode. Give a reason why these
instructions are privileged.**
- Because they deal with the very low level of the hardware, and giving this power to the user will mostly run into protection issues.
10. **What is the difference between kernel and user mode? Explain how having two distinct modes aids in designing an operating system.**
- User mode can only do the things that the O.S permits, kernel mode is unlimited, so it has access and can do everything. Two modes exists for preventing the user to breaking the machine.
12. **Which of the following instructions should be allowed only in kernel mode?**
- a) Disable all interrupts
- b) Read the time-of-day clock
- c) Set the time-of-day clock
- d) Change the memory map
- Ans: A.
