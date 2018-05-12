# [Anatomy of High-Performance Matrix Multiplication](http://www.cs.utexas.edu/~flame/pubs/GotoTOMS_revision.pdf)

###### KAZUSHIGE GOTO, ROBERT A. VAN DE GEIJN

---

### What is the Problem?

Implementing matrix multiplication of near-optimal performance requires a thorough understanding of how the operation (kernel) must be layered at the macro level, in combination with careful engineering of high-performance kernels at the micro level. In particular, exploitation of a high-performance kernel needs to take architecture, especially multi-level memory structure, into consideration.

### Summary

This paper primarily addresses the macro issues, namely how to exploit a high-performance "inner-kernel". 

### Key Insights

The general gemm (large matrix multiplication) can be decomposed into multiple calls to gepp, gemp, or gepm. These themselves can be decomposed into multiple calls to gebp, gepb, or gepdot kernels. If these three lowest level kernels attain high performance, then so will the other cases of gemm.

### Notable Design Details/Strengths

Design decisions are justified by successively refining a model of architectures with multilevel memories. In the optimization of kernel `gebp`, constraints are gradually refined when multilevel cache and TLB are taken into account respectively.

### Limitations/Weaknesses

### Summary of Key Results

The resulted `dgemm` subroutine outperforms ATLAS in GFlops per second by a margin, and is comparable to vendor libraries (Intel/AMD) which adopted techniques very similar to those described in the paper.

### Open Questions

### References
