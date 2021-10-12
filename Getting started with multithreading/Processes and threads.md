> This is part 2 of “Getting started with multithreading” series. Click for [part 1](https://lomas.hashnode.dev/synchronous-asynchronous-concurrency-and-parallelism) and [part 3](https://lomas.hashnode.dev/what-is-multithread)

### 1) What are processes?

![one to many.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1632210296518/lBbOOqm5J.jpeg)

A process initializes a program. Programs are nothing but a passive collection of instructions stored in a file on a
disk or simply our software.

A Process contains the program’s code and its activity. It’s the self-contained unit of execution that has all the
things necessary to accomplish the mission.

A program does not consume any memory; it is a passive entity whereas a process consumes some memory (RAM) and gets CPU
time. It’s an instance of a program running on a computer.

A ***“program becomes a process"*** when loaded into memory (RAM) and thus is an active entity or a dynamic entity.

A program can have several processes; for example, opening several instances of the same program often results in more
than one process being executed. Every process has its own memory space or address space.

To visualize in simple terms, consider a program as the McDonald company and its restaurants as the processes. The
company has a set of rules and regulations for the operation of restaurants and recipes of the food, but the actual
implementation of those rules and recipes is run by the restaurant. And Threads(see below) are the workers in a
particular restaurant.

### 2) What are threads?

![thread-roll-close-up.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1632210612730/arKE_BUU3.jpeg)

A thread is a ***portion of the process***. Thread is short for the **thread of execution**. It is a series of
commands (a block of code) that exists as a unit of work.

***A process may have several threads.*** Each of these threads executes semi-independently while sharing common
information. They can run concurrently or in parallel inside the same process.

Each thread has its executor, and this executor can perform only one thread at a time.

Threads run in a shared memory space inside its process. If there is no need of sharing the shared resources then tasks
can run concurrently inside the same thread, there is no need to run them in different threads. It is cheaper in terms
of resources to arrange concurrent execution with time-slicing inside one thread.

A thread is also known as a **lightweight process** because of the system resources they consume, as compared with
processes.

I found a very easy to understand analogy for threads on [StackOverflow](https://stackoverflow.com/a/5201906/14022489)
as follows:
Suppose you’re reading a book, and you want to take a break right now, but you want to be able to come back and resume
reading from the exact point where you left off. One way to achieve that is by jotting down the page number, line
number, and word number. So your execution context for reading a book is these 3 numbers. If you have a roommate and,
she’s using the same technique, she can take the book while you’re not using it, and resume reading from where she
stopped. Then you can take it back, and resume it from where you were.

Threads work in the same way. ***Just like you can share a book with your friend, many tasks can share a CPU.***

In technical terms, an **execution context** (therefore a thread) consists of the independent **set of values for the
processor registers**(for single-core).

The resources associated with a process include memory pages (all the threads in a process have the same view of memory)
, file descriptors (e.g., open sockets), and security credentials (e.g., the ID of the user who started the process).

### • What is time slicing?

![toy-bricks-table-with-word-time.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1632210905499/CX1CqRon4.jpeg)

A CPU is giving you the illusion that it’s doing multiple computations at the same time. It does that by spending a bit
of time on each computation. It can do that because it has an execution context for each computation(Read above to
understand “execution context”).

The operating system can manage multiple threads and assign a thread a piece ***(“slice”)*** of processor time before
switching to another thread to give it a turn to do some work.

***At its core, a processor can simply execute a command, it has no concept of doing two things at one time. The
operating system simulates this by allocating slices of time to different threads.***

Now, if you introduce multiple cores/processors into the mix, then things can actually happen at the same time. The
operating system can allocate time to one thread on the first processor, then allocate the same block of time to another
thread on a different processor. All of this is about allowing the operating system to manage the completion of your
task while you can go on in your code and do other things.

The **“execution inside the threads”** can be synchronous or asynchronous but never parallel because of the “single
executor per thread”.

### • Process Vs Threads:

![wepik-2021821-12443.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1632168116533/bqyUcL59i.png)

- Each process has its own memory space whereas,  
  Threads use the memory of the process they belong to.

- Communication between different processes is slow since processes have different memory addresses whereas,  
  Communications between threads are faster due to sharing of the same memory with the process they belong to.

- Processes are independent of one another due to separate memory spaces whereas,  
  Threads run in shared memory space.


- While one process is blocked, no other process can be executed until the first process is unblocked whereas,  
  If one thread is blocked and waiting, a second thread in the same task can run.

- ***Every process has at least one thread*** as they do all the work. There is no such thing as a thread without a
  process or a process without a thread.

- Each process starts with a thread called the **main thread.** It can initiate the creation of additional threads
  inside the application, and every newly created thread can do it as well.

- Process management is the responsibility of the operating system whereas,  
  Thread management is the concern of the application.

Regards,  
Lomas Singh

***Image credits:***

Cover photo by 8photo

<a href='https://www.freepik.com/photos/business'>Process image by onlyyouqj - www.freepik.com</a>

<a href='https://www.freepik.com/photos/background'>Threads image by rawpixel.com - www.freepik.com</a>

<a href='https://www.freepik.com/photos/time'>Time-slicing image by Racool_studio - www.freepik.com</a>

<a href='https://www.freepik.com/photos/business'>Process vs threads image by jcomp - www.freepik.com</a>
