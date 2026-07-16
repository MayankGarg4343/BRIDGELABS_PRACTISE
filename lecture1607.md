# .NET Internal Architecture

## Overall Execution Flow

```text
                 Source Code (.cs)
                       │
                       ▼
              C# Compiler (Roslyn)
                       │
                       ▼
            CIL / IL + Metadata
                       │
                       ▼
             Assembly (.dll/.exe)
                       │
                       ▼
                CLR (CoreCLR)
         ┌─────────────┼─────────────┐
         ▼             ▼             ▼
    Class Loader   JIT Compiler     GC
         │             │             │
         ▼             ▼             ▼
     Type System   Native Code    Memory
         │             │             │
         └────────────► Execution ◄──┘
                       │
                       ▼
        Operating System (Windows/Linux/macOS)
                       │
                       ▼
                   CPU + Memory
```

---

# High-Level .NET Architecture

```text
                    Your Application
                          │
─────────────────────────────────────────────────
     ASP.NET Core / MAUI / Console / WPF
─────────────────────────────────────────────────
          Base Class Library (BCL)
─────────────────────────────────────────────────
              CoreCLR Runtime
 GC | JIT | ThreadPool | Loader | Security
─────────────────────────────────────────────────
             Operating System
─────────────────────────────────────────────────
                 Hardware
```

---

# C# Compilation Pipeline

```text
Source Code (.cs)
      │
      ▼
Lexical Analysis
      │
      ▼
Tokens
      │
      ▼
Syntax Analysis
      │
      ▼
Syntax Tree (AST)
      │
      ▼
Semantic Analysis
      │
      ▼
Optimization
      │
      ▼
IL (CIL) Generation
```

---

# Assembly Structure

```text
Assembly (.dll/.exe)
├── IL (Intermediate Language)
├── Metadata
├── Manifest
├── Resources
└── Attributes
```

---

# CoreCLR Architecture

```text
                CoreCLR
┌─────────────────────────────────┐
│ Class Loader                    │
│ Type Loader                     │
│ Metadata System                 │
│ JIT Compiler                    │
│ Garbage Collector (GC)          │
│ ThreadPool                      │
│ Exception Engine                │
│ Security                        │
└─────────────────────────────────┘
```

---

# CoreCLR Internal Components

## 1. Class Loader

Responsible for:

- Loading assemblies
- Resolving dependencies
- Loading referenced DLLs
- Initializing assemblies

---

## 2. Type Loader

Responsible for:

- Loading types
- Building Method Tables
- Building EEClass structures
- Preparing runtime type information

---

## 3. Metadata System

Reads metadata stored inside assemblies.

Contains:

- Classes
- Interfaces
- Methods
- Fields
- Properties
- Events
- Generic Information
- Attributes

---

## 4. JIT Compiler

Converts IL into native machine code.

```text
IL Code
    │
    ▼
JIT Compiler
    │
    ▼
Native Machine Code
    │
    ▼
CPU Execution
```

Types of JIT:

- Normal JIT
- Tiered JIT
- ReadyToRun (R2R)
- Native AOT

---

## 5. Garbage Collector (GC)

Responsible for automatic memory management.

```text
Managed Heap

Gen 0
   │
   ▼
Gen 1
   │
   ▼
Gen 2

Large Object Heap (LOH)

Pinned Object Heap (POH)
```

Responsibilities:

- Allocate memory
- Free unused objects
- Compact memory
- Prevent memory leaks

---

## 6. ThreadPool

Manages worker threads.

```text
Tasks
   │
   ▼
ThreadPool Queue
   │
   ▼
Worker Threads
   │
   ▼
Execution
```

---

## 7. Exception Engine

Responsible for:

- Stack unwinding
- Finding catch blocks
- Executing finally blocks
- Throwing exceptions

---

## 8. Security

Provides:

- Code verification
- Type safety
- Memory safety
- Cryptography APIs
- Authentication support
- Authorization support

---

# Runtime Execution Flow

```text
C# Source Code
        │
        ▼
Roslyn Compiler
        │
        ▼
IL + Metadata
        │
        ▼
Assembly (.dll/.exe)
        │
        ▼
CLR Loads Assembly
        │
        ▼
Class Loader
        │
        ▼
Type Loader
        │
        ▼
Metadata Reader
        │
        ▼
JIT Compiler
        │
        ▼
Native Machine Code
        │
        ▼
CPU Executes Instructions
        │
        ▼
Objects Created on Managed Heap
        │
        ▼
Garbage Collector Reclaims Memory
```

---

# Memory Layout

```text
Process Memory

├── Stack
│
├── Managed Heap
│     ├── Gen0
│     ├── Gen1
│     ├── Gen2
│     ├── LOH
│     └── POH
│
├── Native Heap
│
├── Code Heap
│
└── Loader Heap
```

---

# Complete .NET Architecture

```text
Application
     │
     ▼
Framework (ASP.NET Core / MAUI / WPF / Console)
     │
     ▼
Base Class Library (BCL)
     │
     ▼
CoreCLR Runtime
     ├── Class Loader
     ├── Type Loader
     ├── Metadata System
     ├── JIT Compiler
     ├── Garbage Collector
     ├── ThreadPool
     ├── Exception Engine
     └── Security
     │
     ▼
Operating System
     │
     ▼
Hardware (CPU + RAM + Storage)
```