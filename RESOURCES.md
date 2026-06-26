# Odin Type Checker Resources

## Knowledge

- [src/checker.cpp](src/checker.cpp)
  Main checker orchestration. Use for: phase order, worker scheduling, queue merging, global entity checking, procedure-body checking, and final semantic passes.
- [src/checker.hpp](src/checker.hpp)
  Core checker data structures. Use for: `CheckerInfo`, `CheckerContext`, `DeclInfo`, `Operand`, queues, and checker APIs.
- [src/entity.cpp](src/entity.cpp)
  Entity definitions and allocation helpers. Use for: entity kinds, entity states, flags, and how named semantic objects are represented.
- [src/check_decl.cpp](src/check_decl.cpp)
  Declaration resolution. Use for: `check_entity_decl`, global variables, constants, type names, procedure declarations, procedure groups, and declaration-cycle detection.
- [src/check_expr.cpp](src/check_expr.cpp)
  Expression checking. Use for: operand production, addressing modes, literals, identifiers, calls, selectors, casts, indexing, and how `TypeAndValue` is recorded on AST nodes.
- [src/check_type.cpp](src/check_type.cpp)
  Type construction and validation. Use for: struct/union/enum/procedure type checking, polymorphic records, type completion, and layout-relevant type work.
- [src/parser.hpp](src/parser.hpp)
  AST-side semantic storage. Use for: `AddressingMode`, `TypeAndValue`, and the semantic fields attached to parsed nodes.
- [src/thread_pool.cpp](src/thread_pool.cpp)
  Thread-pool implementation. Use for: how checker tasks are scheduled and waited on.
- [src/threading.cpp](src/threading.cpp)
  Low-level synchronization primitives. Use for: mutexes, wait signals, and threading support used by checker/type completion code.

## Wisdom (Communities)

- Odin repository discussions and issues
  Use for: design intent questions that are not answered by the source. Prefer source-backed questions with exact file/function references.
- Odin Discord or forum channels, if available to the learner
  Use for: practitioner feedback on why specific checker tradeoffs were made. Record any community preference before relying on this path.

## Generated Explainers

- [explainers/0001-odin-checker-design.html](explainers/0001-odin-checker-design.html)
  Overview of Odin's checker pipeline and semantic-analysis architecture.
- [explainers/0002-entity-lifecycle.html](explainers/0002-entity-lifecycle.html)
  Visual explanation of entity lifecycle and declaration-resolution state.
- [explainers/0003-operands-in-odin-checker.html](explainers/0003-operands-in-odin-checker.html)
  Explanation of `Operand` as the checked expression result and how addressing modes classify use.
- [explainers/0004-threaded-procedure-body-checking.html](explainers/0004-threaded-procedure-body-checking.html)
  Explanation of Odin's phase barrier before threaded procedure-body checking and how `ProcInfo` work is queued.
- [explainers/0005-odin-thread-pool-work-stealing.html](explainers/0005-odin-thread-pool-work-stealing.html)
  Explanation of Odin's fixed worker thread pool, per-thread queues, work stealing, futex sleeping, and task waiting.
- [explainers/0006-thread-pool-ring-resize-memory-order.html](explainers/0006-thread-pool-ring-resize-memory-order.html)
  Visual step-through of ring-buffer resize, old-ring stealing, `bottom` publication, and acquire/release ordering.

## Gaps

- No primary design document for Odin's checker has been identified in this workspace yet.
- No C-compiler-specific target architecture document exists yet; future sessions should create one before turning Odin patterns into implementation tasks.
