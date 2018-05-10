# [Hoard: A Scalable Memory Allocator for Multithreaded Applications](http://www.cs.utexas.edu/users/mckinley/papers/asplos-2000.pdf)

###### (2000) Emery D. Berger, Kathryn S. McKinleyy, Robert D. Blumofe, Paul R. Wilson

---

### What is the Problem?

Existing memory allocators performs badly with _multithreaded_ programs. They can be the bottleneck of program in performance, scalability, introduce false sharing, or severely decrease memory efficiency in case of producer-consumer pattern.

### Summary

**Hoard** is a fast, highly scalable allocator that largely avoids false sharing and is memory efficient. Hoard combines one global heap and per-processor heaps, with a novel discipline that provably bounds memory consumption and has very low synchronization costs in the common case.

### Key Insights

Key features in order to obtain a scalable and memory-efficient allocator performance: speed (about as fast as a state-of-the-art _serial_ memory allocator), scalability (perf. scales linearly with # of processors), false sharing avoidance, low fragmentation.

### Notable Design Details/Strengths

Hoard maintains per-processor heaps and one global heap. When a per-processor heap’s usage drops below a certain fraction, Hoard transfers a large fixed-size chunk of its memory to the global heap, available for reuse by another processor. This algorithm bounds blowup and synchronization costs to a constant factor, and avoids false sharing by ensuring that the same processor almost always reuses from a given cache line.

### Limitations/Weaknesses

### Summary of Key Results

### Open Questions

### References

- Cache locality / reducing false sharing: 12, 15, 20, 36