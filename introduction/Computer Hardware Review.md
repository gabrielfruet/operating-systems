- An operating system is intimately tied to the hardware of the computer it runs
on
- Conceptually, a simple personal computer can be abstracted to a model resem-
bling that of Fig. 1-6.
![[some_of_the_componentes_of_a_simple_personal_computer.png]]
## Processors
- The "**brain**" of the computer.
- Fetcher instructions from memory and execute them.
- The basic cycle of a CPU is: 
   1. Fetch
   2. Decode
   3. Execute
- Each CPU has an specific set of instructions it can execute.
- Accessing memory takes much longer than executing an instruction, all CPU contains registers to hold temporary variables and temporary results.
- One of these is the **program counter**, which contains the memory address of the next instruction to be fetched
- Another one is the **stack pointer**, which points tot he top of the current stack in memory. (the stack contains one frame for each procedure that has been entered but no exited).
- Yet another is **PSW** (Program Status Word). It contains the condition code bits, which are set by comparison instructions.
- Many modern CPU's have facilities for executing more than one instruction at the same time.
- For example, a CPU might have separate fetch, decode, and execute units, so that while it is executing instruction n, it could also be decoding instruction n + 1 and fetching instruction n + 2.
- The above is called a **pipeline**.
- Usually a bit on the **PSW** controls whether it's using *kernel* mode or *user* mode.
- To obtain services from the operating system, a user program must make a **system call**
## Memory
- The second major component in any computer is the memory.
- Ideally, a memory should be extremely **fast**, abundantly large, and dirt cheap, but this goal is not achieved right now.
![[memory_hierarchy.png]]
- The registers consist of the *internal* CPU memory, that is made of the same material of the CPU, so it's as fast as the CPU.
- The cache, which is mostly controlled by the hardware, are divided in **cache lines**.
- The most heavily used cache lines are kept in a high-speed cache located inside or very close to the CPU.
- The cache is consulted before the memory is consulted.
- Some machines have two or even three levels of cache, each one slower
and bigger than the one before it.
- With cache, some questions rise:
   1. When to put a new item into the cache.
   2. Which cache line to put the new item in.
   3. Which item to remove from the cache when a slot is needed.
   4. Where to put a newly evicted item in the larger memory.
- Caches are such a good idea that modern CPU's have two of them. **L1** and **L2**.
- **L1** is always inside the CPU, and usually is used to *decode* instructions.
- **L2** holds several MB of recently used memory words.
- L1 acess is done without any delay, while L2 has one or two clock delay.
- **Main memory** is usually called **RAM** (Random Acess Memory).
- Many computers have a small amount of non-volatile RAM, the **ROM** (Read Only Memory), that is fast and inexpensive.
- **ROM** does not lose content when the power is off, unlike **RAM**.
## Disks
![[structure_of_a_disk.png]]
- The next on the hierarchy is the hard disk. 
- Disk is two orders of magnitude cheaper than RAM per bit
- A disk consists of one or more metal platters that rotate at 5400, 7200, 10,800
RPM or more.
- SSDs do not have moving parts, do not contain
platters in the shape of disks, and store data in (Flash) memory.
- **Virtual Memory** make it possible to run programs larger than the main memory using the disk drive as a secondary memory.
- The mapping is done by the part of the CPU called **MMU** (Memory Management Unit).
## I/O Devices
## Buses
## Booting the Computer
- Every PC has a motherboard.
- The MB has a program called **BIOS** (Basic Input Output System). Held commonly by flash RAM.
- It contains low level I/O software. 
- At boot, the BIOS is started. It checks the RAM installed, then the keyboard, mouse and etc. It scans the PCIe and PCI buses to detect devices. 
- The BIOS then determines the boot device by trying a list of devices stored in the CMOS memory.
- Typically, an attempt is made to boot from a CD-ROM (or sometimes USB) drive, if one is present.
- If that fails, the system boots from the hard disk.
- The first sector from the boot device is read into memory and executed.
- This sector contains a program that normally examines the partition table at the
end of the boot sector to determine which partition is active.




