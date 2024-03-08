We will examine six different structures that have been tried, in order to get
some idea of the spectrum of possibilities.

## Monolithic Systems
- The **most** common organization by far.
- Entire O.S runs as a single program in kernel mode.
- The O.S is basically a set of procedures linked into a single executable.
- Every procedure can call any other one. This approach is very efficient, but having thousands of procedures that can call each other without restriction may also lead to a system that is unwieldy and difficult to understand.
- For constructing the actual program it:
  1. Compiles all the individual procedures.
  2. Binds them all into a single executable.
- **Every** procedure is visible to the others
- Though the procedures are free to call each other, there is some structure in it.
- **Services** (*syscalls*) provided by the O.S are requested by putting the parameters in a well-defined place (e.g.,  on the stack) and then executing a trap instruction. The trap instruction switches from *user* mode to *kernel* mode. The O.S then fetches the parameters and determines which syscall is to be carried out. After that it indexes into a table that contains in slot *k* a pointer to the procedure that carries out system call *k*.
- The structure look like this:
  1. A program that invokes the request service procedure.
  2. A set of service procedures that carry out the system calls.
  3. A set of utility procedures that help the services procedures.
- Every system call has a service procedure that takes care of it and execute it.
- Other than the core O.S, it loads drivers and file systems. These are loaded on demand, in UNIX are called **shared libraries**, in Windows are called **DLLs** (Dynamic-Link Libraries).
![[monolithic_system.png]]
## Layered Systems
- A generalization of a Monolithic System is to organize it as a **hierarchy of layers**. Each one constructed upon the one below it.
 ![[the_os.png]]
 - This is **THE** operating system(this is the name of it). Made by Dijkstra and his students.
 - The layers are described as:
   0. Allocation of the processor, switching between process when interrupted.
   1. Memory management
   2. Communication between process and the operator console.
   3. I/O management and stream buffering.
   4. User programs.
   5. The system operator.
- Above every layer, a new set of abstraction is defined, such that the one above layer *i* don't need to worry about layer *i* internals.
## Microkernels


   