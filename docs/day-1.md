# Day 1 — Project Setup & Architecture Decisions

## Goal
Establish a clean repository structure and lock core technical decisions
before starting native Android builds.

## Repository Initialization
- Created a dedicated GitHub repository for the native AI core
- Set up a clear folder structure separating:
  - native source code
  - build artifacts
  - documentation

## Initial Folder Structure
pock-ai-core/
├── native/
│   ├── llama/        (llama.cpp source)
│   ├── wrapper/      (future Android wrapper)
│   └── models/       (GGUF models, ignored by git)
├── docs/
└── build-android/    (out-of-source build directory)

## Technology Decisions
- Target Platform: Android
- CPU Architecture: arm64-v8a
- Language: C++
- Build System: CMake
- Generator: Ninja
- Toolchain: Android NDK
- Runtime: llama.cpp
- Mode: Fully offline (no network usage)

## Model Decisions
- Text LLM: Gemma 1B (GGUF, Q4 quantization)
- Vision Model: SmolVLM-Instruct (GGUF)
- Constraint: Only one model loaded at a time (memory safety)

## Design Principles
- Offline-first
- Libraries only (no CLI tools in production)
- Explicit model load and unload
- Token streaming (no blocking responses)
- Graceful failure instead of crashes

## Outcome
Project structure and architecture finalized.
Ready to begin native Android build work.
