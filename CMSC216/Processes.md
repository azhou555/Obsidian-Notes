## What is a Kernel?
If we want to get a deeper grasp of how computers work, we have to eventually look at the hardware. The **kernel** is a program that starts running when a computing system is turned on. It can be described as the central part/core of what makes computers work/able to do things. For example, a kernel may be responsible for setting up handlers for various exceptional control flows, dealing with hardware interrupts and system calls. 
## CPUs
Most CPUs generally have at least two modes:
1. User/Normal mode
2. Kernel/Privileged/Supervisor mode
Generally, what we do and the programs we make can only run in user mode meaning that it can't directly access/change hardware and certain resources->risk reduction. 
We need to request OS in order to perform certain operations, which makes the OS jump to kernel code that is run in kernel mode. 
## Processes
Hardware is only capable of executing streams of instructions. It is very good at that, but it cannot do much else(not really but sure). The OS is what creates the notion of a process, a set of instructions that comprise running a program. Processes can be turned on and off, they can be executed for some time and then paused while another process runs and then turned back on. 
#### Exceptional Control Flow
Anything that forces the CPU to change from the "regular" control flow. Can include interrupts, faults, aborts, traps, etc. Anything deviating from the norm. 

We will generally be looking at 4 main functions for processes:
1. `getppid()`/ `getppid()`
	1. Self explanatory + parent id
2. `fork()`
	1. Clones a process
3. `wait()` / `waitpid()
	1. Wait for another process to finish, can store a return value somewhere
4. `exec()` family, mainly `execvp()`
	1. Makes a process(current process) execute a command. 
Basic design example:
![[Basic Forking Layout.png]]
Note that `fork()` will return a `0` if the current process is the child process that resulted from the `fork()`. This will help to differentiate between what code the parent should run and what code the child should run. Note the usage of `getppid()` compared to `getpid()`. Notably, the difference between getting the **parent** process id(ppid) versus the process id(pid). 
In the above code, the parent process and child process are run in an unpredictable order. Essentially, the CPU can decide that either process will get higher priority and run first. In some cases, it will be the child and in other cases it might be the parent. 
![[Forking With Waiting.png]]
In this version, there is a `wait()` call in the parent process's code. The use of `wait()` rather than `waitpid()` means that the parent process will resume execution after any process is finished. Specifying a specific pid allows us to have even more control over the order with which processes are ran. Also note that we created an int status that stores the return value of whatever process the parent is waiting on. We also have specific macros to get more information about the execution of the function that we `wait()` on. Using the code above, we can add something like:
```
if(WIFEXITED(status)){
	int retval = WEXITSTATUS(status);
}
```
in order to figure out if there is a non-zero exit status or anything abnormal about what happened in the `fork()`. We can then check if `retval != 0` to sus out any non-zero returns. If we don't get our `WIFEXITED(status)`, it means that something happened to the forked process. 
Note that the return value for `wait()` and `waitpid()` is the PID of the child that finished. 
WNOHANG->asynchronous. Doesn't wait, but rather checks up on process. 

Note that whereas a `fork()` duplicates the original code aside from having a different return value, running an `exec()` completely replaces the entire memory image of process. It begins a completely new main function that takes over the original **Text** of the function, and does not return to the original code. Thus, any and all code after a successful `exec()` call is unreachable. 
