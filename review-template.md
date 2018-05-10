# [The Mystery Machine: End-to-end Performance Analysis of Large-scale Internet Services](http://web.eecs.umich.edu/~twenisch/papers/osdi14.pdf)

###### Michael Chow, David Meisner, Jason Flinn, Daniel Peek, Thomas F. Wenisch

---

### What is the Problem? [Good papers generally solve *a single* problem]

Existing performance debugging methods for complex distributed systems do not provide useful information about end-to-end performance characteristics, because it is challenging to construct an execution model of requests in a highly-distributed heterogeneous system. 

### Summary [Up to 3 sentences]

The Mystery Machine analyzes end-to-end request executions in a modern Internet service (Facebook) to automatically infer the request execution model and the performance behavior by making minor changes to the existing logging infrastructure. Mystery Machine relies on the law of large numbers to automatically build causal relationships between the components (segments) of a request. Using the findings of The Mystery Machine, connections with no slack (i.e., room for deferring) can be prioritized to improve their end-to-end latency while connections with enough slack can be deprioritized without harming their end-to-end latency.

### Key Insights [Up to 2 insights]

- One can automatically construct a model of request execution by generating a large number of potential hypotheses about program behavior and rejecting the hypotheses contradicted by the empirical observations. This is an example of the more general idea of *iteratively refining likely execution invariants*.
- Complex performance optimizations in a large scale Internet service can be validated without the actual implementation effort. This is possible by relying on the inherent variability in system behavior that manifests naturally over large number of requests.

### Notable Design Details/Strengths [Up to 2 details/strengths]

- UberTrace, which is the end-to-end request tracing component that Mystery Machine relies on, uses sampling to reduce overhead. However, sampling reduces the probability that individual logging systems monitor the same set of requests. In order to perform targeted request monitoring, UberTrace propagates the decision about whether or not to monitor a given request through all logging subsystems along the path of the request.
- A key strength of The Mystery machine is that it discovers and updates dependencies in a request automatically. This is a key feature because the underlying logging infrastructure is constantly evolving.

### Limitations/Weaknesses [up to 2 weaknesses]

- The Mystery Machine could recompute model changes incrementally rather than from scratch to account for the changes in the request model.
- The Mystery Machine makes the assumption that the segments in a call graph are acyclic. It is unclear how the system design would need to be changed in the presence of cycles (e.g., what happens when the same <event, task> pair appear more than once in a request trace).

### Summary of Key Results [Up to 3 results]

- There is significant variation in the contribution of major end-to-end performance components (servers, network, and client) to the critical path. One can use this variation to provide differentiated service (e.g., prioritizing service where the server has no slack, whereas deprioritizing those where network and client latency will likely dominate).
- Slack tends to remain stable for a given user across multiple Facebook sessions, so past slack information can be used to predict the slack of the current connection.

### Open Questions [Where to go from here?]

- The performance properties analyzed by the Mystery machine are fairly high-level. One interesting direction would be to extend this work to gather more information in a targeted way to do more low-level performance debugging (e.g., what code is responsible for the slow down?).
- The scope of the work can be extended to look into end-to-end performance analysis for mobile platforms in addition to the desktop.
