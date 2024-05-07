# Process
collapsed:: true
	- ## Process synchronization
		- Process
			- Cooperative process : Dependent; share variable/memory/buffer/code/resources etc
				- Race conditions -> Synchronization
			- Independent process
		- ### Problems
			- #### Producer Consumer Problem
				- Producer produces onto buffer and consumer consumes it! Case of race conditions due to shared variable.
				- ![image.png](../assets/image_1714938042924_0.png){:height 276, :width 470}
				- Solution
					- ![image.png](../assets/image_1714989441974_0.png){:height 324, :width 468}
			- #### Printer spooler Problem
				- ![image.png](../assets/image_1714940096306_0.png){:height 349, :width 429}
			- #### Reader Writer Problem
				- Database R/W problem on same data
				- rc = read counter
				- ![image.png](../assets/image_1714989830913_0.png){:height 327, :width 367}
			- #### Dining Philosopher's Problem
				- ![image.png](../assets/image_1714992719272_0.png){:height 253, :width 208}
				- ![image.png](../assets/image_1714992687003_0.png){:height 279, :width 330}
				- Deadlock: If all philosopher takes there left fork, then nobody can eat and signal can't be given either.
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
	- ## Deadlocks
		- Waiting on some event that never happens (eg: Dining Philosopher's Problem)
		- Conditions
			- Mutual Exclusion : No resource interleaving
			  logseq.order-list-type:: number
			- No preemption : No release of resource at preemption
			  logseq.order-list-type:: number
			- Hold & Wait : Hold resources acquired & Wait for event(resources)
			  logseq.order-list-type:: number
			- Circular Wait : Loop
			  logseq.order-list-type:: number
		- ### Resource Allocation Graph
			- ![image.png](../assets/image_1715063494919_0.png){:height 358, :width 431}
			- ![image.png](../assets/image_1715063524421_0.png){:height 224, :width 422}
			- Waiting
				- Finite -> Starvation
				- Infinite time -> Deadlock
			- In single instance, if RAG has cycle -> Deadlock and vice versa
		- ### Deadlock Management
			- Deadlock Ignorance (Ostrich method) : Performant
			  logseq.order-list-type:: number
			- Prevention
			  logseq.order-list-type:: number
				- Avoid mutual exclusion
				  logseq.order-list-type:: number
				- Premption using scheduling algo (time quanta)
				  logseq.order-list-type:: number
				- No hold & wait: All the resource the process is given before start, not on demand.
				  logseq.order-list-type:: number
					- #### Banker's Algorithm
						- ![image.png](../assets/image_1715070225374_0.png)
						- Remaining Need = Max Need - Allocation
						- Condition for no deadlock: Resources + Process > Total demand
				- Circular Wait: All resources are numbered and a process can request upcoming resource in increasing order of previous request. (Access 3rd now can access >3 resource only!)
				  logseq.order-list-type:: number
			- Avoidance (Banker's Algorithm) : Predetermine if safe or not!
			  logseq.order-list-type:: number
			- Detection & Recovery: Kill the process linearly/Resource preemption
			  logseq.order-list-type:: number
		-
- # Memory Management
	- Multiprogramming: More & more process from secondary memory to RAM
		- CPU Utilization = 1 - K^n (n = no. of process in RAM at time; k = I/O time ratio)
	- Techniques
		- Contiguous - Fixed partition (static), Variable parition (Dynamic)
		- Non-contiguous - Paging, Mutilevel paging, Inverted paging, Segmentation, Segmented paging
	- ## Contiguous
		- ### Fixed partition (Static)
			- No of partitions are fixed, not the size
			- Spanning is not allowed. (Entire process need to be accommodated in one partition)
			- Internal fragmentation : Waste of memory space due to smaller process than the partition in RAM
			- Has a limit in max process size & degree of multi-programming/no. of process at a time.
			- External fragmentation: The RAM has sufficient memory but isn't contiguous to allot to a process.
		- ### Variable partition (Dynamic)
			- The partition are determined at runtime on demand and can be changed as well per need with no cap on numbers.
			- Pros: No internal fragmentation, no limit of no. of process/ process size.
			- Cons: External fragmentation (de-allocation creates holes in memory, which can be resolved using compaction i.e. moving non-allocated memory at whole together, but this is undesired) and allocation & deallocation is complex
			- ![image.png](../assets/image_1715102638707_0.png){:height 208, :width 138}
			- #### Allocation Algorithms
				- First fit : To the first _fit_ hole after 0. (simple, fast, internal fragmentation)
				  logseq.order-list-type:: number
				- Next fit : To the next _fit_ hole after the previously allocated hole. (faster, internal fragmentation)
				  logseq.order-list-type:: number
				- Best fit : To hole with least internal fragmentation. (slow, least internal fragmentation, smaller holes may become unusable)
				  logseq.order-list-type:: number
				- Worst fit : To hole with max size. (slow, least internal fragmentation)
				  logseq.order-list-type:: number