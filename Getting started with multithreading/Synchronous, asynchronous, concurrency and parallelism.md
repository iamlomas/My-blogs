> This is part 1 of “Getting started with multithreading” series. Click for [part 2](https://lomas.hashnode.dev/processes-and-threads) and [part 3](https://lomas.hashnode.dev/what-is-multithread)

Before getting to multithreading let’s first prepare ourselves with some prerequisites i.e. **Synchronous and
Asynchronous programming, Concurrency and Parallelism.**

#### 1) What is Synchronous programming?

It is a programming workflow in which operations take place one by one.

The program moves to the next step when the current step has completed execution and has returned an outcome. It has one
executor only.

Most of the activities should go synchronously if their goal is to achieve some specific results.

Syntax:

`Input -> processing -> output -> input -> processing -> output....`

OR,

`Task 1 -> Task 2 -> ……… Task n`

E.g.- Words in a sentence, making a cup of tea, car assembling, etc

#### 2) What is Asynchronous programming?

It is a programming workflow in which you can move to another operation before the previous one finishes.

Operations of this kind often emerge when there is a need for waiting. You begin a routine, and let it run in the
background while you start your next, then at some point, say “wait for this to finish”.

It’s more like:
Start `A -> B -> C -> D ->....` Wait for `A` to finish.

The advantage is that you can execute `B`,`C` and or `D` while `A` is still running in the background or on a separate
thread (which we will get to know a bit later), so you can take better advantage of your resources and have fewer
“hangs” or “waits”.

E.g.- You are eating your food on an aircraft while flying, or you are recording video while bungee jumping etc.

#### 3) What is Concurrency?

It is an ability to execute multiple operations at the same time and no predefined order without affecting the final
outcome.

Concurrency appears when there is a scarce shared resource, and workers compete for access to it. The process of
managing access to scarce shared resources for concurrent tasks is called Synchronization.

Concurrency can appear with one executor and with multiple.

For concurrency, it’s necessary to have:
more than one task in operation at least one critical section (scarce shared resource required for task execution) for
these tasks.

The second name of concurrency is multitasking because there is no such thing as concurrency for one task.

#### 4) What is Parallelism?

Parallel processing is a method of simultaneously breaking up and running operations via multiple executors, thereby
reducing processing time. These can be either several independent operations or one big task split into smaller subtasks
and divided between workers.

Each task in parallel processing is running in a continuous period as a whole unit process.

The parallel execution is possible only if there is more than one executor. Since there are many executors processing
tasks in parallel, the second name of parallelism is multiprocessing.

#### • What is the difference between concurrency and parallelism?

![0_Tw6M41D444_7BXwE.jpeg](https://cdn.hashnode.com/res/hashnode/image/upload/v1631435067448/ji-97WXiR.jpeg)
Parallelism is, in some sense, a concurrency without a limited resource for task execution. If shared resources are
sufficient for all participants, processes can run in parallel. They don’t need to compete for resources and get access
to it by turn because we distribute tasks among several executors so that everyone has only one.

In concurrency two or more operations can start, run and complete in overlapping time periods. It does not necessarily
mean they’ll ever be running at the same instant, e.g.- multitasking on a single-core machine.  
But, Parallelism is when tasks literally run at the same time, e.g.- on a multicore processor.

Concurrency is a property of a program or system whereas Parallelism is the run-time behavior of executing multiple
operations at the same time.

To visualize in simple terms:
Concurrency is like having a juggler juggle many balls. Regardless of how it seems, the juggler is only
catching/throwing one ball per hand at a time. Parallelism is having multiple jugglers juggle balls simultaneously.

Use the term “parallel” when the simultaneous execution is assured or expected, and use the term “concurrent” when it is
uncertain or irrelevant if simultaneous execution will be employed.

#### • Can we mix concurrency and parallelism together?

![GettyImages-594836477-58fe53963df78ca159068b1a.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1631435113531/PrFbL5tte.jpeg)

Concurrency and parallelism often intersect and appear together. They can mutate one to another.

Concurrency is dealing with lots of things at once whereas parallelism is about doing lots of things at once.

Concurrency can appear with one executor or with multiple whereas Parallelism appears only when there are multiple
executors. Parallel tasks can become concurrent and so on. Practically, all combinations of concurrency and parallelism
are possible.

For example, you can drink a glass of water while giving a speech. Here you can drink and speak simultaneously in
several combinations. You can drink a whole glass of water and then complete your speech, or you can drink half of the
water in the glass and then complete half of the speech, then repeat it again, etc.   
In parallelism, you deliver your speech in a team of two. You can drink water while letting your friend deliver the
speech. This time, the two tasks are really executed simultaneously, and it’s called parallel.

Parallelism is a specific kind of concurrency where tasks are really executed simultaneously.

> Link to my original post : https://iamlomas.medium.com/synchronous-asynchronous-concurrency-and-parallelism-9eb8336df120

Regards,   
Lomas Singh
