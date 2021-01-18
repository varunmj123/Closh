
Design Choice:

-Sequential Execution:
Firstly, we created an array of pids of size count. We then determined whether the program is going to run in parallel or sequentially, within an if-else statement. After establishing the nature of the process, in the sequential execution code block, we began by creating a for-loop that iterates over count. Then within the for-loop, we created an if-statement that forks a new child process and equates the forked process to zero. If that is true, which it should be, then it is a child process. The process is then executed by calling execvp, and the timeout is then implemented (please refer to the timeout section below Parallel Execution), the program then waits (using waitpid) for the child process that was forked to terminate. The for-loop then iterates again with an increment of i until i is equal to count. In summary, sequential execution creates a process and waits for it to terminate before creating a new process.


-Parallel Execution:
If the program is not running sequentially, that means it runs in parallel. We started by using a for-loop to iterate over count, then fork a count number of child processes, and begin their execution (by calling execvp). After doing so, we exit the loop and begin another for-loop, which we then wait for the child processes to terminate. In summary, Parallel execution creates and starts the execution of all the child processes and only after doing does it start calling waitpid() on them.