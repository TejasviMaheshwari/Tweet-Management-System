# Tweet-Management-System
This repository implements a Tweet Management System using custom Singly and Doubly Linked Lists in C++. It features a console-based interface for inserting, deleting, searching, and traversing "tweets" with auto-generated IDs. Designed to demonstrate core data structures and pointer manipulation in a real-world scenario.

# 🐦 Tweet & Data Management System
## *Using Linked Lists in C++ — Singly & Doubly*

<div align="center">

![C++](https://img.shields.io/badge/Language-C%2B%2B-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![Data Structures](https://img.shields.io/badge/Topic-Data%20Structures-blueviolet?style=for-the-badge)
![Linked List](https://img.shields.io/badge/Structure-Linked%20List-orange?style=for-the-badge)
![OOP](https://img.shields.io/badge/Paradigm-OOP-green?style=for-the-badge)
![Console App](https://img.shields.io/badge/Type-Console%20Application-black?style=for-the-badge)
![Beginner Friendly](https://img.shields.io/badge/Level-Beginner%20Friendly-brightgreen?style=for-the-badge)

---

*A fully menu-driven, interactive C++ console application that simulates a Tweet Management System
using both Singly and Doubly Linked Lists — built with Object-Oriented Programming principles,
dynamic memory allocation, and real pointer manipulation.*

</div>

---

## 📋 Table of Contents

| # | Section |
|---|---------|
| 1 | [Project Overview](#-project-overview) |
| 2 | [Core Technical Concepts](#-core-technical-concepts) |
| 3 | [Features](#-features) |
| 4 | [Data Structure Explanation](#-data-structure-explanation) |
| 5 | [Project Architecture & Program Flow](#-project-architecture--program-flow) |
| 6 | [File Structure](#-file-structure) |
| 7 | [Detailed Operations Table](#-detailed-operations-table) |
| 8 | [Singly Linked List Operations](#-singly-linked-list-operations) |
| 9 | [Doubly Linked List Operations](#-doubly-linked-list-operations) |
| 10 | [Searching Mechanism](#-searching-mechanism) |
| 11 | [Traversal Mechanism](#-traversal-mechanism) |
| 12 | [Complexity Analysis](#-complexity-analysis) |
| 13 | [Memory Management](#-memory-management) |
| 14 | [Sample Console Output](#-sample-console-output) |
| 15 | [Compilation & Execution](#-compilation--execution) |
| 16 | [Technologies Used](#-technologies-used) |
| 17 | [Learning Outcomes](#-learning-outcomes) |
| 18 | [Future Enhancements](#-future-enhancements) |
| 19 | [Conclusion](#-conclusion) |

---

## 🚀 Project Overview

The **Tweet & Data Management System** is a comprehensive, fully interactive console-based application built in **C++** that demonstrates the real-world application of **Linked List data structures** through the lens of a simplified tweet management platform.

This project was engineered with the following objectives:

- To implement **Singly Linked List** and **Doubly Linked List** from scratch using raw C++ pointers and dynamic memory allocation
- To demonstrate **Object-Oriented Programming** through well-encapsulated classes (`NODE`, `singlylinklist`, `DNODE`, `Doublylinklist`)
- To build a complete **menu-driven interactive system** that allows users to insert, delete, search, traverse, and count tweet nodes without any external libraries
- To provide a clear, practical, and hands-on understanding of pointer manipulation, node linking, and memory management

Each **tweet node** in the system stores three pieces of data:

| Field | Type | Description |
|-------|------|-------------|
| `ID` / `TID` | `string` | Auto-generated Tweet ID (e.g., `TWEET1001`) |
| `NAME` / `UNAME` | `string` | Username of the tweet author |
| `TWEET` / `UTWEET` | `string` | The actual tweet message content |

The project is split across **three source files** — two header files implementing each linked list variant, and one unified main driver file — making the codebase modular, clean, and easy to navigate.

> 📁 **Terminal output screenshots for every operation described in this document are available in the `Tweet_LinkedList_Operation_Outputs` folder.**

---

## 🧠 Core Technical Concepts

```
┌─────────────────────────────────────────────────────────────────────┐
│                     KEY TECHNICAL PILLARS                           │
├──────────────────────┬──────────────────────────────────────────────┤
│  OOP                 │  Classes, Constructors, Encapsulation        │
│  Dynamic Memory      │  new / delete operators, Heap Allocation     │
│  Pointer Operations  │  NEXT, PREV, START, END pointer chaining     │
│  Data Structures     │  Singly LL & Doubly LL from scratch          │
│  Searching Algorithms│  Linear Search by ID and Username            │
│  Traversal Algorithms│  Forward (head→NULL) & Backward (tail→NULL) │
└──────────────────────┴──────────────────────────────────────────────┘
```

### 🔷 Object-Oriented Programming (OOP)

The system is architected using two pairs of classes:

- **`NODE`** — The fundamental building block of the singly linked list. Stores `ID`, `NAME`, `TWEET`, and a `NEXT` pointer.
- **`singlylinklist`** — Manages all singly linked list operations including `START`/`END` pointers, `CountNode`, `AutoTID`, and all menu-driven methods.
- **`DNODE`** — The doubly linked node, extending the concept with an additional `PREV` pointer alongside `NEXT`.
- **`Doublylinklist`** — Manages the full doubly linked list lifecycle with bidirectional traversal, four-pointer re-wiring during insertions/deletions.

Constructors initialize all pointers to `nullptr` and counters to their default values, ensuring a safe, predictable initial state.

### 🔷 Dynamic Memory Allocation

Every new tweet inserted into the list allocates memory on the **heap** at runtime:

```cpp
NODE *TEMP = new NODE(TID, UNAME, UTWEET);
```

This contrasts with stack allocation — nodes persist beyond the scope of any single function and live as long as the list holds a reference. Each deletion invokes `delete(TEMP)` to responsibly reclaim heap memory and prevent leaks.

### 🔷 Pointer Operations

The entire system operates through raw C++ pointer manipulation:

- `START` always points to the first (head) node
- `END` always points to the last (tail) node
- `NEXT` links each node to its successor
- `PREV` (doubly LL only) links each node back to its predecessor
- Insertion and deletion require carefully re-wiring these pointers to preserve list integrity

### 🔷 Searching Algorithms

The system employs **linear search** — traversing from `START` to `nullptr`, comparing each node's `ID` or `NAME`/`UNAME` field against the user's query. All matching nodes are printed, supporting multiple results per query (e.g., all tweets by the same username).

### 🔷 Traversal Algorithms

- **Forward Traversal**: Begins at `START`, follows `NEXT` pointers, prints nodes until `nullptr`
- **Backward Traversal** (Doubly LL only): Begins at `END`, follows `PREV` pointers back to `nullptr`

---

## ✨ Features

### 🟢 Singly Linked List Module
- ✅ Insert at Beginning, End, and any Position
- ✅ Delete from Beginning, End, and any Position
- ✅ Forward Traversal (Head → NULL)
- ✅ Search by Tweet ID
- ✅ Search by Username
- ✅ Count total nodes in the list
- ✅ Auto-incrementing Tweet ID (starting from `TWEET1001`)
- ✅ Interactive sub-menus with continue/go-back options

### 🔵 Doubly Linked List Module
- ✅ Insert at Beginning, End, and any Position
- ✅ Delete from Beginning, End, and any Position
- ✅ **Forward Traversal** (Head → NULL)
- ✅ **Backward Traversal** (Tail → NULL) — *exclusive to Doubly LL*
- ✅ Search by Tweet ID
- ✅ Search by Username
- ✅ Count total nodes in the list
- ✅ Four-pointer re-wiring for all insert/delete operations

### 🌐 System-Wide Features
- ✅ Fully menu-driven navigation across all modules
- ✅ Unified main menu switches between Singly and Doubly LL
- ✅ Graceful exit with a thank-you message
- ✅ Input validation and empty-list guards
- ✅ `system("cls")` screen clearing for a clean console UX
- ✅ Keyboard-driven navigation using `getch()` (no Enter key required)

---

## 📐 Data Structure Explanation

### Singly Linked List Node — `NODE`

```
┌───────────────────────────────────────────────┐
│                   NODE                        │
├──────────────┬────────────────────────────────┤
│   ID         │  "TWEET1001"                   │
│   NAME       │  "Tejasvi"                     │
│   TWEET      │  "My name is Tejasvi"          │
│   *NEXT      │  ──────────────────────►       │
└──────────────┴────────────────────────────────┘
```

Each `NODE` holds its data fields and a single forward-pointing `NEXT` pointer. Traversal can only go in one direction — forward.

### Doubly Linked List Node — `DNODE`

```
◄────────────────────────────────────────────────────────────►
│                        DNODE                               │
├──────────┬──────────────────────────────┬──────────────────┤
│  *PREV   │  ID | UNAME | TWEET          │  *NEXT           │
│ ◄────────│  "TWEET1001","Tejasvi","..."  │ ──────────►      │
└──────────┴──────────────────────────────┴──────────────────┘
```

`DNODE` adds a `PREV` pointer, enabling **bidirectional traversal** and more efficient deletion (no need to traverse from `START` to find the previous node — you already have `PREV`).

### Singly vs. Doubly — Side-by-Side

| Property | Singly Linked List | Doubly Linked List |
|----------|--------------------|-------------------|
| Pointers per node | 1 (`NEXT`) | 2 (`PREV` + `NEXT`) |
| Traversal direction | Forward only | Forward & Backward |
| Memory per node | Less | More |
| Delete from End | O(n) — must traverse | O(1) — use `END->PREV` |
| Insert at Position | Re-wire 2 pointers | Re-wire 4 pointers |
| Implementation complexity | Simpler | More sophisticated |

---

## 🏗️ Project Architecture & Program Flow

### Top-Level Application Flow

```
╔══════════════════════════════════════╗
║     Main Link List Menu              ║
║  1. Singly Link List                 ║
║  2. Doubly Link List                 ║
║  3. Exit                             ║
╚══════════════════════════════════════╝
         │                │
         ▼                ▼
  ┌──────────────┐  ┌──────────────────┐
  │ singlylinklist│  │  Doublylinklist  │
  │  MainMenu()  │  │   MainMenu()     │
  └──────┬───────┘  └────────┬─────────┘
         │                   │
    ┌────┴──────────┐   ┌────┴──────────┐
    │ 1. Insertion  │   │ 1. Insertion  │
    │ 2. Traversal  │   │ 2. Traversal  │
    │ 3. Search     │   │ 3. Search     │
    │ 4. Deletion   │   │ 4. Deletion   │
    │ 5. Count      │   │ 5. Count      │
    └───────────────┘   └───────────────┘
```

### Singly Linked List — Memory Layout

```
START                                               END
  │                                                   │
  ▼                                                   ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│ TWEET1001   │    │ TWEET1002   │    │ TWEET1003   │
│ Tejasvi     │───►│ Aarav       │───►│ Riya        │──► NULL
│ How are you?│    │ Hello World │    │ Good morning│
└─────────────┘    └─────────────┘    └─────────────┘
```

```
HEAD -> [ TWEET1001 , Tejasvi , How are you? ] -> [ TWEET1002 , Aarav , Hello World ] -> NULL
```

### Doubly Linked List — Memory Layout

```
START                                                              END
  │                                                                 │
  ▼                                                                 ▼
┌───────────────┐         ┌───────────────┐         ┌─────────────┐
│   TWEET1001   │         │   TWEET1002   │         │   TWEET1003 │
│   Tejasvi     │ ◄──────►│   Aarav       │◄───────►│   Riya      │
│   My name ... │         │   Doubly node │         │   Pos 2 ins │
└───────────────┘         └───────────────┘         └─────────────┘
       ▲                                                    │
       │                                                    ▼
      NULL                                                 NULL
```

```
NULL <- [ TWEET1001 , Tejasvi , MY name is Tejasvi ] <-> [ TWEET1002 , Aarav , Doubly node added ] -> NULL
```

### Insert at Position — Pointer Re-wiring (Doubly LL)

```
Before:
  PREV_NODE  ◄──────►  NEXT_NODE

After inserting NEW between them:
  PREV_NODE  ◄──────►  NEW_NODE  ◄──────►  NEXT_NODE

Pointer assignments:
  NEW->NEXT  = NEXT_NODE        (step 1)
  PREV->NEXT = NEW              (step 2)
  NEW->PREV  = PREV_NODE        (step 3)
  NEXT->PREV = NEW              (step 4)
```

---

## 📁 File Structure

```
📦 Tweet-LinkedList-Project
 ┣ 📄 singlyLinkList.hpp          — Singly Linked List: NODE class + singlylinklist class
 ┣ 📄 DoublyLinkList.hpp          — Doubly Linked List: DNODE class + Doublylinklist class
 ┣ 📄 MainLinkListFIle.cpp        — Main driver: unified entry point, top-level menu
 ┗ 📁 Tweet_LinkedList_Operation_Outputs
     ┣ 🖼️  Insert_Beginning_SLL.png
     ┣ 🖼️  Insert_End_SLL.png
     ┣ 🖼️  Insert_Position_SLL.png
     ┣ 🖼️  Traversal_SLL.png
     ┣ 🖼️  Search_TweetID_SLL.png
     ┣ 🖼️  Delete_Beginning_SLL.png
     ┣ 🖼️  Delete_End_SLL.png
     ┣ 🖼️  Delete_Position_SLL.png
     ┣ 🖼️  Insert_Beginning_DLL.png
     ┣ 🖼️  Insert_End_DLL.png
     ┣ 🖼️  Insert_Position_DLL.png
     ┣ 🖼️  Forward_Backward_Traversal_DLL.png
     ┣ 🖼️  Delete_Beginning_DLL.png
     ┣ 🖼️  Delete_End_DLL.png
     ┣ 🖼️  Delete_Position_DLL.png
     ┗ 🖼️  Search_Username_DLL.png
```

### File Responsibilities

| File | Class(es) | Responsibility |
|------|-----------|----------------|
| `singlyLinkList.hpp` | `NODE`, `singlylinklist` | Entire singly LL implementation — node definition, all insert/delete/search/traverse/count operations |
| `DoublyLinkList.hpp` | `DNODE`, `Doublylinklist` | Entire doubly LL implementation — bidirectional node, all operations including backward traversal |
| `MainLinkListFIle.cpp` | *(includes both headers)* | Entry point — instantiates both list objects, runs the top-level menu loop, handles clean program exit |

---

## 📊 Detailed Operations Table

| # | Operation | Module | Description | Key Pointer Concept |
|---|-----------|--------|-------------|---------------------|
| 1 | Insert at Beginning | SLL & DLL | New node placed before current `START`; `START` updated | `TEMP->NEXT = START; START = TEMP` |
| 2 | Insert at End | SLL & DLL | New node appended after `END`; `END` updated | `END->NEXT = TEMP; END = TEMP` |
| 3 | Insert at Position | SLL & DLL | New node spliced at user-specified index | Traverse to pos-1, re-wire `NEXT` (+ `PREV` for DLL) |
| 4 | Delete from Beginning | SLL & DLL | `START` moved to `START->NEXT`; old head freed | `START = TEMP->NEXT; delete(TEMP)` |
| 5 | Delete from End | SLL & DLL | Traverse to second-last; its `NEXT` set to `nullptr` | `END->PREV->NEXT = nullptr; END = END->PREV` |
| 6 | Delete from Position | SLL & DLL | Bypass target node; re-wire surrounding nodes; free target | `PREV->NEXT = TARGET->NEXT; delete(TARGET)` |
| 7 | Forward Traversal | SLL & DLL | Walk `START` → `nullptr`, printing each node | `TEMP = TEMP->NEXT` |
| 8 | Backward Traversal | DLL only | Walk `END` → `nullptr`, printing each node in reverse | `TEMP = TEMP->PREV` |
| 9 | Search by Tweet ID | SLL & DLL | Linear scan; match `ID == "TWEET" + query` | Increment counter per match; report "Not Found" if 0 |
| 10 | Search by Username | SLL & DLL | Linear scan; match `NAME/UNAME == query` | Supports multiple matches per username |
| 11 | Count Nodes | SLL & DLL | Display the value of `CountNode` | Maintained automatically on every insert/delete |

---

## 🔗 Singly Linked List Operations

The singly linked list is defined in `singlyLinkList.hpp` and provides the core, forward-only linked list experience. Below is a deep-dive into each operation.

---

### 1️⃣ Insert at Beginning

**Mechanism:** A new `NODE` is created with `new NODE(TID, UNAME, UTWEET)`. Its `NEXT` pointer is set to the current `START`, making the existing list follow the new node. `START` is then updated to point to the new node. `CountNode` is incremented and `AutoTID` is advanced.

```cpp
TEMP->NEXT = START;
START = TEMP;
CountNode++;
AutoTID++;
```

**Visual Transition:**

```
Before:
  START → [TWEET1001, Tejasvi, How are you?] → NULL

After Insert at Beginning (TWEET1000, NewUser, Hello):
  START → [TWEET1000, NewUser, Hello] → [TWEET1001, Tejasvi, How are you?] → NULL
```

**Edge Case:** If the list is empty (`START == nullptr`), both `START` and `END` are assigned to the new node.

> 📸 Screenshot of this operation in action is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> ==========Insertion Opertaion===========
> 1.Insert at Beggining
> 2.Insert at End
> 3.Insert at given Position
> ...
> --------Insertion at Beggining--------
> Enter TID :-TWEET1001
> Enter User Name :- Tejasvi
> Enter Tweet :- MY name is Tejasvi
>
> Node Inserted at Beginning Successfully...
> ```

---

### 2️⃣ Insert at End

**Mechanism:** A new `NODE` is created. The current `END` node's `NEXT` pointer is set to the new node, and `END` is updated to the new node. The new node's `NEXT` is already `nullptr` (set in the constructor).

```cpp
END->NEXT = TEMP;
END = TEMP;
CountNode++;
AutoTID++;
```

**Visual Transition:**

```
Before:
  START → [TWEET1001, Tejasvi, ...] → NULL
                                END ↑

After Insert at End (TWEET1002, Aarav, Hello World):
  START → [TWEET1001, Tejasvi, ...] → [TWEET1002, Aarav, Hello World] → NULL
                                                                  END ↑
```

> 📸 Screenshot of this operation in action is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> --------Insertion at End--------
> Enter TID :-TWEET1002
> Enter User Name :- Aarav
> Enter Tweet :- Hello World
>
> Node Inserted at End Successfully...
> ```

---

### 3️⃣ Insert at Position

**Mechanism:** The user specifies a position (between 0 and `CountNode`). The algorithm traverses to the node at `position - 1`, then splices the new node in between using pointer re-wiring.

```cpp
NODE *TEMP1 = START;
for(i = 2; i < pos; i++) {
    TEMP1 = TEMP1->NEXT;
}
TEMP->NEXT = TEMP1->NEXT;
TEMP1->NEXT = TEMP;
```

> 📸 Screenshot of this operation in action is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> --------Insertion at given Position--------
> Total Number of Nodes Are -- 0
> Enter Position Between 0 and 0- 0
> Enter TID :-TWEET1001
> Enter User Name :- Tejasvi
> Enter Tweet :- How are you?
>
> Node Inserted at Position Successfully...
> ```

---

### 4️⃣ Delete from Beginning

**Mechanism:** A temporary pointer `TEMP` saves the current `START`. `START` is advanced to `TEMP->NEXT`, orphaning the original head. The orphaned node is then freed with `delete(TEMP)` to release heap memory.

```cpp
TEMP = START;
START = TEMP->NEXT;
CountNode--;
delete(TEMP);
```

**Edge Case:** If there is only one node (`START->NEXT == nullptr`), both `START` and `END` are set to `nullptr` before deleting.

> 📸 Screenshot of this operation in action is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> --------Delete from Beggining--------
>
> Node Deleted Successfully...
> ```

---

### 5️⃣ Delete from End

**Mechanism:** The algorithm traverses from `START` until `TEMP->NEXT == END`, reaching the second-to-last node. Its `NEXT` is set to `nullptr`, the old `END` is freed, and `END` is updated to this node.

```cpp
TEMP = START;
while(TEMP->NEXT != END) {
    TEMP = TEMP->NEXT;
}
NODE *TEMP1 = END;
TEMP->NEXT = nullptr;
END = TEMP;
delete(TEMP1);
```

> 📸 Screenshot of this operation is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> --------Delete from End--------
>
> Node Deleted Successfully...
> ```

---

### 6️⃣ Delete from Position

**Mechanism:** Traverse to the node just before the target position. Bypass the target by wiring the predecessor's `NEXT` directly to the target's `NEXT`. Free the target node.

```cpp
for(i = 2; i < pos; i++) { TEMP = TEMP->NEXT; }
NODE *TEMP1 = TEMP->NEXT;
TEMP->NEXT = TEMP1->NEXT;
delete(TEMP1);
```

> 📸 Screenshot of this operation is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> --------Delete from given Position--------
> Enter Position Between 1 and 1- 1
>
> Node Deleted Successfully...
> ```

---

## 🔄 Doubly Linked List Operations

Defined in `DoublyLinkList.hpp`, the doubly linked list extends the singly variant by adding a `PREV` pointer to every `DNODE`. This enables backward traversal and O(1) deletion from the end.

---

### 9️⃣ Insert at Beginning (Doubly LL)

**Mechanism:** The new node's `NEXT` is set to the current `START`. The old `START`'s `PREV` is then pointed back to the new node, before `START` is updated.

```cpp
TEMP->NEXT = START;
START->PREV = TEMP;
START = TEMP;
```

> 📸 Screenshot of this operation is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> ============Insertion Opertaion============
> --------Insertion at Beggining--------
> Enter TID :-TWEET1001
> Enter User Name :- Tejasvi
> Enter Tweet :- MY name is Tejasvi
>
> Node Inserted at Beginning Successfully...
> ```

---

### 🔟 Insert at End (Doubly LL)

**Mechanism:** The current `END` node's `NEXT` is pointed to the new node, and the new node's `PREV` is pointed back to `END`. `END` is then updated to the new node.

```cpp
END->NEXT = TEMP;
TEMP->PREV = END;
END = TEMP;
```

> 📸 Screenshot of this operation is available in `Tweet_LinkedList_Operation_Outputs`.

---

### 1️⃣1️⃣ Insert at Position (Doubly LL)

**Mechanism:** The most complex insertion — four pointers must be re-wired correctly to maintain bidirectional integrity:

```cpp
TEMP->NEXT = TEMP1->NEXT;    // Step 1: new node points forward
TEMP1->NEXT = TEMP;           // Step 2: predecessor points to new node
TEMP->PREV = TEMP1;           // Step 3: new node points back to predecessor
TEMP->NEXT->PREV = TEMP;      // Step 4: successor points back to new node
```

**Pointer Re-wiring Diagram:**

```
Before:
  [A] ◄──────────────────► [B]

After inserting [NEW] between A and B:
  [A] ◄──────► [NEW] ◄──────► [B]

Step 1: NEW->NEXT  = B
Step 2: A->NEXT    = NEW
Step 3: NEW->PREV  = A
Step 4: B->PREV    = NEW
```

> 📸 Screenshot of this operation is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> ---------Insertion at given Position---------
> Total Number of Nodes Are -- 1
> Enter Position Between 1 and 2- 2
> Enter TID :-TWEET1003
> Enter User Name :- Riya
> Enter Tweet :- Inserted at pos 2
>
> Node Inserted at Position Successfully...
> ```

---

### 1️⃣2️⃣ Delete from Beginning (Doubly LL)

```cpp
TEMP = START;
START = TEMP->NEXT;
START->PREV = nullptr;
delete(TEMP);
```

After moving `START` forward, the new head's `PREV` is set to `nullptr`, severing the backward link to the deleted node.

> 📸 Screenshot available in `Tweet_LinkedList_Operation_Outputs`.

---

### 1️⃣3️⃣ Delete from End (Doubly LL)

Doubly LL makes this O(1) — no full traversal needed:

```cpp
TEMP = END;
END = END->PREV;
END->NEXT = nullptr;
delete(TEMP);
```

> 📸 Screenshot available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> ---------Delete from End---------
>
> Node Deleted Successfully...
> ```

---

### 1️⃣4️⃣ Delete from Position (Doubly LL)

The most sophisticated deletion — both the predecessor and successor must update their pointers:

```cpp
TEMP->PREV->NEXT = TEMP->NEXT;
TEMP->NEXT->PREV = TEMP->PREV;
delete(TEMP);
```

> 📸 Screenshot available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output:**
> ```
> ---------Delete from given Position---------
> Enter Position Between 1 and 2- 2
>
> Node Deleted Successfully...
> ```

---

## 🔍 Searching Mechanism

Both linked list modules implement **linear search** — the only viable strategy for unsorted, non-indexed linked lists. The search traverses the entire list from `START` to `nullptr`, accumulating matches.

### Search by Tweet ID

The user enters a numeric suffix (e.g., `1001`). The system prepends `"TWEET"` to form the full ID and compares against each node's `ID` field:

```cpp
if(TEMP->ID == ("TWEET" + TweetID)) {
    // print match
    counter++;
}
```

> 📸 Screenshot of Tweet ID search is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output (Singly LL):**
> ```
> ============Search Module============
> 1.Search by Tweet ID
> 2.Search by User Name
> ...
> ---------Search Tweet by Tweet ID---------
> Enter Tweet ID to find the Tweet -- 1001
>
> [ TWEET1001 , Tejasvi , How are you? ]
> ```

### Search by Username

Traverses the full list and prints all tweets belonging to the given username — useful for viewing a specific user's tweet history:

```cpp
if(TEMP->NAME == uname) {
    // print match
    counter++;
}
```

> 📸 Screenshot of Username search (Doubly LL) is available in `Tweet_LinkedList_Operation_Outputs`.
>
> **Actual Console Output (Doubly LL):**
> ```
> ==========Search Module==========
> --------Search Tweet by User Name--------
> Enter user Name to find the Tweet -- Tejasvi
>
> Head -> [ TWEET1001 , Tejasvi , MY name is Tejasvi ]
> ```

### Search Result Handling

| Scenario | System Response |
|----------|-----------------|
| One match found | Prints the matching node |
| Multiple matches | Prints all matching nodes sequentially |
| No match found | Prints "No Tweet Found" |
| Empty list | Prints "Link List is Empty..." |

---

## 🔁 Traversal Mechanism

### Forward Traversal (Both SLL and DLL)

Starting at `START`, the pointer walks forward through `NEXT` links, printing each node until `nullptr`:

```
HEAD -> [ TWEET1001 , Tejasvi , How are you? ] -> Null
```

```cpp
DNODE *TEMP = START;
while(TEMP != nullptr) {
    cout << "[ " << TEMP->ID << " , " << TEMP->UNAME << " , " << TEMP->TWEET << " ] -> ";
    TEMP = TEMP->NEXT;
}
cout << "Null";
```

### Backward Traversal (DLL Exclusive)

Starting at `END`, the pointer walks backward through `PREV` links:

```
NULL <- [ TWEET1001 , Tejasvi , MY name is Tejasvi ] -> Null
```

```cpp
DNODE *TEMP = END;
while(TEMP != nullptr) {
    cout << "[ " << TEMP->ID << " , " << TEMP->UNAME << " , " << TEMP->TWEET << " ] -> ";
    TEMP = TEMP->PREV;
}
cout << "Null";
```

The doubly linked list's traversal module presents a dedicated sub-menu:

```
==========Traversal Module==========
1.Forward Traversal
2.Backward Traversal
3.Main Menu
4.Exit
```

> 📸 Both traversal outputs are captured in `Tweet_LinkedList_Operation_Outputs`.

---

## ⏱️ Complexity Analysis

### Time Complexity

| Operation | Singly Linked List | Doubly Linked List |
|-----------|-------------------|-------------------|
| Insert at Beginning | O(1) | O(1) |
| Insert at End | O(1) *(with END pointer)* | O(1) *(with END pointer)* |
| Insert at Position | O(n) | O(n) |
| Delete from Beginning | O(1) | O(1) |
| Delete from End | O(n) *(traverse to find prev)* | O(1) *(use PREV pointer)* |
| Delete from Position | O(n) | O(n) |
| Forward Traversal | O(n) | O(n) |
| Backward Traversal | ❌ Not supported | O(n) |
| Search by ID | O(n) | O(n) |
| Search by Username | O(n) | O(n) |
| Count Nodes | O(1) *(maintained variable)* | O(1) *(maintained variable)* |

### Space Complexity

| List Type | Per Node | Notes |
|-----------|----------|-------|
| Singly LL | `sizeof(string) * 3 + sizeof(NODE*)` | One pointer per node |
| Doubly LL | `sizeof(string) * 3 + sizeof(DNODE*) * 2` | Two pointers per node — marginally more memory |

> **Key Insight:** The Doubly Linked List's extra `PREV` pointer costs a small amount of additional memory per node but pays dividends in O(1) deletion from the end, eliminating the O(n) traversal required by the Singly LL.

---

## 🧹 Memory Management

This project manages memory manually — one of the most important and educational aspects of the implementation.

### Allocation

Every `InsertNode()` call dynamically allocates memory on the heap:

```cpp
NODE *TEMP = new NODE(TID, UNAME, UTWEET);
if (TEMP == nullptr) {
    cout << "Insufficient Memory\n";
    return 0;
}
```

The `nullptr` check acts as a safeguard — if the system cannot allocate memory, the operation is aborted gracefully rather than crashing.

### Deallocation

Every `DeleteNode()` call explicitly frees the removed node:

```cpp
delete(TEMP);
```

Without this, each deletion would create a **memory leak** — the node's heap memory would remain allocated but inaccessible, consuming system resources until the program terminates.

### Object Lifecycle

```
Program Start
     │
     ▼
singlylinklist sl; ──► Constructor: START=nullptr, END=nullptr, CountNode=0, AutoTID=1001
Doublylinklist dl; ──► Constructor: START=nullptr, END=nullptr, CountNode=0, AutoTID=1001
     │
     ▼
User Inserts Nodes ──► new NODE(...) / new DNODE(...) — heap allocation
     │
     ▼
User Deletes Nodes ──► delete(TEMP) — heap deallocation
     │
     ▼
Program Exit ──► Any remaining nodes leak (future enhancement: destructor cleanup)
```

> **Note for Future Enhancement:** Adding destructors (`~singlylinklist()`, `~Doublylinklist()`) that traverse and free all remaining nodes would make this production-grade.

---

## 🖥️ Sample Console Output

All terminal screenshots below are captured directly from the running program and are stored in their full resolution in the **`Tweet_LinkedList_Operation_Outputs`** folder.

---

### 📌 Main Menu

```
==============Main Link List Menu==============
1.Singly Link List
2.Doubly Link List
3.Exit
```

---

### 📌 Singly LL — Main Operations Menu

```
==============Singly LinkList Operations==============
1.Insertion Operation
2.Traversal Operation
3.Search Operation
4.Delete Operation
5.Count Node
6.Go To Main Link List Menu

Choose one of Them --
```

---

### 📌 Insert at Beginning — Singly LL

```
==========Insertion Opertaion===========
1.Insert at Beggining
2.Insert at End
3.Insert at given Position
4.Go to Main Menu
5.Exit
Choose one of Them -- 1

--------Insertion at Beggining--------
Enter TID :-TWEET1001
Enter User Name :- Tejasvi
Enter Tweet :- MY name is Tejasvi

Node Inserted at Beginning Successfully...

Do you want to --
1.Continue the Same
2.Go to Previous Menu
3.Go to Main Menu
4.Exit
```

> 📸 Full screenshot available in `Tweet_LinkedList_Operation_Outputs`

---

### 📌 Traversal — Singly LL

```
--------Link List--------
Head -> [ TWEET1001 , Tejasvi , How are you? ] -> Null

Do you want to --
1.Continue the Same
2.Go to Main Menu
3.Exit
```

> 📸 Full screenshot available in `Tweet_LinkedList_Operation_Outputs`

---

### 📌 Search by Tweet ID — Singly LL

```
============Search Module============
1.Search by Tweet ID
2.Search by User Name
3.Main Menu
4.Exit
Choose one of Them -- 1

---------Search Tweet by Tweet ID---------
Enter Tweet ID to find the Tweet -- 1001

[ TWEET1001 , Tejasvi , How are you? ]

Do you want to --
1.Continue the Same
2.Go to Main Menu
3.Exit
```

> 📸 Full screenshot available in `Tweet_LinkedList_Operation_Outputs`

---

### 📌 Count Nodes

```
==========Count Node Module==========

Total Number of Nodes -- 1 Available Nodes

Do you want to --
1.Continue the Same
2.Go to Main Menu
3.Exit
```

> 📸 Full screenshot available in `Tweet_LinkedList_Operation_Outputs`

---

### 📌 Forward & Backward Traversal — Doubly LL

```
==========Traversal Module==========
1.Forward Traversal
2.Backward Traversal
3.Main Menu
4.Exit

---------Link List---------

NULL <- [ TWEET1001 , Tejasvi , MY name is Tejasvi ] -> Null

---------Reverse Link List---------

NULL <- [ TWEET1001 , Tejasvi , MY name is Tejasvi ] -> Null

Do you want to --
1.Continue the Same
2.Go to Main Menu
3.Exit
```

> 📸 Full screenshot available in `Tweet_LinkedList_Operation_Outputs`

---

### 📌 Search by Username — Doubly LL

```
==========Search Module==========
1.Search by Tweet ID
2.Search by User Name
3.Main Menu
4.Exit
Choose one of Them -- 2

--------Search Tweet by User Name--------
Enter user Name to find the Tweet -- Tejasvi

Head -> [ TWEET1001 , Tejasvi , MY name is Tejasvi ]

Do you want to --
1.Continue the Same
2.Go to Main Menu
3.Exit
```

> 📸 Full screenshot available in `Tweet_LinkedList_Operation_Outputs`

---

## ⚙️ Compilation & Execution

### Prerequisites

| Requirement | Details |
|-------------|---------|
| **Compiler** | `g++` (GCC) — version 7.0 or higher recommended |
| **OS** | Windows (required for `conio.h` and `getch()`) |
| **Standard** | C++11 or higher |
| **IDE** | Code::Blocks, Dev-C++, Visual Studio, or any GCC-compatible IDE |

> ⚠️ **Platform Note:** This project uses `#include <conio.h>` and `getch()` — a Windows-specific header. It will **not** compile on Linux or macOS without substituting `getch()` with a POSIX alternative (e.g., `getchar()` after configuring raw terminal mode).

---

### Step 1 — Clone or Download

```bash
# Clone the repository
git clone https://github.com/yourusername/tweet-linkedlist-cpp.git

# Navigate into the project directory
cd tweet-linkedlist-cpp
```

---

### Step 2 — Verify File Structure

```bash
ls
# Expected output:
# singlyLinkList.hpp   DoublyLinkList.hpp   MainLinkListFIle.cpp
```

---

### Step 3 — Compile

```bash
g++ MainLinkListFIle.cpp -o TweetManager
```

Or with explicit C++ standard:

```bash
g++ -std=c++11 MainLinkListFIle.cpp -o TweetManager
```

> **Note:** The header files (`singlyLinkList.hpp`, `DoublyLinkList.hpp`) are automatically included by `MainLinkListFIle.cpp` via `#include` directives. You do not compile them separately.

---

### Step 4 — Run

```bash
# On Windows
TweetManager.exe

# On Windows via MinGW / Git Bash
./TweetManager
```

---

### Step 5 — Navigate the Menus

Once the program launches:

```
==============Main Link List Menu==============
1.Singly Link List
2.Doubly Link List
3.Exit
```

Press **`1`** or **`2`** (no Enter key required — `getch()` reads single keystrokes instantly). Navigate through sub-menus the same way.

---

### Quick Reference — All Commands

```bash
# Full compile and run (one-liner)
g++ MainLinkListFIle.cpp -o TweetManager && ./TweetManager

# Compile with warnings enabled (recommended for development)
g++ -Wall -Wextra -std=c++11 MainLinkListFIle.cpp -o TweetManager
```

---

## 🛠️ Technologies Used

| Technology | Version | Role |
|------------|---------|------|
| **C++** | C++11 / C++14 | Core programming language |
| **`<iostream>`** | Standard | Console input/output (`cin`, `cout`) |
| **`<string>`** | Standard | String data type for tweet fields |
| **`<conio.h>`** | Windows | `getch()` for single-keystroke menu navigation |
| **GCC / g++** | 7.0+ | Compilation |
| **`new` / `delete`** | C++ Built-in | Dynamic heap memory management |
| **Raw Pointers** | C++ Built-in | Node linking, list traversal |

---

## 🎓 Learning Outcomes

This project is designed to cement the following skills for Computer Science students:

### 📌 Data Structures Mastery
- Understand the conceptual and implementation differences between **Singly** and **Doubly Linked Lists**
- Appreciate when each structure is appropriate — and why the extra `PREV` pointer in DLL is worth the memory cost for bidirectional access

### 📌 Pointer Fluency
- Write and reason about complex pointer re-wiring during insertions and deletions
- Understand that pointer bugs (dangling pointers, lost references) are silent killers — this project forces you to handle every case explicitly

### 📌 Dynamic Memory Management
- Use `new` and `delete` responsibly
- Understand heap vs. stack allocation and the consequences of memory leaks

### 📌 OOP Design
- Encapsulate node data and list operations inside cohesive classes
- See how constructors establish safe initial state, and how methods maintain list invariants

### 📌 Algorithm Design
- Implement linear search from scratch and understand its O(n) implications
- Design traversal loops that correctly handle empty lists, single-node lists, and multi-node lists

### 📌 Software Engineering Practices
- Organize code into header files and a main driver — modular design
- Build complete user-facing menus with input validation and graceful error messages
- Maintain auxiliary state (`CountNode`, `AutoTID`, `END` pointer) to avoid expensive recomputation

---

## 🚀 Future Enhancements

| # | Enhancement | Description | Benefit |
|---|-------------|-------------|---------|
| 1 | **File Handling** | Save and load tweet records to/from `.txt` or `.csv` files using `<fstream>` | Persistent data across program sessions |
| 2 | **Database Integration** | Connect to SQLite or MySQL to store tweet nodes in a relational database | Scalable, queryable storage |
| 3 | **Graphical User Interface** | Port to Qt or SFML for a visual GUI with list visualization | Dramatically improved UX |
| 4 | **STL Conversion** | Replace custom linked list with `std::list<>` or `std::forward_list<>` | Production-standard, iterator-compatible code |
| 5 | **Hashing / Indexing** | Add a `std::unordered_map<string, NODE*>` for O(1) Tweet ID lookups | Near-instant search instead of O(n) linear scan |
| 6 | **Undo / Redo System** | Use a stack of operation records to support undo/redo of insert and delete | Professional-grade data management |
| 7 | **Destructor Cleanup** | Add `~singlylinklist()` and `~Doublylinklist()` that free all remaining nodes | Eliminate memory leaks on program exit |
| 8 | **Sorting** | Implement sort-by-TweetID or sort-by-Username using merge sort on the linked list | Ordered traversal and better search efficiency |
| 9 | **Cross-Platform Support** | Replace `conio.h` / `getch()` with POSIX alternatives for Linux/macOS | Broader compiler and OS compatibility |
| 10 | **Multi-user Mode** | Support multiple user accounts, each with their own linked list of tweets | Realistic social-media simulation |

---

## 🏁 Conclusion

The **Tweet & Data Management System** is far more than a college practical submission — it is a comprehensive, hands-on exploration of two of the most fundamental data structures in Computer Science.

By building both a **Singly Linked List** and a **Doubly Linked List** entirely from scratch in C++ — without any STL containers or external libraries — this project delivers a genuine deep-dive into:

- How memory is allocated and reclaimed dynamically at runtime
- How pointer chains create and dissolve relationships between nodes
- How bidirectionality (the `PREV` pointer) unlocks new algorithmic possibilities like backward traversal and O(1) tail deletion
- How a fully interactive, menu-driven console application can be architectured cleanly across multiple files

Every operation — from the subtle four-pointer re-wiring of a mid-list doubly linked insertion, to the careful null-check guards on every deletion — has been implemented deliberately and documented thoroughly.

> 📁 **All terminal outputs and screenshots demonstrating every operation described in this README are available in the `Tweet_LinkedList_Operation_Outputs` folder.** Refer to them alongside this documentation for a complete picture of the system's behavior.

This project stands as a strong portfolio piece demonstrating core Computer Science fundamentals, C++ programming proficiency, and the discipline to engineer clean, readable, well-organized code.

---

<div align="center">

**Built with 💙 in C++ · Data Structures · OOP · Pointer Mastery**

*If you found this project useful, consider giving it a ⭐ on GitHub!*

---

![C++](https://img.shields.io/badge/C%2B%2B-Tweet%20Manager-00599C?style=flat-square&logo=cplusplus)
![Made With Love](https://img.shields.io/badge/Made%20with-💙-blue?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

</div>
