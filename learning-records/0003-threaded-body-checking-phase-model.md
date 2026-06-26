# Threaded body checking phase model

The learner understands the main checker split: global declarations and procedure signatures are resolved before procedure bodies are checked in parallel. They also understand that body work is represented as queued `ProcInfo` tasks and that newly discovered body work during the body-checking phase is submitted back to the thread pool. The important refinement is that Odin also parallelizes some earlier collection/export/dependency work, and the thread pool uses already-created workers rather than spawning a new worker thread per procedure body.
