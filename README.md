# DSA01 - Assignment 2: Functions and Object-Oriented Concepts

**Course:** Object Oriented Programming with C++ / Data Structures and Algorithms (CO2)  
**Student Name:** Nirmal S  
**Register Number:** 192511249  
**Nature of Assignment:** Individual  
**Total Marks:** 50 (Bloom's Level: K5 – Evaluate)  
**GitHub Repository Link:** https://github.com/nirmal2308/DSA01-192511249-Assignment2  

---

## 1. System and Compiler Information

- **Operating System:** Linux (Ubuntu 24.04 LTS x86_64 via WSL)
- **Compiler:** `g++` (Ubuntu 15.2.0-16ubuntu1) 15.2.0
- **C++ Standard:** C++17 (`-std=c++17`)
- **Compilation Flags:** `-std=c++17 -Wall -Wextra -O2`

---

## 2. Directory Structure

```text
DSA01-192511249-Assignment2/
├── .gitignore
├── README.md
├── REPORT.md
├── VIVA_NOTES.md
├── Task01/
│   ├── task01.cpp
│   └── output.txt
├── Task02/
│   ├── task02.cpp
│   └── output.txt
├── Task03/
│   ├── task03.cpp
│   └── output.txt
├── Task04/
│   ├── task04.cpp
│   └── output.txt
├── Task05/
│   ├── task05.cpp
│   └── output.txt
├── Task06/
│   ├── task06.cpp
│   └── output.txt
└── Task07/
    ├── task07.cpp
    └── output.txt
```

---

## 3. Compilation and Execution Commands

Run the following commands from the repository root:

### Task 01: Call by Value, by Reference and by Pointer
```bash
g++ -std=c++17 -Wall -Wextra Task01/task01.cpp -o Task01/task01
./Task01/task01
```

### Task 02: Return by Reference and Its Dangers
```bash
g++ -std=c++17 -Wall -Wextra Task02/task02.cpp -o Task02/task02
./Task02/task02
```

### Task 03: Default Arguments and Function Overloading
```bash
g++ -std=c++17 -Wall -Wextra Task03/task03.cpp -o Task03/task03
./Task03/task03
```

### Task 04: Specifying a Class with an Array Inside It
```bash
g++ -std=c++17 -Wall -Wextra Task04/task04.cpp -o Task04/task04
./Task04/task04
```

### Task 05: Static Members and Arrays of Objects
```bash
g++ -std=c++17 -Wall -Wextra Task05/task05.cpp -o Task05/task05
./Task05/task05
```

### Task 06: Friend Functions and Inline Functions
```bash
g++ -std=c++17 -Wall -Wextra Task06/task06.cpp -o Task06/task06
./Task06/task06
```

### Task 07: Day-4 Design Challenge - Circular Ring Buffer Mini-Statement
```bash
g++ -std=c++17 -O2 -Wall -Wextra Task07/task07.cpp -o Task07/task07
./Task07/task07
```

---

## 4. Summary of Tasks and Key Findings

| Task | Topic | Key Findings & Evaluation |
| :--- | :--- | :--- |
| **Task 01** | Value, Reference, Pointer | Demonstrated that pass-by-value operates on stack copies leaving caller state intact, while reference and pointer enable direct in-place mutation. |
| **Task 02** | Return by Reference | Returning an lvalue reference allows direct moderation (`getHighestMark() += 2`), while returning reference to local variables triggers undefined behavior. Demonstrated vector reallocation invalidation. |
| **Task 03** | Overloading & Default Args | Resolved compiler ambiguity by restructuring default parameters from the right and separating types into `int`, `double`, and `Parcel`. |
| **Task 04** | Class with Array | Encapsulated 10-transaction buffer in `SavingsAccount`, showing linear shifting behavior on the 11th transaction. |
| **Task 05** | Static Members & Object Arrays | Managed shared capacity and seat allocation across `BusTicket` instances; verified state retention across nested function invocations. |
| **Task 06** | Friend & Inline Functions | Implemented symmetric binary comparison between private `Time` instances with zero abstraction penalty via inlining. |
| **Task 07** | Day-4 Design Challenge | Redesigned fixed-size shifting mini-statement into a dynamic circular ring buffer, achieving a $5\times$ speedup ($O(1)$ amortized insertion vs $O(k)$ shifts). |
