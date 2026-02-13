# 32-bit Virtual Machine & Assembler in C

![Language](https://img.shields.io/badge/Language-C-blue.svg) ![Architecture](https://img.shields.io/badge/Architecture-Von_Neumann_32--bit-red.svg) ![Status](https://img.shields.io/badge/Status-Completed-green.svg)

## 📄 Abstract
This project is a complete design and implementation of a **32-bit Virtual Machine (VM)** and its associated **Assembler**, developed entirely from scratch in **C**. It simulates a Von Neumann architecture, handling the full **Fetch-Decode-Execute cycle** without relying on high-level abstractions.

The goal was to reconstruct computer logic using arithmetic operations, managing memory manually, and ensuring robust execution flow.

## 🚀 Key Features

### 🧠 CPU Simulation
* **Custom ALU:** Implementation of bitwise operations (masks, shifts) using modular arithmetic and integer division/multiplication to simulate hardware logic.
* **Cycle Management:** Full simulation of Fetch, Decode, and Execute stages.
* **Register Bank:** Management of 32 general-purpose registers ($R_0$ to $R_{31}$).

### 💾 Memory Management
* **Virtual RAM:** Simulation of a 64KB memory space (linear array).
* **Little Endian:** Handles byte-addressing and manual reconstruction of 32-bit words from 8-bit memory slots.
* **Safety:** Strict boundary checks to prevent segmentation faults during load/store operations.

### ⚙️ Assembler
* **Two-Pass Strategy:**
    1.  **Pass 1:** Collects labels and resolves addresses.
    2.  **Pass 2:** Parses instructions and encodes them into 32-bit hexadecimal machine code.
* **Overflow Handling:** Distinguishes between "Standard Overflow" (handled via modulo) and "Critical Overflow" (> 2,000,000,000) to ensure system stability.

## 📂 Project Structure

* **`main.c`**: Entry point. Orchestrates the assembly translation and the VM execution loop.
* **`Gestion_memoire.c`**: Handles the 64KB RAM simulation, Little Endian loading, and boundary checks.
* **`Conversion_Instruction_Hexa.c`**: Converts parsed assembly instructions into 32-bit binary and hexadecimal strings.
* **`Structures_et_Fonctions_instructions.c`**: Logic for the 2nd assembler pass (instruction parsing, opcode validation, encoding).
* **`Structures_et_Fonctions_etiquettes.c`**: Logic for the 1st assembler pass (symbol table management, label resolution).
* **`Fonctions_outils.c`**: Low-level helper functions (bitwise masks, string trimming, safe type conversion).
* **`Constantes.c`**: Defines global constants and configuration for the VM.

## 🛠️ How to Run

### 1. Compilation
The project is modular. You need to compile all source files together. Use the following `gcc` command:

```bash
gcc -Wall main.c Constantes.c Fonctions_outils.c Structures_et_Fonctions_etiquettes.c Structures_et_Fonctions_instructions.c Conversion_Instruction_Hexa.c Gestion_memoire.c -o simulateur
