# Standard library thread pool first

The learner understands that Odin's internal checker pool is optimized and complex, while `core:thread` provides a simpler central-queue thread pool that should be sufficient for an initial C compiler checker. The intended design is to validate the phase architecture first, hide the executor behind a small abstraction, and replace the pool only if profiling proves it necessary.

