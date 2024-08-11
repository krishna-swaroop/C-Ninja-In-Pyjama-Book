# Proofreading Report

## Book Title: _C Ninja, In Pyjama_
### Author: _Piyush Itankar_
### Date: _11th August 2024_

## Error Categories
- **Typo**: Spelling mistakes, repeated words, etc.
- **Grammar**: Incorrect sentence structure, verb tenses, etc.
- **Punctuation**: Missing or incorrect punctuation marks.
- **Formatting**: Inconsistent or incorrect formatting.
- **Fact-Check**: Errors in factual information.
- **Suggestion**: Rewording or other suggestions for improvement.

## Table of Contents
- [Letter to the Reader](#letter-to-the-reader)
  - [Why this book?](#why-this-book)
  - [Embedded C doesn't exist!](#embedded-c-doesnt-exist)
  - [Who this is for?](#who-this-is-for)
  - [Approach](#approach)
  - [Why emulator?](#why-emulator)
  - [Why RISC-V architecture?](#why-risc-v-architecture)
  - [Sharing the book](#sharing-the-book)
  - [Community and resources](#community-and-resources)
  - [Meet the Crew](#meet-the-crew)
    - [Rajat Batra](#rajat-batra)
    - [Dev Bishnoi](#dev-bishnoi)
    - [Piyush Itankar](#piyush-itankar)
    - [Mahmad Bharmal](#mahmad-bharmal)
    - [Wasim Akram](#wasim-akram)
  - [Providing feedback](#providing-feedback)

- [Mental Models](#mental-models)
  - [C: History and Relevance](#c-history-and-relevance)
    - [Origins of C](#origins-of-c)
    - [Influence](#influence)
    - [Relevance](#relevance)
    - [Computers in 1970s](#computers-in-1970s)
  - [Computer System Model](#computer-system-model)
    - [Load-Store model](#load-store-model)
    - [Storage, Data and Instructions](#storage-data-and-instructions)
    - [Instructions](#instructions)
    - [Summary](#summary)
  - [Storage Models](#storage-models)
    - [Ways to store a bit](#ways-to-store-a-bit)
      - [Feedback based](#feedback-based)
      - [Trapping Charge](#trapping-charge)
      - [Bit, Register and Register file](#bit-register-and-register-file)
    - [Memory](#memory)
    - [Summary](#summary-1)
  - [CPU Model](#cpu-model)
    - [Abstraction: Ignoring the details](#abstraction-ignoring-the-details)
    - [The Programmer’s Model](#the-programmers-model)
    - [Registers and Buses](#registers-and-buses)
    - [Interrupts and Buses](#interrupts-and-buses)
    - [Summary](#summary-2)
  - [Instruction Set (RISC-V)](#instruction-set-risc-v)
    - [Encoding and machine code](#encoding-and-machine-code)
    - [Types of Instructions](#types-of-instructions)
      - [Encoding](#encoding)
    - [Hello, Assembler](#hello-assembler)
    - [Instruction Execution](#instruction-execution)
    - [Summary](#summary-3)
    - [Try it out!](#try-it-out)

  - [Lab Setup](#lab-setup)
    - [Docker](#docker)
      - [Installing Docker](#installing-docker)
      - [Docker dashboard](#docker-dashboard)
    - [Creating Image and Container](#creating-image-and-container)
    - [Launch setup](#launch-setup)
    - [Launching c-ninja](#launching-c-ninja)
    - [Setting up VS-Code](#setting-up-vs-code)
      - [Install VS-Code](#install-vs-code)
      - [Install Extensions and Connect](#install-extensions-and-connect)
    - [What is in Docker image?](#what-is-in-docker-image)

- [Assembly](#assembly)
  - [Text to 0s and 1s](#text-to-0s-and-1s)
    - [RISC-V Assembly Instructions](#risc-v-assembly-instructions)
    - [Converting Assembly to Machine code](#converting-assembly-to-machine-code)
      - [Linker script](#linker-script)
    - [Makefile and make](#makefile-and-make)
    - [Demo](#demo)
      - [Launching QEMU](#launching-qemu)
      - [Launching GDB](#launching-gdb)
      - [Single stepping the CPU](#single-stepping-the-cpu)
    - [Summary](#summary-4)
  - [Assembly Language](#assembly-language)
    - [ISA and Assembly Program](#isa-and-assembly-program)
    - [Pseudoinstructions](#pseudoinstructions)
    - [ABI register names](#abi-register-names)
  - [Essentials](#essentials)
    - [Program structure](#program-structure)
    - [Different Parts](#different-parts)
    - [Better GDB](#better-gdb)
    - [Summary](#summary-5)
  - [Directives & generated assembly](#directives--generated-assembly)
    - [Generating assembly from C code](#generating-assembly-from-c-code)
    - [Generated assembly code](#generated-assembly-code)
    - [Grouping patterns](#grouping-patterns)
    - [Summary](#summary-6)
  - [Build Process](#build-process)
    - [The need for C](#the-need-for-c)
    - [Build process](#build-process-1)
    - [Compiler](#compiler)
    - [Assembler](#assembler)
    - [Linker](#linker)
    - [Using the compiler](#using-the-compiler)
    - [Controlling the compiler](#controlling-the-compiler)
    - [Options](#options)
    - [Summary](#summary-7)

- [C Language](#c-language)
  - [Keywords](#keywords)
    - [Data Types](#data-types)
    - [Modifiers](#modifiers)
    - [Data Storage for basic types](#data-storage-for-basic-types)
      - [Integer types](#integer-types)
      - [Floating point type](#floating-point-type)
    - [void type](#void-type)
    - [typedef](#typedef)
    - [Custom data types](#custom-data-types)
      - [struct](#struct)
      - [sizeof](#sizeof)
      - [union](#union)
    - [Enumeration](#enumeration)
    - [Decision making](#decision-making)
      - [if-else](#if-else)
      - [switch](#switch)
    - [Repeated execution](#repeated-execution)
      - [for](#for)
      - [while](#while)
      - [do while](#do-while)
    - [Manipulating loops](#manipulating-loops)
      - [break](#break)
      - [continue](#continue)
    - [Unconditional jumps](#unconditional-jumps)
      - [goto](#goto)
      - [return](#return)
    - [Summary](#summary-8)
  - [Anatomy of Code](#anatomy-of-code)
    - [Functions](#functions)
      - [Generated assembly!](#generated-assembly)
      - [Function calls and the stack](#function-calls-and-the-stack)
      - [What is __mulsi3?](#what-is-__mulsi3)
      - [Without rv32im](#without-rv32im)
    - [Variables](#variables)
      - [Declaring Variables](#declaring-variables)
      - [Memory allocation & placement](#memory-allocation--placement)
      - [Initialized Globals](#initialized-globals)
      - [Uninitialized Globals](#uninitialized-globals)
      - [Locals](#locals)
      - [Array](#array)
      - [Thumb rules](#thumb-rules)
      - [Passing Parameters](#passing-parameters)
      - [Entry point](#entry-point)
      - [Multiple files](#multiple-files)
  - [Not C Keywords!](#not-c-keywords)
    - [Preprocessor directives](#preprocessor-directives)
      - [#include](#include)
      - [#define](#define)
      - [the #if family](#the-if-family)
      - [#ifdef](#ifdef)
      - [#ifndef](#ifndef)
      - [#else](#else)
      - [#endif](#endif)
      - [#undef](#undef)
      - [#pragma](#pragma)
      - [more directives](#more-directives)
  - [C: Pointers](#c-pointers)
    - [Pointers](#pointers)
    - [Declaration and Types](#declaration-and-types)
    - [Dereferencing a pointer](#dereferencing-a-pointer)
    - [Note on the usage of * and &](#note-on-the-usage-of--and-)
    - [Summary](#summary-9)
  - [C: More Pointers](#c-more-pointers)
    - [With an associated datatype](#with-an-associated-datatype)
    - [Without an associated datatype](#without-an-associated-datatype)
    - [typecasting](#typecasting)
    - [Pointing to code](#pointing-to-code)
    - [Summary](#summary-10)

  - [The power of structs](#the-power-of-structs)
    - [Generating 24x24 Red Square BMP Image](#generating-24x24-red-square-bmp-image)
    - [Compiling, Running and Viewing the output](#compiling-running-and-viewing-the-output)
    - [Summary](#summary-11)
  - [Object Oriented approach](#object-oriented-approach)
    - [An Object?](#an-object)
    - [structs and pointers](#structs-and-pointers)
    - [Linux Device Drivers](#linux-device-drivers)
    - [Data and fsops](#data-and-fsops)

- [Programming Embedded Systems](#programming-embedded-systems)
  - [Mixing Assembly & C](#mixing-assembly--c)
    - [Function Calling Convention for RISC-V RV32I CPU](#function-calling-convention-for-risc-v-rv32i-cpu)
      - [Register Usage](#register-usage)
      - [Parameter Passing](#parameter-passing)
      - [Return Values](#return-values)
      - [Function Prologue and Epilogue](#function-prologue-and-epilogue)
      - [Stack Usage](#stack-usage)
    - [Calling Assembly Code from C Files and Vice Versa](#calling-assembly-code-from-c-files-and-vice-versa)
    - [Running on Qemu](#running-on-qemu)
    - [Calling C Function from Assembly Code](#calling-c-function-from-assembly-code)
    - [Summary](#summary-12)
  - [CPU boot process](#cpu-boot-process)
    - [Why care about CPU boot process?](#why-care-about-cpu-boot-process)
    - [Single Core boot](#single-core-boot)
    - [Revisiting CPU model](#revisiting-cpu-model)
      - [Boot Flow](#boot-flow)
      - [RISC-V CPU boot flow](#risc-v-cpu-boot-flow)
      - [ARM-M CPU boot flow](#arm-m-cpu-boot-flow)
    - [Minimum boot setup](#minimum-boot-setup)
    - [Branch to main()](#branch-to-main)
    - [The ignored piece](#the-ignored-piece)
    - [Multi-core Boot flow](#multi-core-boot-flow)
  - [Code placement](#code-placement)
    - [Linker](#linker-1)
    - [Linker Script](#linker-script-1)
  - [C: Address Map & Struct](#c-address-map--struct)
    - [Memory Mapped I/O](#memory-mapped-io)
      - [Address Map/Space](#address-mapspace)
    - [Peripheral](#peripheral)
      - [Basics of UART](#basics-of-uart)
      - [Config and Status Registers (CSRs)](#config-and-status-registers-csrs)
      - [CSRs and Struct](#csrs-and-struct)
      - [volatile](#volatile)
      - [const](#const)
    - [Summary](#summary-13)
  - [Interacting with qemu UART](#interacting-with-qemu-uart)
    - [Moving Parts](#moving-parts)
    - [Jump from Assembly to C](#jump-from-assembly-to-c)
    - [Linker script](#linker-script-2)
    - [Code to manipulate the UART](#code-to-manipulate-the-uart)
      - [Black magic!](#black-magic)
      - [main()](#main)
      - [putc()](#putc)
      - [getc()](#getc)
      - [Missing curly braces](#missing-curly-braces)
      - [Struct pointer dereferencing](#struct-pointer-dereferencing)
    - [Building](#building)
    - [Running on qemu](#running-on-qemu)
    - [Summary](#summary-14)
  - [Where to Next?](#where-to-next)
    - [Traying on hardware](#traying-on-hardware)
    - [Board Support Packages](#board-support-packages)
    - [RTOS based firmware development](#rtos-based-firmware-development)

- [Bibliography](#bibliography)

---

## [Letter to the Reader](#letter-to-the-reader)

### [Why this book?](#why-this-book)
- **Page Number**: Unknown
  - **Typo**: .Their journies 
  - **Suggested Correction**: Their journeys
  - **Comment**: Spelling mistake
  ---
### [Embedded C doesn't exist!](#embedded-c-doesnt-exist)
  - **Page Number**: Unknown
    - **Typo**: seemed to have accidently
    - **Suggested Correction**: accidentally
    - **Comment**: Spelling mistake
  ---
  - **Page Number**: Unknown
    - **Typo**: seemed to have accidently
    - **Suggested Correction**: accidentally
    - **Comment**: Spelling mistake
  ---
  - **Page Number**: Unknown
    - **Typo**: as appiled
    - **Suggested Correction**: as applied
    - **Comment**: Spelling Mistake
  ---

### [Who this is for?](#who-this-is-for)
  - **Page Number**: Unknown  
    - **Typo**: targeted for begineers
    - **Suggested Correction**: beginners
    - **Comment**: Spelling Mistake
  ---

  - **Suggestion**: I would use bullet points here instead of listing down the target audience in a paragraph
  ---

### [Why emulator?](#why-emulator)
  - **Page Number**: Unknown
    - **Typo**: necessarily invtest
    - **Suggested Correction**: invest
    - **Comment**: Spelling Mistake
  ---

### [Why RISC-V architecture?](#why-risc-v-architecture)
  - **Page Number**: Unknown
    - **Typo**: will have a great futher
    - **Suggested Correction**: great future
    - **Comment**: Spelling Mistake
  ---
  - **Page Number**: Unknown
    - **Typo**: are adopting for there own courses
    - **Suggested Correction**: their own courses
    - **Comment**: There, their error
  ---
  - **Page Number**: Unknown
    - **Typo**: as a self exploration
    - **Suggested Correction**: as self-exploration
    - **Comment**: Grammar
  ---

### [Community and resources](#community-and-resources)
  - **Page Number**: Unknown
    - **Typo**: There also various
    - **Suggested Correction**: There are also various
    - **Comment**: Probably meant to type this in but didn't
  ---
  - **Page Number**: Unknown
    - **Typo**: 
    - **Suggested Correction**:
    - **Comment**: Spelling Mistake
  ---

### [Meet the Crew](#meet-the-crew)
  - **Comment**: Don't want to comment on anything here. This section is probably close to your heart and I dont think it's my place to suggest any edits here.
  ---

### [Providing Feedback](#providing-feedback)
  - **Page Number**: Unknown
    - **Typo**: Providing feeback
    - **Suggested Correction**: Providing Feedback
    - **Comment**: This was just funny lol
  ---




## Mental Models

### [C: History and Relevance](#c-history-and-relevance)
  - **Page Number**: 5
    - **Typo**: 
    - **Suggested Correction**: 
    - **Comment**: 
  ---

  - **Page Number**: 5
    - **Suggestion**: Note 3 seems to informal. Maybe something like, "While it is possible for some applications to run code written in C++, the vast majority (around 99%) of such applications execute code written in C.
    ---


## Overall Feedback
- **Consistency**: Review the use of capitalization, particularly in chapter titles and headings, to ensure consistency.
- **Clarity**: Some sentences could benefit from restructuring for clarity. See suggestions provided in individual sections.
- **Tone**: The tone varies slightly in different parts of the text; consider maintaining a consistent tone throughout the book.
- **Final Note**: Please address the issues outlined in this report. If you have any questions or need further clarification, feel free to reach out.

---

