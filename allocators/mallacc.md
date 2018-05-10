# [Mallacc: Accelerating Memory Allocation](https://dl.acm.org/citation.cfm?id=3037736)

###### Svilen Kanev, Sam (Likun) Xi, Gu-Yeon Wei, David Brooks

---

### What is the Problem?

A large fraction of cycles in datacenter is spent on low-level routines, for example, dynamic memory allocation consuming nearly 7% of all cycles in Google datacenters. 

### Summary

We see the possibility to accelerate these low-level routines with specialized hardwares. **Mallacc**
is a tiny in-core hardware block which accelerates the three primary operations of a typical memory allocation request: size class computation, retrieval of a free memory block, and sampling of memory usage. 

### Key Insights

- Calls to `malloc` routines tend to be very frequent, fast, and interspersed inside other application
code, so accelerators must be optimized for latency rather than throughput.
- `malloc` being only a mild hotspot of program efficiency, its accelerator brings a limited amount of overall application speedup, so overheads must be kept to a bare minimum.

### Notable Design Details/Strengths

Mallacc is designed not for a specific allocator implementation, but for use by a number of high-performance memory allocators commonly found in datacenters today.

### Limitations/Weaknesses

### Summary of Key Results

### Open Questions

### References

- Improved allocators: 1, 8, 11 (overview: 10)

- Allocator evaluation: 10
