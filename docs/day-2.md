# Day 2 — Android NDK Build of llama.cpp

## Goal
Successfully build llama.cpp as Android shared libraries using the Android NDK.

This day focused purely on toolchain correctness and cross-compilation,
not application logic.

## Environment
- OS: Windows
- Android NDK: 26.3.11579264
- CMake: 3.22.1
- Generator: Ninja
- ABI: arm64-v8a
- Android API Level: 24

## Build Strategy
- Use llama.cpp as the root CMake project
- Perform an out-of-source build
- Build libraries only (no CLI tools, servers, or tests)

## Key Challenges Encountered
- PowerShell vs CMD path and syntax issues
- Incorrect CMake generator (Visual Studio vs Ninja)
- llama.cpp assuming POSIX APIs in tests and tools
- Android NDK lacking support for posix_spawn APIs

## Solutions Applied
- Forced Ninja generator
- Cleaned build directory between generator changes
- Disabled non-Android-compatible targets:
  - Tests
  - Tools
  - Server
  - Examples

## Final CMake Configuration Flags
- DLLAMA_BUILD_TESTS=OFF
- DGGML_BUILD_TESTS=OFF
- DLLAMA_BUILD_EXAMPLES=OFF
- DLLAMA_BUILD_SERVER=OFF
- DLLAMA_BUILD_TOOLS=OFF

## Result
- llama.cpp successfully configured for Android
- Shared libraries generated (libllama.so, libggml.so)
- Android toolchain and build pipeline verified

## Outcome
Android-native build environment is confirmed working.
Project is ready to move on to:
- loading GGUF models
- running first inference
- adding a minimal Android wrapper
