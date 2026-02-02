# Model Decisions

## Text LLM
- Model: Gemma 1B
- Quantization: Q4_K_M
- Format: GGUF
- Runtime: llama.cpp

## Vision Model
- Model: SmolVLM-Instruct
- Format: GGUF
- Runtime: llama.cpp (vision build)

## Constraints
- One model loaded at a time
- Target RAM < 1 GB
- Fully offline

