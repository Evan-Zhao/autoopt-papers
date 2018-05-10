# Automatic Profiling and Optimizations of Applications

## Improving Data Layout at Memory Allocation (Runtime)

### Phenomenon Research

- reduce-false-sharing: variation of cache miss rate w.r.t. cache block size and kind of variables

### Better Allocators

- hoard: Hoard allocator, using shared heap + per-process heaps

- reduce-false-sharing: several optimizations of data layout.
    - SplitScalar: Place scalar variables into different blocks (their ideal architecture has control over cache blocks)

    - HeapAllocate: Allocate from different heap regions for different processors

    - Expand Record: Pad between fields of a record (struct).

    - Align Record: Choose a layout for arrays of records that minimizes the number of blocks the average record spans.

    - LockScalar: Place active scalars with a lock in the same block as the lock variable.

### Hardware Acceleration

- mallacc: dedicated hardware for allocator operations

### Allocator Evaluations

- alloc-experiment: compared 7 allocators comprehensively and statistically significantly.

- cache-locality: early paper, studied some poorly-designed allocator and showed allocators may impact perfomance by increasing paging and cache miss rates.

### Ignored Keywords

#### Algorithm for parallel memory allocation

- Some ancient papers focus on this. We should already have this in modern allocators.

#### Buddy system/algorithm

- This minimizes little bits of allocator _memory_ overhead, which is of more interest when memory was tight.

## Improving Data Layout at Compile Time

## Improving Text Layout
