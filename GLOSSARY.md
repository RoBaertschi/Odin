# Odin Type Checker Glossary

Canonical terms for discussing Odin's semantic analysis design and how its architecture can transfer to a C compiler.

## Terms

**Semantic analysis**:
The compiler phase that gives parsed syntax meaning by resolving names, checking declarations, assigning expression types, validating conversions, and recording semantic facts for later phases.
_Avoid_: Type checking when referring to the whole phase

**Type checking**:
The part of semantic analysis that determines and validates types for declarations and expressions.
_Avoid_: Semantic analysis when referring only to type compatibility

**Entity**:
A named semantic object in Odin, such as a variable, constant, type name, procedure, procedure group, import name, or label.
_Avoid_: Symbol when discussing Odin source structures

**Scope**:
The mapping from names to entities for a package, file, type, procedure, or nested block.
_Avoid_: Namespace when discussing local lexical lookup

**Declaration record**:
The stored semantic payload for a declaration before it is fully resolved: its AST, scope, type expression, initializer, dependencies, and checked state.
_Avoid_: AST declaration when referring to `DeclInfo`

**Operand**:
The intermediate result of checking an expression: addressing mode, type, constant value if any, and source expression.
_Avoid_: Expression result

**Addressing mode**:
The classification of an operand as invalid, no-value, value, variable, constant, type, builtin, procedure group, or a special assignable/query form.
_Avoid_: Value category unless comparing with C/C++

**Procedure body checking**:
The phase that checks statements and expressions inside a procedure after the procedure declaration and signature are known.
_Avoid_: Procedure declaration checking

**Phase barrier**:
A deliberate wait point between checker phases where queued concurrent work is drained and shared semantic state becomes consistent for the next phase.
_Avoid_: Synchronization point when the specific pipeline role matters

**Thread pool**:
A fixed set of worker threads that execute submitted tasks without creating a new thread per task.
_Avoid_: Thread-per-job model

**Work stealing**:
A scheduling strategy where an idle worker takes queued work from another worker's queue after exhausting its own queue.
_Avoid_: Shared global queue when discussing Odin's internal checker pool

**Compare-exchange**:
An atomic operation that updates a memory location only if its current value still equals the expected value.
_Avoid_: Lock when referring to the `top` race in Odin's work-stealing queue

**Acquire/release ordering**:
A memory-ordering relationship where release publishes earlier writes and acquire observes those published writes before later reads.
_Avoid_: Eventual consistency
