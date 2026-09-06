# App 122: Code Cipher

Part of [AppADay](https://augustineiacopelli.github.io/appaday/), a daily discipline project shipping one complete, functional, mobile-friendly web app every day.

**Live app:** https://augustineiacopelli.github.io/appaday-122-code-cipher/

## What it does

Code Cipher is a six-protocol cipher lab. Pick a protocol, set its complexity, type a message, and encode or decode. Five classical ciphers are included for the fun of it: Caesar Shift, Atbash, Vigenere, Morse Code, and Symbol Set substitution. A sixth protocol, AES-256, is real modern cryptography, running entirely in the browser through the Web Crypto API with no server involved.

A Field Manual panel explains what each protocol is doing and gives an honest, plain-language read on how easily it can be broken, updating live as settings change. A spacing-removal option strips word boundaries from output for the four letter-based classical ciphers, a real historical technique for increasing the effort needed to crack a cipher by hand. A Mystery Message button generates a random phrase encoded with a random protocol and complexity setting, ready to decode.

## The six protocols

Caesar Shift moves every letter forward a fixed number of places, adjustable from 3 to 25. It only has 26 possible shifts total, so it is breakable by brute force in seconds regardless of shift value.

Atbash mirrors the alphabet with a single fixed mapping. No configuration, no real security, a novelty cipher.

Vigenere shifts each letter using a repeating keyword. Longer, less predictable keywords resist frequency analysis better than short ones, though the cipher remains breakable with enough ciphertext.

Morse Code converts letters to dots and dashes. Standard spacing keeps letters clearly separated; Dense mode removes the gaps, turning decoding into a genuine ambiguity puzzle.

Symbol Set substitutes letters with icons. Easy mode only replaces the 12 most common letters and leaves the rest readable; Full mode replaces all 26.

AES-256 derives a 256-bit key from a passphrase using PBKDF2 at 150,000 iterations, then encrypts with AES-GCM. This is the same standard used to protect classified data and modern banking systems. The passphrase, not the math, is the weak point: a short passphrase can be guessed regardless of how strong AES itself is.

## Build notes

Single self-contained `index.html`, inline CSS and JavaScript, no build step, no external libraries beyond a Google Fonts import. AES-256 uses the browser's native Web Crypto API rather than any third-party crypto library. Scales from a 375px mobile viewport to desktop with no fixed heights. Clipboard copy falls back to `execCommand` when the async Clipboard API is unavailable. Source is ASCII-clean.

---

*Ship something every day. It compounds.*
