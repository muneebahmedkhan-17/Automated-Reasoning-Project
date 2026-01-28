# Automated-Reasoning-Project
Implementation of a decision procedure in C++ for Automated Reasoning, including parsing, congruence closure, and array constraint handling.

Overview of Project
Reads constraints from a text file (one per line), parses them into an AST, runs the solver, and prints SAT/UNSAT.

Files
- main.cpp: reads input, calls parser + solver, prints result
- parser.h / parser.cpp: tokenizer + parser, builds Term/Literal AST
- solver.h / solver.cpp: solver pipeline (preprocessing + reasoning) and SAT/UNSAT decision


Input Format
- One constraint per non-empty line.
- Supported forms:
    t1 = t2
    t1 != t2
    atom(t)
    !atom(t)
- Terms may be identifiers or function applications such as f(x,y).
- Lines starting with # or // are treated as comments and ignored.
- Input files may include comments describing the source of a test case.

Build Instructions (Windows / PowerShell, MinGW g++)
1) Compile the project:
   g++ -std=c++17 -O2 -Wall -Wextra main.cpp parser.cpp solver.cpp -o solver.exe

Run Instructions
- Run the solver with an input file:
   .\solver.exe input.txt

Example
Input file:
   // Simple sanity check
   a = a

Output:
   SAT

Clean rebuild (recommended after edits)
  Remove-Item .\solver.exe -ErrorAction SilentlyContinue
  g++ -std=c++17 -O2 -Wall -Wextra main.cpp parser.cpp solver.cpp -o solver.exe
