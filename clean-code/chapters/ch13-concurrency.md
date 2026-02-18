## Chapter 13: Concurrency

### Why Concurrency?
- **Decoupling:** Separates *what* gets done from *when* it gets done.
- **Throughput:** Improves response time and structure (e.g., handling multiple I/O-bound requests).
- **Complexity:** Harder than single-threaded code; surface-level correctness masks deep, stress-induced bugs.
- **Myths:** It doesn't always improve performance; design *must* change; frameworks don't exempt you from knowing the fundamentals.

### Challenges
- **Race Conditions:** Multiple execution paths can lead to inconsistent state.
- **Nondeterminism:** Bugs are often unrepeatable "one-offs" that are actually logic defects.
- **Path Explosion:** With N instructions and T threads, possible orderings = (T×N)! / (N!)^T — even trivial code has thousands of interleavings.

### Concurrency Defense Principles
- **SRP for Concurrency:** Keep concurrency-related code separate from business logic.
- **Limit Data Scope:** Encapsulate shared data strictly; the more places shared data is updated, the higher the risk.
- **Use Copies:** Avoid sharing data by copying objects (read-only) or merging results from independent tasks.
- **Independence:** Partition data into subsets that tasks can process without synchronization.

### Standard Execution Algorithms
- **Producer-Consumer:** Producers fill a buffer; consumers empty it. Needs coordination on empty/full states.
- **Readers-Writers:** Balancing throughput for many readers with occasional updates; risk of writer starvation.
- **Dining Philosophers:** Represents tasks competing for multiple resources; high risk of deadlock.

### Development Guidelines
- **Small Critical Sections:** While Java uses `synchronized/yield/wait`, the principle is universal: keep locked sections tiny.
- **Avoid Multi-Method Locking:** Using multiple locked methods on one shared object is dangerous.
- **Execution Models:** Understand Deadlock (waiting for each other), Starvation (denied access), and Livelock (resonance).
- **Four Deadlock Conditions:** Mutual exclusion + lock & wait + no preemption + circular wait. Break any one to prevent deadlock.
- **Thread-Safe Collections:** Prefer `ConcurrentHashMap`, atomic classes (`AtomicInteger`), and `putIfAbsent`-style compound operations over manual locking.
- **Graceful Shutdown:** Design shutdown early; tasks blocked on external input are notoriously hard to kill.

### Modern Patterns
- **Async/Await & Event Loops:** (Node.js, Python) Concurrency via non-blocking I/O on a single thread.
- **Channels & Goroutines:** (Go) Communicating by sharing memory vs sharing memory by communicating.
- **Actor Model:** (Erlang, Akka) Isolated entities that communicate solely via message passing.
- **Core Truth:** Whether using threads or actors, the goal is always to isolate shared state and minimize sync.

### Testing Strategies
- **Treat One-offs as Real Bugs:** Never ignore a "glitch"; if it happened once, it's a race condition.
- **Test on Multiple Platforms:** Execution behavior varies wildly between OSs and runtimes.
- **Force Failures:** Use "jiggling" (injecting random delays) to increase the probability of exposing rare races.

### Agent Relevance
Agents frequently generate race conditions by sharing mutable state between async operations.
The "use copies" and "thread independence" principles are the most directly applicable defensive patterns for agentic workflows.
