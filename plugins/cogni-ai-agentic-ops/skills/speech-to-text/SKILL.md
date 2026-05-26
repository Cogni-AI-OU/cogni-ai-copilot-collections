---
name: speech-to-text
description: >-
  Open-source speech-to-text and voice typing tools for dictation, transcription, and voice input across desktop, mobile, and terminal.
  USE FOR: evaluating local/hybrid ASR tools, comparing platform-specific voice typing options, selecting dictation tools with direct editor integration.
  DO NOT USE FOR: meeting bots, call transcription services, closed-source dictation products, general speech APIs without a typing interface, non-open-source mobile assistants.
  You MUST load this skill when evaluating or comparing open-source speech-to-text and voice typing tools.
license: MIT
---

# Speech to Text

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## WHEN TO USE

- You need open-source tools for dictation, voice typing, or speech-to-text text entry while actively working.
- You are comparing desktop, mobile, or terminal-first speech input workflows.
- You want tools that can insert recognized text directly into an editor, input field, or command-line workflow.
- You are specifically evaluating local-only or hybrid speech recognition options.
- You need a platform-specific shortlist for Linux, macOS, Windows, Android, or iOS voice typing tools.

## WHEN NOT TO USE

- You are looking for closed-source dictation or transcription products.
- You need meeting bots, note takers, or call transcription services rather than active voice typing tools.
- You want general speech-to-text APIs or backend transcription services without a usable typing interface.
- You are evaluating non-open-source mobile assistants or OS-native features that are not open-source projects.
- You need a comprehensive survey of all transcription software rather than tools focused on dictation workflows.

## Scope

This list focuses on tools that let you speak and get text into the place where you are actively working.

- Open-source apps, keyboards, menu bar utilities, and CLI tools for dictation or voice typing
- Desktop, mobile, and terminal-first workflows
- Local-only and hybrid tools, as long as the project itself is open source

This list does not try to cover:

- Closed-source products
- General transcription tools that do not support typing or dictation workflows
- Meeting bots, note takers, or speech APIs without a usable typing interface

## Core Process

1. **Identify Target Platform**: Determine the OS (Linux, macOS, Windows, Android, iOS).
2. **Select Mode**: Choose `Local` for fully offline recognition or `Hybrid` for cloud-assisted ASR.
3. **Filter by Engine**: Match against available ASR engines (Whisper, Whisper.cpp, Faster Whisper, Parakeet, Vosk).
4. **Evaluate Tool**: Scan the directory below for matching entries, then visit the repository for setup instructions.

## Quick Start Example

```bash
# Transcribe an audio file using whisper.cpp
git clone https://github.com/ggml-org/whisper.cpp
cd whisper.cpp && make -j
./main -m models/ggml-base.en.bin -f sample.wav

# Start nerd-dictation on Linux (offline Vosk-based dictation)
nerd-dictation begin --vosk-model en-us-small
# Speak into your microphone...
nerd-dictation end
# Transcribed text appears in the active window.
```

Most tools on this list support offline speech recognition. See `Mode` and `Engine` in the directory below for details.

## Directory

`Mode`: `Local` means on-device speech recognition. `Hybrid` means the tool supports both local and cloud or BYO-cloud setups.

| Name | Platforms | Mode | Engine | Summary |
| --- | --- | --- | --- | --- |
| [Amical](https://github.com/amicalhq/amical) | macOS, Windows | Local | Whisper | Context-aware dictation that adapts formatting to the app you are using. |
| [Epicenter Whispering](https://github.com/EpicenterHQ/epicenter/tree/main/apps/whispering) | Linux, macOS, Windows, Web | Hybrid | Whisper | Local-first dictation with global shortcut and multiple Whisper providers. |
| [FluidVoice](https://github.com/altic-dev/FluidVoice) | macOS | Hybrid | Parakeet, Apple Speech, Whisper | macOS dictation that types into any app and switches between local speech engines. |
| [FnKey](https://github.com/evoleinik/fnkey) | macOS | Hybrid | Deepgram Nova-3, Groq Whisper | Rust menu bar app; activates mic only while holding Fn, real-time streaming. |
| [hyprwhspr](https://github.com/goodroot/hyprwhspr) | Linux | Hybrid | Whisper.cpp, Parakeet | Push-to-talk Linux dictation with visualizer, Waybar, and systemd integration. |
| [nerd-dictation](https://github.com/ideasman42/nerd-dictation) | Linux | Local | Vosk | Offline dictation that types into any window via simulated keystrokes. |
| [OmniDictate](https://github.com/gurjar1/OmniDictate) | Windows | Local | Whisper | Desktop dictation tool aimed at type-anywhere workflows. |
| [Tambourine Voice](https://github.com/kstonekuan/tambourine-voice) | macOS, Windows | Hybrid | Faster Whisper | Voice interface for any app with configurable STT and LLM providers. |
| [Vibe](https://github.com/thewh1teagle/vibe) | Linux, macOS, Windows | Local | Whisper.cpp | Desktop app to transcribe audio and video offline. |
| [VoiceInk](https://github.com/Beingpax/VoiceInk) | macOS | Hybrid | WhisperKit | Native macOS dictation with per-app tuning and custom dictionary. |
| [VoiceTypr](https://github.com/moinulmoin/voicetypr) | macOS, Windows | Local | Whisper | Voice-to-text dictation built with Tauri (binaries require a license). |
| [VOXD](https://github.com/jakovius/voxd) | Linux | Local | Whisper.cpp | Linux dictation with GUI, tray, CLI modes, and optional LLM post-processing. |
| [VoxType](https://github.com/peteonrails/voxtype) | Linux | Hybrid | Whisper.cpp, Parakeet, Moonshine, SenseVoice | Linux dictation with seven engine choices, CJK support, and Wayland insertion. |
| [WhisperBoard](https://github.com/Saik0s/Whisperboard) | iOS | Local | Whisper.cpp | iOS app for recording speech with downloadable Whisper models. |

## Related Projects

Speech recognition engines, models, and APIs that power the tools listed above.

- [whisper.cpp](https://github.com/ggml-org/whisper.cpp) - Pure C/C++ Whisper inference; runs on Apple Silicon, CUDA, Vulkan, and WASM.
- [Faster Whisper](https://github.com/SYSTRAN/faster-whisper) - CTranslate2-based Whisper reimplementation; up to 4x faster with lower memory.
- [Apple Speech](https://developer.apple.com/documentation/speech) - Apple's on-device speech recognition framework for iOS, macOS, and watchOS.

## References
