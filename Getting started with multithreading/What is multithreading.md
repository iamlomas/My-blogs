### What is multithreading?

Multithreading is a CPU feature which allows creation and execution of multiple threads within a process concurrently or
parallelly or both.

During development, the programmer divides the processes into threads i.e. **separate units of semi-independent
instructions extracted from the process.** These threads are managed by the application.

With multithreading more than one user *(here user can also be another program)* can use a program at a time or even
multiple requests by the same user can be managed by the program without having to run multiple copies of it in the
computer.

Each user request for a program or system service is kept track of as *a thread with a separate identity.* There are
some unique data incorporated in each thread that helps to identify them, such as:

- **Program counter:** A program counter is responsible for keeping track of instructions and to tell which instruction
  to execute next.

- **Register:** System registers are there to keep track of the current working variable of a thread.

- **Stack:** It contains the history of thread execution.

As programs work on behalf of the initial request for that thread and are interrupted by other requests, the status of
work on behalf of that thread is kept track of until the work is completed.

In multithreading, threads share the resources of a single or multi-cores. Depending on the hardware, threads can run
fully parallel if they are distributed to their own CPU core.

The execution in this is both concurrent and parallel:

- **Concurrent Execution:** If the processor can switch execution resources between threads in a multithreaded process
  on a single processor, it is a concurrent execution.

- **Parallel Execution:** When each thread in the process can run on a separate processor at the same time in the same
  multithreaded process, then it is said to be a parallel execution.

Examples of threads are several background/front end tasks such as updating data in the file system, capturing the log
files, multiple windows operations management, file scanning, continuous interaction with users.

### • Advantages of multithreading:

The main reason for incorporating threads into an application is to improve its performance. It is usually used for its
essential characteristics like it uses the system resources efficiently, high performance, greatly responsive, and also
its parallel execution ability.

Threading can be useful in a single-processor system because it allows the primary execution thread to be responsive to
user input while supporting threads execute long-running tasks in the background that do not require user intervention.

Application responsiveness is improved as requests from one thread do not block requests from other threads.

Additionally, multithreading is less resource-intensive than running multiple processes at the same time. There is much
more overhead, time consumption, and management involved in creating processes as compared to creating and managing
threads.

Regards, Lomas Singh

***Image credits***

<a href='https://www.freepik.com/vectors/people'>Cover image by freepik - www.freepik.com </a>