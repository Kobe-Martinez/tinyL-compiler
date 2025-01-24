# tinyL Compiler

## Overview


A recursive-descent parser and code generator for the tinyL language, a compact programming language defined by its context-free grammar (CFG). This project demonstrates fundamental concepts in compiler design, including parsing, tokenization, and code generation. 


## Table of Contents

- [About tinyL Language](#about-tinyL-Language)
- [Features](#features)
- [Usage](#usage)
- [Code Structure](#code-structure)
- [Requirements](#requirements)
- [File Output](#file-output)
- [Contributing](#contributing)
- [License](#license)
- [Important Note](#important-note)


## About tinyL Language

Grammar (CFG):

```bash
<program> ::= <stmt_list> !
<stmt_list> ::= <stmt> <morestmts>
<morestmts> ::= ; <stmt_list> | ε
<stmt> ::= <assign> | <read> | <print>
<assign> ::= <variable> = <expr>
<read> ::= ? <variable>
<print> ::= % <variable>
<expr> ::= + <expr> <expr> | - <expr> <expr> | * <expr> <expr> | 
           & <expr> <expr> | | <expr> <expr> | <variable> | <digit>
<variable> ::= a | b | c | d | e | f
<digit> ::= 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
```

Example Code:

```bash
a=+2+25;%a!
```

Tokens:

```bash
Each token in tinyL is a single character, such as +, -, *, &, |, or variables like a and digits like 2
```


## Features

```bash
- Arithmetic Expressions: Supports addition (+), subtraction (-), multiplication (*), bitwise AND (&), and bitwise OR (|)

- Read/Write Operations: Allows reading from input using ? and writing to output using %

- Variable Support: Limited to a through f

- Digit Support: Includes digits 0 through 9
```


## Usage

##### Compiling tinyL Code:

1. Ensure you have the tinyL source code file (e.g., example.tinyL)

2. Compile and run the program:
   
```bash
./compiler example.tinyL
```

3. The compiled output will be written to tinyL.out

##### Input Example:

Given the following tinyL code:

```bash
a=+2*3b;%a!
```

The compiler processes it and outputs the intermediate instructions in tinyL.out


## Code Structure

The primary files in this project include:

```bash
1. Parsing Functions: Recursive functions parse different components of tinyL:

    * program(): Parses the entire program

    * stmtlist(), morestmts(): Handle lists of statements

    * stmt(): Processes a single statement

    * assign(), read(), print(): Handle assignment, input, and output statements

    * expr(): Parses and evaluates arithmetic expressions

2. Utilities:

    * next_token(): Advances the input token

    * next_register(): Allocates a new virtual register

    * CodeGen(): Generates and writes intermediate instructions

3. Output Instructions:

    * Uses InstrUtils.h and Instr.h for defining and printing instructions like LOAD, STORE, ADD, SUB, etc.
```


## Requirements

```bash
- Compiler: C compiler such as GCC or any C compiler supporting standard C libraries

- Input File: A valid tinyL program

- Basic understanding of compiler design concepts

- Familiarity with tinyL language syntax (see examples in the code)
```


## File Output

```bash
- Compiler: C compiler such as GCC or any C compiler supporting standard C libraries

- Input File: A valid tinyL program

- Basic understanding of compiler design concepts

- Familiarity with tinyL language syntax (see examples in the code)
```
 

## License

This project is licensed under the MIT License. See the LICENSE file for details.


## Important Note

```bash
- The program requires tokens to strictly follow the tinyL grammar. Any deviation will result in an error

- The compiler generates error messages for invalid tokens or incorrect syntax

- The recursive descent parser ensures a structured and modular approach to parsing tinyL programs
```
