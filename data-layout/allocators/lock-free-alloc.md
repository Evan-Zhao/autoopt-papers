# [Scalable Lock-Free Dynamic Memory Allocation](https://dl.acm.org/citation.cfm?id=996848/)

###### Maged M. Michael

---

### What is the Problem?

Dynamic memory allocators (malloc/free) rely on mutual exclusion locks, which has many disadvantages with respect to performance, availability, robustness, and programming flexibility.

### Summary

This paper presents a completely lockfree memory allocator, using only widely-available operating system support and hardware atomic instructions. Also, by leveraging some high-level structures from Hoard, our allocator inherits the advantages of Hoard while allows finer concurrency and much lower latency than Hoard.

### Key Insights

Lock-free synchronization implies several inherent advantages: immunity to deadlock, async-signal-safety (could be used by signal handlers safely), tolerance to priority inversion, kill-tolerant availability, preemption-tolerance.

### Notable Design Details/Strengths

We break down malloc and free into fine atomic steps, and organize the allocator’s data structures such that if any thread is delayed arbitrarily (or even killed) at any point, then any other thread using the allocator will be able to determine enough of the state of the allocator to proceed with its own operation without waiting for the delayed thread to resume.

### Limitations/Weaknesses

### Summary of Key Results

### Open Questions

### References
