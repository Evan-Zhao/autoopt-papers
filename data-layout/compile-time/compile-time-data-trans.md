# [Reducing False Sharing on Shared Memory Multiprocessors through Compile Time Data Transformation](https://ieeexplore.ieee.org/abstract/document/286299/)

###### Tor E. Jeremiassen, Susan J. Eggers

---

### What is the Problem?

False sharing could degrade performance in a multiprocessor system. In some coarse-grain, explicitly parallel applications, misses due to false sharing comprise between 40% and 90% of all cache misses.

### Summary

False sharing is caused by a mismatch between the memory layout of write-shared data and the crossprocessor
memory reference pattern to it. Our algorithms analyze explicitly parallel programs, producing information about their cross-processor memory reference patterns that identies data structures susceptible to false sharing and then chooses appropriate transformations to eliminate it.

### Key Insights

### Notable Design Details/Strengths

### Limitations/Weaknesses

How well the reduction in false sharing misses translated into improved execution time depended heavily on the memory subsystem architecture and previous programmer efforts to optimize for locality.

### Summary of Key Results

### Open Questions

### References
