# Virtual Memory
We have covered the basic principles of memory in lectures, now some specifics relating to Windows only. 

Virtual memory arose as a granular solution to the complex problem of how to deal with programs that will not all fit into real memory at once. In a virtual-memory system, programs are given access to a larger set of addresses than is physically available, and a dedicated memory manager maps these logical addresses to actual locations, using temporary storage on disc to hold the overflow. In the implementation of virtual memory that Windows uses, virtual storage is organized into units known as pages. Each process is allocated its own virtual address space, which is a set of virtual-memory pages that it can read from and write to. Each page can be in one of three states: 

Free: The process is not yet using that area of the address space. Any attempt to access that area for reading or writing causes an error. A Windows dialog box will pop up to say that an access violation has occurred or similar. Java programs cannot make this kind of mistake; only a program written in a language that supports pointers can. 

Reserved: This area of the address space has been reserved for future use by the process but cannot be accessed until it has been committed. A lot of the Java heap starts off as reserved. 

Committed: Memory that can be accessed by the program and is fully backed, which means that page frames have been allocated for it in the paging file. Committed pages are loaded into main memory only when the process first references them. This is called on-demand paging.

<figure>
<img src = "https://jor-donegal.github.io/PowerShell7/images/fig1.png">
<figcaption>Fig 1. Virtual Memory.</figcaption>
</figure>

On the standard lab machines, the total virtual address space for a process is 4GB (calculate 232). Windows does not allow access to all the memory in this address space. 

Using the example of Java programming, your process gets just under half for its own private use, and Windows uses the rest. The 2GB private area contains most of the memory the JVM needs to execute your program, the Java heap, the C heap for the JVM itself, stacks for program threads, memory for holding byte code and methods, memory that native methods allocate, etc. 

Physical storage is organized into equal-sized units, page frames. The page table maps the virtual pages accessed by applications to real page frames in main memory. The pages that cannot fit are kept in temporary paging files on disk. When a process tries to access a page that is not currently in memory, a page fault occurs that causes the memory manager to retrieve it from the paging file and put it back into main memory (paging). 

The precise algorithm used to decide which page should be swapped out depends on the version of Windows you are using; it is probably a variation of the least-recently-accessed method. It is also important to note that Windows allows page frames to be shared between processes, for example for DLLs, which are often used by several applications at once. Windows does this by mapping multiple virtual pages from different address spaces to the same physical location. An application is unaware of all this activity, all it knows about is its own virtual address space. However, an application soon begins to suffer a marked degradation in performance if the set of its pages currently in main memory, known as the resident set, is smaller than the set of pages it needs to use, known as the working set. 

The terminology used here should all be familiar to you from lectures. If not, do a little bit of searching and reading on the Internet until you are comfortable that you understand what is going on!