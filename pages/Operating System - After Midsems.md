# Process
	- ## Process synchronization
		- Process
			- Cooperative process : Dependent; share variable/memory/buffer/code/resources etc
				- Race conditions -> Synchronization
			- Independent process
		- ### Producer Consumer Problem
			- Producer produces onto buffer and consumer consumes it! Case of race conditions due to shared variable.
			- ![image.png](../assets/image_1714938042924_0.png){:height 276, :width 470}
			- Solution
				- ![image.png](../assets/image_1714989441974_0.png)
				-
		- ### Printer spooler Problem
			- ![image.png](../assets/image_1714940096306_0.png){:height 349, :width 429}
		- ### Critical Section
			- Part of program having shared resources accessed by various processes
			- Prefix and Suffix by entry and exit section in program and wait till they are complete, before completing their own's.
			- #### Synchronization Mechanism
				- Mutual Exclusion: One access at a time
				- Progress: Mutual blocking and no progress
				- Bounded Wait: Starvation on one process, due to multiple allocation to single process making other starve for lock on critical section.
				- No assumption related to H/W and speed
		- ### Synchronization
			- #### LOCK Variable
				- ```c
				  while (LOCK == 1); // entry 
				  LOCK = 1;          // entry
				  // access critical section
				  LOCK = 0;          // exit
				  ```
				- User mode; Multi-process; Mutual exclusion is not guaranteed if a process preempt after running instruction 1.
			- #### Test and set
				- Entry point must be *atomic instructions*.
				- It's guaranteed that if a process is currently performing a `test_and_set`, no other process may begin another `test_and_set` until the first process's `test_and_set` is finished.
				- ```c
				  while (test_and_set(&lock)); // atomic op
				  // access critical section
				  LOCK = false;
				  ```
				- ```cpp
				  bool test_and_set(bool *target) {
				    bool r = *target;
				    *target = true;
				    return r;
				  }
				  ```
			- #### Turn Variable (Strict Alternation)
				- For _two process only_, user mode, alternating turns
				- Process Pa
					- ```c
					  while (turn != 0);
					  // critical section
					  turn = 1;
					  ```
				- Process Pb
					- ```c
					  while (turn != 1);
					  // critical section
					  turn = 0;
					  ```
			- #### Semaphore
				- Binary Semaphore (0, 1)
				- Counting Semaphore (-\infty to \infty)
				- P() or Down or Wait -> To add a new entry section
				- V() or Up or Signal, Wait or Release -> To remove a entry via exit section
				- ```c
				  Down(Semaphore S) {
				    S.value -= 1;
				    if (S.value < 0) {
				      // put process(PCB) in suspend list
				      sleep();
				    }
				    else {
				      return;
				    }
				  }
				  ```
				- ```c
				  Up(Semaphore S) {
				    S.value += 1;
				    if (S.value <= 0) {
				      // select process(PCB) in suspend list
				      wakeup();
				    }
				  }
				  ```
			- #### Binary Semaphore
				- ```c
				  Down(Semaphore S) {
				    if (S.value == 1) {
				      S.value = 0;
				    }
				    else {
				      // block this process(PCB) in suspend list
				      sleep();
				    }
				  }
				  ```
				- ```c
				  Up(Semaphore S) {
				    if (/*Suspend list is empty*/) {
				      S.value = 1;
				    }
				    else{
				      // select process(PCB) in suspend list
				      wakeup();
				    }
				  }
				  ```
			-