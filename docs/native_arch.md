# Native Architecture

## Platform
- Android (arm64-v8a)
- C++ with Android NDK
- CMake build system

## Components
- llama/: llama.cpp source
- wrapper/: thin C++ API for Flutter
- models/: local GGUF models
- cmake/: build configuration

## Design Rules
- No global model state leaks
- Explicit load/unload
- Streaming tokens
