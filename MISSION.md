# Mission: Odin Type Checker Design

## Why
Learn how Odin structures semantic analysis and threaded type checking so the design can inform a C compiler implementation. The goal is not to memorize Odin internals, but to extract architecture patterns that transfer: symbol discovery, declaration resolution, expression typing, procedure-body checking, dependency handling, and safe parallelism.

## Success looks like
- Explain Odin's checker pipeline from parsed files to checked procedure bodies.
- Identify which semantic phases Odin parallelizes and which it keeps serialized.
- Design a C semantic analyzer with similar separation between declaration collection, type resolution, and function-body checking.
- Recognize where entity state, scopes, declaration records, and operand classification fit in a compiler.

## Constraints
- Use the local Odin source as the primary source of truth.
- Keep compiler-source changes out of scope unless explicitly requested.
- Prefer design-level understanding and transferable patterns over exhaustive coverage of every Odin language feature.

## Out of scope
- Reimplementing Odin's checker.
- Deep LLVM backend/codegen internals.
- Full Odin language tutorial material unrelated to semantic analysis.
- Broad compiler theory not tied back to the Odin source or the target C compiler design.
