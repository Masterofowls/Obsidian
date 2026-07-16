---
aliases: [code-execution, how-code-runs, interpreter, compiler]
tags: [software, code, execution, compiler, interpreter]
cssclass: wiki
---
# How Code Execution Works

## Compiled Languages (C, C++, Rust)
1. **Compiler** translates source code → machine code (binary)
2. Machine code is stored as an executable file
3. CPU directly executes the machine code
4. No runtime translation needed → fast

## Interpreted Languages (Python, JavaScript)
1. **Interpreter** reads source code line by line
2. Translates and executes each line immediately
3. No separate executable file
4. Slower than compiled, but more flexible

## JIT (Just-In-Time) Compilation (Java, C#, JavaScript engines)
1. Code starts as intermediate bytecode
2. JIT compiler translates hot paths to machine code at runtime
3. Best of both worlds: portability + speed

## How It Works (Simplified)
1. Source code is **parsed** into an Abstract Syntax Tree (AST)
2. AST is **compiled** or **interpreted** into operations
3. CPU executes operations using registers and memory
4. Results are written back to memory or output

## Related
- [[Wiki\Hardware\CPU|CPU]]
