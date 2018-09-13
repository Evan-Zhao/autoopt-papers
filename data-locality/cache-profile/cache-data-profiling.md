# [Locating Cache Performance Bottlenecks Using Data Profiling](https://pdos.csail.mit.edu/papers/dprof:eurosys10.pdf)

###### Aleksey Pesterev, Nickolai Zeldovich, Robert T. Morris

---

### What is the Problem?

Effective use of CPU data caches is critical to good performance, but poor cache use patterns are often hard to spot using existing execution profiling tools.

Traditional profilers aren't of help because the costs due to frequent cache misses on a given piece of data disperses over instructions throughout the application and then becomes seemingly insignificant.

### Summary

**DProf** is a profiler optimized for spotting cache performance issues. It helps programmers understand cache miss costs by attributing misses to *data types* instead of code, classifying cache misses and providing  different views for each class.

### Key Insights

Cache misses can be classified as *compulsory*, *conflict*, *capacity*, *true sharing* and *false sharing*. Depicting the cause of each cache miss is a huge help to programmers trying to fix them. If the cause is clear, programmers know to adjust data layout for conflict and capacity misses and reconsider sharing strategy for true/false sharing misses.

### Notable Design Details/Strengths

- DProf provides 4 views, the top level one being *data profile* which associates data type to # of misses. *Miss classification* is available for each data type. Then *working set* view provides data type size info (for capacity miss) and an cache associativity graph (for conflict miss), while *data flow* view shows sequences of functions referencing particular objects (for share miss).
- DProf records *path traces* (roughly call graph + load/store info) by sampling raw data from CPU performance monitoring hardware, thus reducing overhead greatly. Meanwhile, it maintains an address set mapping from address to data type.

### Limitations/Weaknesses

- The working set view for debugging non-sharing misses is practically only size information of the object, yet size is not the only factor that affects misses. The order of access (that's why we have tiling) is also important and often more tunable.
- DProf assists optimization at a per-object level, yet it's possible to optimize at inter-object level as well. A typical example is data + lock that reside in different `alloc`s but used together.

### Summary of Key Results

- DProf successfully helped in optimizing true sharing in `Memcached` and workset size in `Apache` server, providing more explicit and accurate diagnosis than *OProfile* and *lock_stat.*
- DProf overhead consists of access sample overhead and object access history overhead. The former is approx. 1% per 1000 samples/s/core while the latter is different on each data type, averaging to 16% in `Apache`. Both overheads are adjustable by sampling rate.

### Open Questions

### References

This is a 2010 article. Its focus is further partitioned down to true/false sharing, which we already have a collection of, and data locality. Follow-ups on data locality includes:

1. End-to-end memory behavior profiling with DINAMITE. https://dl.acm.org/citation.cfm?id=2983941
2. A library for portable and composable data locality optimizations for NUMA systems. https://dl.acm.org/citation.cfm?id=2688509
3. Lightweight detection of cache conflicts. https://dl.acm.org/citation.cfm?id=3168819 (low-overhead cache miss detection, conflict miss detection)