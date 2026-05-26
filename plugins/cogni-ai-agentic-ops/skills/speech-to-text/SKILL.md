---
name: speech-to-text
description: |
  Real-time streaming speech-to-text and simultaneous translation workflows.
  USE FOR:
  - https://github.com/ufal/SimulStreaming
    - SimulStreaming
    - Simultaneous Translation
    - Offline Speech
    - LLM Models
    - IWSLT 2025
    - Whisper speech-to-text
    - EuroLLM text-to-text translation
    - streaming ASR
  - https://github.com/ufal/whisper_streaming
    - Whisper realtime streaming
    - long speech-to-text transcription
    - LocalAgreement policy
    - Whisper-Streaming
    - faster-whisper
    - whisper_timestamped
    - mlx-whisper
    - Voice Activity Controller (VAC)
  DO NOT USE FOR:
  - Offline text-to-text translation without an ASR component
  - Transcribing short audio chunks where real-time streaming is not required
  - Persona specification or general project context
license: MIT
---

# Speech to Text

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## When to Use

- When needing to stream real-time microphone or audio file input to text.
- When performing simultaneous translation using Whisper or EuroLLM.
- When working with SimulStreaming or whisper_streaming repositories.

## When Not to Use

- Offline text-to-text translation without speech components.
- Traditional offline speech transcription where latency is not a concern.

## Core Process

1. **SimulStreaming Initialization**:
   - Determine if the task is transcription (Whisper) or translation (EuroLLM cascade).
   - Install required dependencies (`requirements_whisper.txt` or `requirements_translate.txt`).
2. **Whisper Streaming Setup**:
   - Install `faster-whisper`, `whisper_timestamped`, or `mlx-whisper` based on hardware availability.
3. **Execution**:
   - Run `simulstreaming_whisper.py` or `whisper_online.py` with appropriate audio source (`audio_path`), language (`--language`), and task flags.
   - For real-time mic input, pipe audio (e.g., `arecord`) into the TCP server via `nc`.

## Common Pitfalls

- **Missing VAD**: Not using Voice Activity Controller (`--vac`) can result in processing silence and higher latency. Always use `--vac` when available.
- **Suboptimal Chunk Size**: Setting `--min-chunk-size` too small without `--vac` causes word truncation. Ensure the chunk size is appropriate for your latency requirements.
- **Hardware Limitations**: Using the largest models (like `large-v3` or `EuroLLM-9B`) on CPU will be too slow for real-time. Use GPU acceleration and `faster-whisper` backend if possible.

## References

- [SimulStreaming](https://github.com/ufal/SimulStreaming)
- [whisper_streaming](https://github.com/ufal/whisper_streaming)