# Speech and Voice

## Implementation

Speech is implemented in `src/speech/speechSynthesis.js`.

The extension uses browser-provided:

- `SpeechSynthesis`
- `SpeechSynthesisUtterance`

It does not use a remote speech-generation API in the supplied implementation.

## Settings

The user can control:

- volume
- speed
- voice profile

## Volume

The UI uses a 0–100 value and converts it to the browser's 0–1 speech-synthesis range.

## Speed

The current speech speed is constrained to approximately **0.5–2.0**.

## Chunking

Long text is divided into smaller speech utterances of approximately **260 characters**. This is intended to reduce browser speech-synthesis problems associated with very long utterances.

## Voice selection

The implementation attempts, in order:

1. Exact language match
2. Base-language match
3. Fallback voice

For example, an `en-US` page can first look for an `en-US` voice, then another English voice if an exact match is unavailable.

## Voice profiles

The current profiles are:

- Default
- Clear
- Calm

These profiles influence browser voice-selection heuristics and speech pitch. They are **not** separate SecureReader cloud voices.

## Browser dependency

The available voice list depends on Chrome and the device's installed speech services. SecureReader cannot guarantee the same voices on every machine.