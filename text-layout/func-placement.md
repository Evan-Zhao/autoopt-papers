# [Optimizing Function Placement for Large-Scale Data-Center Applications](https://research.fb.com/publications/optimizing-function-placement-for-large-scale-data-center-applications-2/)

###### Guilherme Ottoni, Bertrand Maher

---

### What is the Problem?

Modern data-center applications are good candidates for code-layout optimizations, yet no recent study has evaluated the benefit of function placement for such large-scale applications.

### Summary

Sample-based profiling data is collected from production binaries, which is then used to guide function placement. The Pettis-Hansen function placement algorithm is evaluated, after which we propose two improvements: an algorithm called C^3, and the selective use of huge pages.

### Key Insights

- Instrumentation-based profilers intorduces too much overhead to be used to gather accurate profiles from a production system. It is beneficial to have a system that can profile unmodified binaries running in production. This is possible through the use of sample-based profiling.

- By default, the linker places functions according to the order the object files are specified in the command line, which disperses the hot code across the text section and reduces the efficiency of caches and TLBs. There is a potential to improve the function order and the performance.

### Notable Design Details/Strengths

### Limitations/Weaknesses

### Summary of Key Results

### Open Questions

### References

- AutoFDO & alike: 1, 2, 34

- Pettis-Hansen: 3

- NP-hardness of optimizing data layout: 11

- Other text layout optimization experiments: 12, 20-29

- Data layout/transformation: 30-33
