# [AutoFDO: Automatic Feedback-Directed Optimization for Warehouse-Scale Applications](https://ai.google/research/pubs/pub45290)

###### Dehao Chen, David Xinliang Li, Tipp Moseley

---

### What is the Problem?

The use of feedback directed optimization (FDO) for datacenter applications is especially compelling, but the nature of these applications makes maintaining a representative benchmark, and thus the deployment of FDO, prohibitively difficult.

### Summary

AutoFDO is a system to simplify real-world deployment of FDO. The system works by sampling hardware performance monitors on production machines and using those profiles to guide optimization. Profile data is stale by design, and we have implemented compiler features to deliver stable speedup across releases.

### Key Insights

### Notable Design Details/Strengths

### Limitations/Weaknesses

### Summary of Key Results

### Open Questions

### References

- Sampling with hw counters: 5-10

- Sampling without hw counters: 11, 30
