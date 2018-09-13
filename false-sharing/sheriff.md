# [PREDATOR: Predictive False Sharing Detection](https://people.cs.umass.edu/~emery/pubs/Predator-ppopp14.pdf)

###### Tongping Liu, Chen Tian, Ziang Hu, Emery D. Berger

---

### What is the Problem?

Previous tools for detecting false sharing cannot distinguish false sharing from true sharing, have high false positive rates, and provide limited assistance to help programmers locate and resolve false sharing.

### Summary

This paper presents two tools that attack the problem of false sharing: SHERIFF-DETECT and SHERIFF-PROTECT. Both tools leverage a framework we introduce here called SHERIFF. 

SHERIFF-DETECT finds instances of false sharing by comparing updates within the same cache lines by different threads, and uses sampling to rank them by performance impact.

SHERIFF-PROTECT mitigates false sharing by adaptively isolating shared updates from different threads into separate physical addresses, effectively eliminating most of the performance impact of false sharing.

### Key Insights

### Notable Design Details/Strengths


### Limitations/Weaknesses

### Summary of Key Results

### Open Questions

### References
