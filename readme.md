Project Overview:

What is Pintos?
Pintos is a simple operating system framework for the 80x86 architecture. It supports kernel threads, loading and running user programs, and a file system, but it implements all of these in a very simple way. Pintos could, theoretically, run on a regular IBM-compatible PC. Unfortunately, it is impractical to supply every student a dedicated PC for use with Pintos. Therefore, we will run Pintos projects in a system simulator, that is, a program that simulates an 80x86 CPU and its peripheral devices accurately enough that unmodified operating systems and software can run under it. Bochs and QEMU simulators are used to run Pintos

Priority Scheduling
Priority scheduling is a non-preemptive algorithm and one of the most common scheduling algorithms in batch systems. Each process is assigned a priority. Process with the highest priority is to be executed first and so on.
When a thread is added to the ready list that has a higher priority than the currently running thread, the current thread immediately yields the processor to the new thread. Similarly, when threads are waiting for a lock, semaphore, or condition variable, the highest priority waiting thread is awakened first. A thread may raise or lower its own priority at any time, but lowering its priority such that it no longer has the highest priority causes it to immediately yield the CPU.

Priority Donation

Priority inversion is handelled in the scheduler. Consider high, medium, and low priority threads H, M, and L, respectively. If H needs to wait for L (for instance, for a lock held by L), and M is on the ready list, then H will never get the CPU because the low priority thread will not get any CPU time. The technique used to solve this issue is priority donation.


Alarm clock:

Reimplement timer_sleep(), defined in ‘devices/timer.c’. Although a working implementation is provided, it “busy waits,” that is, it spins in a loop checking the current time and calling thread_yield() until enough time has gone by. Reimplement it to avoid busy waiting.
Design Ideas for alarm clock :
In timer_sleep(), while loop is not efficient due to loop ececute thread_yield(). This will lead to have the busy waiting, so we need to put thread to sleep when busy and wake when not busy.
So we can put threads in timer_sleep() on block status, when the sleep time passed, wake up the threads, and then put it on ready status.

