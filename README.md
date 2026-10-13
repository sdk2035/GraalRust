# GraalRust

Experimental Rust / LLVM / GraalVM research laboratory maintained under sdk2035.

**One project per language:** TruffleRust is a conceptual alias within this repository, not a second repository or an implemented AST interpreter. These are portfolio project names, not official GraalVM language distributions.

## Technical status

Architecture and research plan, created 2026-10-12. No validated Sulong execution or production-ready Rust runtime is delivered. “Experimental / academic” describes the intended workstream; it is not evidence of a published academic implementation.

## Proposed mechanism

`rustc → LLVM bitcode → Sulong (Truffle) → GraalVM`

Start with a no_std, allocation-free library exposing a C ABI over fixed-width integers. Rust standard-library linking, panic handling, LLVM dialect/version compatibility and native dependencies must be assessed separately. A rustc .bc file alone does not establish a runnable application.

Sulong supplies the Truffle-based LLVM execution layer. A direct Rust AST interpreter would be a separate future design decision within this same project.

## Initial scope

- Deterministic integer arithmetic and conditional control flow.
- Native reference results compared with execution of the same workload through Sulong.
- Recorded compiler, LLVM and GraalVM versions, OS, architecture, commands and logs.
- Explicit rejection or documentation of unsupported language/runtime features.

See [architecture and requirements](docs/specification.md) and [validation plan](docs/validation.md).

## Next task

**GRUST-001:** select and pin a compatible toolchain; produce one minimal bitcode artifact; capture native and Sulong results or a reproducible incompatibility report. Do not label the project a working pilot until the end-to-end evidence is committed.

## References

- [GraalVM LLVM compilation](https://www.graalvm.org/latest/reference-manual/llvm/Compiling/)
- [Sulong upstream](https://github.com/oracle/graal/tree/master/sulong)
- [rustc code generation options](https://doc.rust-lang.org/rustc/codegen-options/index.html)

## Portfolio

[Profile](https://github.com/sdk2035) · [Companion project](https://github.com/sdk2035/GraalGo)
