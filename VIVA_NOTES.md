# VIVA & CONCEPT GUIDE: FUNCTIONS AND OBJECT-ORIENTED CONCEPTS
**Student:** Nirmal S (Reg No: 192511249)  
**Perspective:** Python Master to C++ Beginner Bridge  
**Goal:** Crack the viva and confidently explain/modify any part of Assignment 2 on the spot.

---

## 1. PYTHON VS C++ "CHEAT SHEET" (YOUR MENTAL BRIDGE)

| Concept | Python Mental Model | C++ Reality in Assignment 2 | Why Faculty Cares |
| :--- | :--- | :--- | :--- |
| **Pass by Value** | Rebinding a name locally (`x = x - 10`) doesn't change caller immutable int. | Bits of variable are physically copied onto called function's stack frame. Modifications die on return. | Core of Task 01: Why `applyByValue` failed to deduct fee. |
| **Pass by Reference** | Mutable objects (lists/dicts) mutate in-place. | `long long& fee` binds an alias to caller's exact memory address. Zero copy overhead. | Core of Task 01: How `applyConcession` modifies caller fee directly. |
| **Pointers** | No pointer syntax; `id(obj)` gives memory address. | `long long* fee` holds explicit memory address; dereferenced via `*fee`. | Pointer arithmetic, nullability checks (`fee != nullptr`). |
| **Lvalues & Return by Ref** | Function call cannot be on left of assignment (`f() = 10` is SyntaxError). | Functions returning `int&` yield valid lvalues: `getHighestMark() += 2;` or `f() = 100;` is valid C++. | Core of Task 02: In-place moderation of array elements. |
| **Dangling Reference** | Objects stay alive until garbage collection collects them. | Stack variables are destroyed immediately when function exits. Returning reference to local is undefined behavior! | Trap question in Task 02. Compiler warns: `-Wreturn-local-addr`. |
| **Default Arguments** | `def f(x, y=5, z=10):` evaluated once at function definition. | Evaluated at each call site; must be placed strictly from the rightmost parameter. | Task 03: Resolving ambiguity in overloaded signatures. |
| **Static Class Members** | Class attributes (`Class.count`). | `static int issued;` shared across all instances, defined outside class in global scope. | Task 05: Class-wide ticket allocation and count tracking. |
| **Friend Functions** | No concept; private attributes only use name mangling. | `friend` grants a non-member function access to private members. Allows symmetric binary operators. | Task 06: `minutesBetween(Time a, Time b)`. |
| **Inlining** | Python bytecode is interpreted; no direct inline keyword. | `inline` instructs compiler to replace call with function body, eliminating call stack overhead. | Task 06: 10M calls benchmark under `-O0` vs `-O2`. |

---

## 2. TASK-BY-TASK VIVA CHEAT SHEET

### TASK 01: Value, Reference, Pointer (`Task01/task01.cpp`)
- **What it does:** Applies hostel fee concessions via value, reference, and pointer. Executes `change()`, `bigger()`, and `show()` prediction snippet.
- **Viva Answer:** *"Sir, pass-by-value copies the argument to the local stack frame, so mutations are discarded on return. Pass-by-reference binds an lvalue reference directly to the caller's storage, and pass-by-pointer passes the memory address, allowing in-place mutation."*
- **On-the-spot code change:** *"Change concession to 20% by pointer"*:
  `applyByPointer(&hostelFee, 20);`

---

### TASK 02: Return by Reference & Dangers (`Task02/task02.cpp`)
- **What it does:** Moderates highest mark via `getHighestMark(marks, n) += 2;`. Demonstrates dangling reference warning and vector reallocation invalidation.
- **Viva Answer:** *"Returning an lvalue reference allows the caller to use the function call on the left side of an assignment. However, returning a reference to a local variable creates a dangling reference because the activation frame is destroyed on return."*
- **Vector Trap:** *"Why do vector references become invalid?"*  
  $\rightarrow$ *"When a vector grows beyond its capacity, it reallocates a new memory buffer and deallocates the old one. Pointers and references to elements in the old buffer dangle. Using array index (`vec[i]`) avoids this because it references the active buffer."*

---

### TASK 03: Default Arguments & Overloading (`Task03/task03.cpp`)
- **What it does:** Resolves ambiguous courier charge function overloads and tests 6 calls including `charge(2)` and `charge(2.0f)`.
- **Viva Answer:** *"The original code failed because a call with one or two arguments matched multiple overloads with default arguments. We solved this by using default arguments from the right and overloading by distinct types (`int` grams, `double` kg, and `Parcel`)."*
- **Trap Question:** *"Why does `charge(2.0f)` call the double overload?"*  
  $\rightarrow$ *"Because standard conversion from float to double is preferred over float to int truncation."*

---

### TASK 04: Class with Array Inside (`Task04/task04.cpp`)
- **What it does:** Implements `SavingsAccount` with 10-transaction array. Shows shifting when 11th transaction arrives.
- **Viva Answer:** *"The transaction array is kept private to enforce data integrity so balance always matches transaction history. When the 11th transaction arrives, older elements shift left, which takes $O(k)$ time."*

---

### TASK 05: Static Members & Object Arrays (`Task05/task05.cpp`)
- **What it does:** Implements `BusTicket` with `static int issued` and `CAPACITY = 3`. Verifies `Token` output prediction `101 103 104 4`.
- **Viva Answer:** *"Static data members exist once for the entire class, not per instance. Static member functions can be called without an object, so they do not receive an implicit `this` pointer and cannot touch non-static members."*

---

### TASK 06: Friend Functions & Inlining (`Task06/task06.cpp`)
- **What it does:** Computes time difference and ordering using friend functions. Benchmarks 10M calls with and without inlining.
- **Viva Answer:** *"Friend functions are ideal for symmetric binary operations like time difference where neither object owns the other. Inlining eliminates call-stack overhead, achieving a $3.4\times$ speedup at 10M calls."*

---

### TASK 07: Day-4 Design Challenge (`Task07/task07.cpp`)
- **What it does:** Replaces linear array shifting ($O(k)$) with a dynamic circular ring buffer ($O(1)$ amortized insertion).
- **Viva Answer:** *"Sir, shifting 49 elements for every transaction in a 50-entry statement causes severe memory movement overhead. My circular ring buffer uses modulo arithmetic `(head + 1) % capacity` to achieve strictly $O(1)$ insertion, running $5\times$ faster in our 1,000,000 transaction benchmark."*
