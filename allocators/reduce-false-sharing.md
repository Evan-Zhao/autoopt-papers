# [False Sharing and Spatial Locality in Multiprocessor Caches](https://ieeexplore.ieee.org/abstract/document/286299/)

###### Josep Torrellas, Mbnica S. Lam, John L. Hennessy

---

### What is the Problem?

The high cache miss rate in multiprocessor systems significantly limit its performance. This is partly due to false sharing, and poor spatial locality among accesses to shared data has an even larger impact.

### Summary

We confirm through the analysis of six applications that false sharing and poor spatial locality among accesses to shared data have a significant impact on the miss rate. We propose optimizations with simple, local techniques that optimize the layout of shared data at the cache block level and can be implemented by the compiler.

### Key Insights

False sharing usually increases with the block size and tends to drive miss rates up with increasing block size, while spatial locality in the data produces a reduction in the miss rate as the block size increases.

### Notable Design Details/Strengths

### Limitations/Weaknesses

Most of the evaluations are done in the _ideal architecture_: caches are infinite; all memory references, read or writes, hits or misses, take a single cycle; and every instruction executes in one cycle. It's sometimes not clear how to transfer the paper result reasonably to a real architecture.

### Summary of Key Results

We propose five optimizations of the data layout to enhance spatial locality and mitigate false sharing: SplitScalar, HeapAllocate, Expand Record, Align Record, LockScalar. All optimizations except Lockscalar try to minimize false sharing. Lockscalar and AlignRecord try to increase the spatial locality of the data.

### Open Questions

### References
