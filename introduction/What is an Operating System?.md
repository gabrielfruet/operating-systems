- Provide application programmers a abstract set of resources instead of the messy hardware ones and managing these hardware resources. 
- O.S job is to provide user programs with a better, simpler, cleaner, model of the computer and to handle managing all the computer resources that are "hard" to the user to handle.
- The *shell* is not part of the operating system itself.
## Computers modes of operation
![[where_the_operating_system_fits_in.png]]
- The O.S runs in **kernel mode** (A.K.A supervisor mode), to all the hardware and can execute any instruction the machine is capable of executing.
- The rest of the software is commonly run in **user mode**, in which only a
subset of the machine instructions is available
- An *user mode* **user** can change it's email reader, but cannot rewrite the kernel clock interrupt handler
## The Operating System as an Extended Machine
- The architecture of computers at the machine-level is primitive and awkward to program.
- An example is the *SATA* (Serial ATA) used in most computers, the manual is over 450 pages that can be abstracted with a simple piece of software called **disk driver**. Even though this level is still low enough for being hard to program.
- So most modern O.S provide an abstraction even higher, called *file*.
- One of the major tasks of the operating system is to hide the hardware and present programs with nice, clean, elegant, consistent, abstractions to work with instead. Operating systems turn the ugly into the beautiful
![[operating_systems_turn_ugly_hardware_into_beautiful_abstractions.png]]
- The **real** customer of an O.S is the application program.
- In contrast, end users deal with the abstractions provided by the user interface, either a command-line shell or a graphical interface
## The Operating System as a Resource Manager
- In the bottom-up view, operating system is responsible for providing orderly and controlled allocation of the processors, memories, and I/O devices among the various programs wanting them.
- Modern O.S allow multiple programs to be in memory and run at the same time.
- #### Problem: Imagine what would happen if three programs tried to print their output simultaneously on the same printer?
  The O.S solves this by buffering the outputs.
- Resource management includes ***multiplexing*** (sharing) resources in two different ways: in time and in space.
- The CPU can allocate itself for one program at a time.