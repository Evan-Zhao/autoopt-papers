# [Improving the Cache Locality of Memory Allocation](https://dl.acm.org/citation.cfm?id=155107)

###### Dirk Grunwald, Benjamin Zorn, Robert Henderson

---

### What is the Problem?

The allocation and disposal of memory is a ubiquitous operation in most programs, yet one largely ignored by most programmers. The majority of programmers use the memory allocator provided in a given programming environment, and rarely are programmers concerned with "secondary" effects, such as cache locality.

### Summary

In this paper, we show how the design of a memory allocator can significantly affect the reference locality for various applications. Our measurements show that poor locality in sequential-fit allocation algorithms reduces program performance, both by increasing paging and cache miss rates. Our measurements suggest an allocator design that is both very fast and has good locality of reference.

### Key Insights

Reference locality and allocator speed are two aspects of memory allocation that must be balanced to achieve high performance.

### Notable Design Details/Strengths

### Limitations/Weaknesses

### Summary of Key Results

### Open Questions

### References
