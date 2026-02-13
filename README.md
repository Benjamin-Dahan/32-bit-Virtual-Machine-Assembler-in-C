# 32-bit Virtual Machine & Assembler in C

![Language](https://img.shields.io/badge/Language-C-blue.svg) ![Type](https://img.shields.io/badge/Architecture-Von_Neumann_32--bit-red.svg)

## 📄 Abstract
This project is a complete implementation of a **32-bit Virtual Machine (VM)** and a **2-pass Assembler** developed from scratch in **C**. It simulates a Von Neumann architecture, handling the full **Fetch-Decode-Execute** cycle without relying on high-level abstractions.

## 🚀 Key Features
* **CPU Simulation:** Implements bitwise operations (masks, shifts) to decode instructions, handling arithmetic overflows and sign extensions manually[cite: 301, 372].
* **Memory Management:** Simulates a 64KB RAM with **Little Endian** addressing and robust segmentation fault detection[cite: 402, 561].
* **Assembler:** Converts Assembly language into 32-bit hexadecimal machine code using a 2-pass strategy (Label resolution + Instruction encoding)[cite: 104].
* **Robustness:** Strict error handling for memory access bounds and arithmetic overflows (Critical vs Standard)[cite: 177, 494].

## 📂 Project Structure
*Note: Source code filenames are in French following the original academic guidelines.*

* `main.c`: Entry point handling the Assembler translation and the VM execution loop.
* `Gestion_memoire.c`: Handles RAM simulation (64KB array), Little Endian loading, and boundary checks.
* `Conversion_Instruction_Hexa.c`: Converts assembly instructions into 32-bit binary/hex strings.
* `Structures_et_Fonctions_instructions.c`: Logic for the 2nd assembler pass (instruction parsing and encoding).
* `Structures_et_Fonctions_etiquettes.c`: Logic for the 1st assembler pass (label/symbol table management).
* `Fonctions_outils.c`: Low-level helpers (bitwise masks, string trimming, safe conversion).

## 🛠️ How to Run

### 1. Compilation
The project is split into modules. Compile everything using GCC:

```bash
gcc -Wall main.c Constantes.c Fonctions_outils.c Structures_et_Fonctions_etiquettes.c Structures_et_Fonctions_instructions.c Conversion_Instruction_Hexa.c Gestion_memoire.c -o simulateur
