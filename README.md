# CALC Interpreter

### Mini Programming Language & Interpreter in Pure Java

![Java](https://img.shields.io/badge/Language-Java-orange)
![Architecture](https://img.shields.io/badge/Architecture-Interpreter-blue)
![Type](https://img.shields.io/badge/Project-Programming%20Language-green)

**Group Project developed as part of Advanced Object-Oriented Programming coursework at Sitare University.**

---

## What is CALC?

CALC (Concise Algorithmic Language for Computation) is a lightweight scripting language and interpreter built entirely in pure Java, featuring a custom tokenizer, parser, and execution pipeline.

```calc
x := 10
y := 3
result := x + y * 2
>> result

? result > 10 =>
    >> "big number"

@ 4 =>
    >> "hello"
````

---

## My Contribution

* Implemented parser components and expression tree handling
* Worked on execution pipeline integration and interpreter flow
* Contributed to modular instruction architecture and runtime evaluation logic

---

## Features

* Pure Java interpreter implementation
* Custom tokenizer and parser pipeline
* Abstract Syntax Tree (AST)-style expression evaluation
* Variables and arithmetic operations
* Conditional execution and loops
* Modular instruction architecture
* File-based `.calc` program execution

---

## Supported Language Features

* Variable assignment
* Arithmetic expressions
* String literals
* Conditional execution
* Loop execution
* Expression evaluation
* Console output

---

## Concepts Used

* Tokenization
* Parsing
* Expression Trees
* Abstract Syntax Representation
* Runtime Evaluation
* Object-Oriented Design
* Execution Pipelines

---

## Project Structure

```text
CALC-Interpreter/
│
├── src/
│   ├── tokenizer/
│   │   ├── TokenType.java       — enum of every token kind
│   │   ├── Token.java           — immutable token object
│   │   └── Tokenizer.java       — reads source, emits token list
│   │
│   ├── parser/
│   │   ├── Expression.java      — interface for all expression nodes
│   │   ├── NumberNode.java      — numeric literal node
│   │   ├── StringNode.java      — string literal node
│   │   ├── VariableNode.java    — variable reference node
│   │   ├── BinaryOpNode.java    — arithmetic and comparison node
│   │   └── Parser.java          — builds List<Instruction> from tokens
│   │
│   └── interpreter/
│       ├── Environment.java     — variable store (Map<String, Object>)
│       ├── Instruction.java     — interface for all instructions
│       ├── AssignInstruction.java
│       ├── PrintInstruction.java
│       ├── IfInstruction.java
│       ├── RepeatInstruction.java
│       └── Interpreter.java     — pipeline entry point
│
├── programs/
│   ├── program1.calc            — arithmetic and variables
│   ├── program2.calc            — string output
│   ├── program3.calc            — conditional
│   └── program4.calc            — loop
│
├── .gitignore
└── README.md
```

---

## Interpreter Pipeline

The interpreter runs as a 3-step pipeline:

```text
Source Code (.calc file)
        │
        ▼
   [ Tokenizer ]     — breaks source into a flat list of tokens
        │
        ▼
   [   Parser  ]     — builds expression trees and instructions
        │
        ▼
 [ Interpreter ]     — evaluates parsed expressions and executes instructions
        │
        ▼
      Output
```

---

## CALC Syntax

| Operation   | Syntax              | Example           |
| ----------- | ------------------- | ----------------- |
| Assign      | `x := <expression>` | `x := 10`         |
| Print       | `>> <expression>`   | `>> result`       |
| Conditional | `? <condition> =>`  | `? score > 50 =>` |
| Loop        | `@ <count> =>`      | `@ 4 =>`          |

### Operators

| Type       | Symbols         |
| ---------- | --------------- |
| Arithmetic | `+` `-` `*` `/` |
| Comparison | `>` `<`         |

---

## Sample Programs

### Program 1 — Arithmetic

```calc
x := 10
y := 3
result := x + y * 2
>> result
```

Expected Output:

```text
16
```

---

### Program 2 — Strings

```calc
name := "Sitare"
>> name
>> "Hello from CALC"
```

Expected Output:

```text
Sitare
Hello from CALC
```

---

### Program 3 — Conditional

```calc
score := 85
? score > 50 =>
    >> "Pass"
```

Expected Output:

```text
Pass
```

---

### Program 4 — Loop

```calc
i := 1

@ 4 =>
    >> i
    i := i + 1
```

Expected Output:

```text
1
2
3
4
```

---

## How to Compile and Run

### Compile all files from the project root

```bash
javac -d out src/tokenizer/*.java src/interpreter/*.java src/parser/*.java
```

### Run a `.calc` program

```bash
java -cp out interpreter.Interpreter programs/program1.calc
```

---

## Team

| Member   | Responsibility                                       |
| -------- | ---------------------------------------------------- |
| Member 1 | Tokenizer (TokenType, Token, Tokenizer)              |
| Member 2 | Parser (Expression Tree, Parser)                     |
| Member 3 | Interpreter (Instructions, Environment, Interpreter) |

---

## Branch Strategy

```text
main
├── tokenizer    — Member 1's branch
├── parser       — Member 2's branch
└── interpreter  — Member 3's branch
```

Each member worked on separate branches and merged changes into `main` through Pull Requests after review.

---

## Future Improvements

* Function definitions and user-defined procedures
* Boolean operators and nested conditions
* Better syntax diagnostics and error reporting
* REPL support for interactive execution
* Bytecode or virtual machine experimentation
