# Java-Thread

## Thread & Process
## Thread
- Thread is used to decribe a process that load the command to CPU and manage the memory and io for running a porgram.
- When we start run a program, meaning start to load this program form disk to memory, we start a process.
- Most of the program can have can multiple thread runining at the same time.(open the same program)
- Thread is a unit of CPU utilization.

## Process
- One thread can have multiple process.
- One Process is one instruction stream, which means execute the instructions in instruction steam in order by CPU.
- In window, thread is not dynamic, is be like the container for process.  

## Concurrent

Thread takes turn use the cpu.
- ![image](https://user-images.githubusercontent.com/79159894/200863867-fd2b0a1b-81bd-4471-ae7f-9e32c60d5b6a.png)

## Parallel
- When cpu have multiple cores, every core can schedule the thread, so the schedule can be used in parallel.
- ![image](https://user-images.githubusercontent.com/79159894/200863722-bba33c2c-5a6f-4bd4-bb44-2fe795485b41.png)

## Common Function
| Method | static|Description|Notice|
| ------------- | ------------- |------------- |------------- |
| start()  | |start a new thread and run the code that in the run() | start() is used to let thread stand by, not immediately execute the code. Each start() can only be called one, if we use strart multiple time, it will appear IllegalThreadStateException. | 
| run() | |node.js, express.js |https://tranquil-citadel-69579.herokuapp.com/ |
| join()| |node.js, express.js|
| join(long n) ||node.js, express.js|


## Reference
- https://www.bilibili.com/video/BV16J411h7Rd/?p=6&spm_id_from=pageDriver




