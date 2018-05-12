# [PREDATOR: Predictive False Sharing Detection](https://people.cs.umass.edu/~emery/pubs/Predator-ppopp14.pdf)

###### Tongping Liu, Chen Tian, Ziang Hu, Emery D. Berger

---

### What is the Problem?

Existing approaches can only report false sharing actually observed during execution; they do not generalize across executions, nor they can predict the impact of false sharing on hardware with different cache line sizes.

### Summary

This paper presents PREDATOR, a predictive software-based false sharing detector. PREDATOR tracks accesses within a _range_ that could lead to false sharing given different object placement. It also tracks accesses within _virtual cache lines_, contiguous memory ranges that span actual hardware cache lines, to predict sharing on hardware platforms with larger cache line sizes.

### Key Insights

### Notable Design Details/Strengths

- PREDATOR combines compiler instrumentation with a runtime system to track cache invalidations. The compiler instruments memory accesses with calls to the runtime system that notify it when an access occurs, and the runtime system collects and analyzes these accesses to detect and report false sharing.

- PREDATOR tracks cache invalidations of all cache lines, and ranks the severity of performance degradation of any detected false sharing problems according to the number of cache invalidations.

### Limitations/Weaknesses

### Summary of Key Results

### Open Questions

### References
