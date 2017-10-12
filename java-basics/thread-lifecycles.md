
##States in Thread

![Thread State](https://github.com/AntiiiMage/study-notes/blob/master/java-basics/images/thread-states.png)

Thread state | Description
---- | ---
NEW | A thread that has been created but hasn't yet started is in this state.
RUNNABLE | Thread state for a runnable thread. A thread in this state is executing in the JVM but it may be waiting for other resources from the OS, such as a processor.
BLOCKED | A thread that’s blocked waiting for a monitor lock is in this state.
WAITING | A thread that’s waiting indefinitely for another thread to perform a particular action is in this state.
TIMED_WAITING | A thread that’s waiting for another thread to perform an action for up to a speci- fied waiting time is in this state. 
TERMINATED | A thread whose run() method has finished is in this state (still a thread object but not a thread of execution).

##Pause the Thread

![StateSwitch](https://github.com/AntiiiMage/study-notes/blob/master/java-basics/images/thread-state-switch.png)

###yield()

A hint to the scheduler that the current thread is willing to yield its current use of a processor. The scheduler is free to ignore this hint.

It is rarely appropriate to use this method. It may be useful for debugging or testing purposes, where it may help to reproduce bugs due to race conditions. It may also be useful when designing concurrency control constructs such as the ones in the java.util.concurrent.locks package.

###sleep(long millis)

Causes the currently executing thread to sleep (temporarily cease execution) for the specified number of milliseconds, subject to the precision and accuracy of system timers and schedulers. The thread does not lose ownership of any monitors.

###join()

If thread A calls join() on a Thread instance B, A will wait for B to complete its execution before A can proceed to its own completion.

Method join() guarantees that the calling thread won’t exe- cute its remaining code until the thread on which it calls join() completes.

###wait()

A thread can pause its execution and wait on an object, a queue in this case, by calling wait(), until another thread calls notify() or notify- All() on the same object.
