\---

name: claude-senior-voice-tts

description: Handles Web Audio chimes, SpeechRecognition triggers, and safe TTS vocal notifications without blocking UI rendering.

\---



\# Voice \& Speech Guidelines



When modifying `src/App.tsx` or `sunnyBrain.ts` for voice or audio features:



1\. \*\*Audio Feedback\*\*:

&#x20;  - Always trigger a Web Audio API synthesized chime (523.25 Hz / 659.25 Hz sine wave) \*before\* invoking spoken TTS for medication or system alerts.

&#x20;  - Never load large external `.mp3` files; rely strictly on local browser Web Audio oscillators to keep memory usage low and execution instant.



2\. \*\*Speech Recognition (STT)\*\*:

&#x20;  - Use native `webkitSpeechRecognition` with graceful fallback checking (`if (!('webkitSpeechRecognition' in window))`).

&#x20;  - Automatically strip filler words ("um", "uh") from the transcribed string before passing input into `sunnyBrain.ts`.

&#x20;  - Maintain continuous visual listening states ("Listening...", "Microphone Off") with high-contrast indicator badges.

