# JavaScript Execution Pipeline IQ

## Concept: JavaScript Execution Layers

This note explains the major layers in the JavaScript execution pipeline using a side-by-side breakdown table, a simple file example, a pipeline diagram, and a TL;DR.

---

## Layer Comparison Table

| Layer | What it is | Output | Where it happens | Why it matters |
|------|------------|--------|------------------|---------------|
| Source Code | Human-readable JavaScript text | Code text | Developer editor or file system | The input that defines program behavior |
| Tokenization / Lexing | Breaking code into tokens | Stream of tokens | JS engine frontend | Converts raw text into structured pieces |
| Parsing | Building a syntax tree | Abstract Syntax Tree (AST) | JS engine frontend | Validates syntax and structures code logic |
| Compilation / Bytecode | Translating AST into internal instructions | Bytecode or intermediate code | JS engine compiler | Optimizes and prepares code for execution |
| Execution | Running instructions | Program output / side effects | JS engine runtime | Performs the actual work defined by code |

---

## Example Walkthrough

### Example file: `example.js`

```js
const x = 2 + 3;
console.log('value:', x);
```

### Layer 1: Source Code

- The file `example.js` contains the raw JavaScript program.
- This is what a developer writes and saves.
- Example text: `const x = 2 + 3; console.log('value:', x);`

### Layer 2: Tokenization / Lexing

The engine turns the source into tokens like:
- `const`
- `x`
- `=` 
- `2`
- `+`
- `3`
- `;`
- `console` `.` `log`
- `(` `'value:'` `,` `x` `)` `;`

This is the first pass that recognizes identifiers, operators, literals, and punctuation.

### Layer 3: Parsing

The parser reads tokens and builds an AST representing structure:

- VariableDeclaration
  - Identifier: `x`
  - BinaryExpression
    - Literal: `2`
    - Operator: `+`
    - Literal: `3`
- ExpressionStatement
  - CallExpression
    - MemberExpression: `console.log`
    - Arguments: `'value:'`, `x`

Parsing verifies the syntax and organizes the code for compilation.

### Layer 4: Compilation / Bytecode

The engine compiles the AST into internal instructions, such as:
- Load constant `2`
- Load constant `3`
- Add
- Store result in `x`
- Load `console.log`
- Load string `'value:'`
- Load variable `x`
- Call function

This stage prepares the program for efficient execution.

### Layer 5: Execution

The runtime executes the compiled instructions and produces output:

- `value: 5`

This is the stage where the program actually runs and produces side effects.

---

## Pipeline Diagram

```text
Source Code (example.js)
      |
      v
Tokenization / Lexing
      |
      v
Parsing -> AST
      |
      v
Compilation -> Bytecode / Intermediate Instructions
      |
      v
Execution -> Program Output
```

---

## TL;DR

- Source code is the text file a developer writes.
- Tokenization splits code into meaningful tokens.
- Parsing builds a syntax tree from tokens.
- Compilation turns the syntax tree into engine instructions.
- Execution runs the instructions and produces the final output.

This layered view helps explain how raw JavaScript becomes working behavior in a browser or Node.js runtime.
