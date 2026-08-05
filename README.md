<div align="center">

<img src="docs/app-icon.png" alt="LavderTS app icon" width="168" height="168">

# LavderTS

**A native TeamSpeak 3 client for Apple Silicon. The protocol, re-implemented; the interface, rebuilt for the Mac.**

![macOS 14+](https://img.shields.io/badge/macOS-14%2B-1d1d1f)
![Apple Silicon](https://img.shields.io/badge/Apple%20Silicon-arm64-1d1d1f)
![Notarized](https://img.shields.io/badge/Apple-notarized-1d1d1f)
![Self updating](https://img.shields.io/badge/updates-in--app-1d1d1f)

<br>

<a href="https://github.com/Lavder-Enterprise/lavderts-releases/releases/latest/download/LavderTS-arm64.zip">
<img src="https://img.shields.io/badge/Download%20for%20Mac-0A84FF?style=for-the-badge&logo=apple&logoColor=white&labelColor=0A84FF" alt="Download LavderTS for Mac" height="44">
</a>

<sub>**v0.2.1** · macOS 14+ · Apple Silicon · 5.6 MB · signed and notarized by Apple</sub>

<sub><a href="../../releases">All releases</a> · <a href="../../releases/latest">Release notes</a></sub>

</div>

---

The official TeamSpeak 3 client runs on macOS the way a Windows application runs on macOS: an Intel binary under translation, a window that belongs to another decade, and an audio path that predates every device most people now own.

LavderTS speaks the same protocol to the same servers — the low-level handshake, the RSA puzzle, EAX packet encryption, QuickLZ command compression, Opus and the legacy Speex and CELT codecs — and does it as an arm64 application with a SwiftUI interface, so it starts instantly, idles at nothing, and looks like it belongs on the machine.

## What it does

| | |
|---|---|
| **The whole protocol** | Channels, permissions, groups, file transfers, offline messages, whisper lists, privilege keys, server administration. |
| **Voice that behaves** | Opus voice and music, the legacy codecs, per-talker volume and mute that survive a reconnect, an adaptive jitter buffer, and spatial separation between simultaneous speakers. |
| **The retail capture chain** | Echo cancellation, noise suppression, automatic gain control and keyboard attenuation, run over speexdsp — the same library the official client uses — so they apply to whichever microphone and speakers you actually chose. |
| **Chat that keeps up** | Per-server history on disk, tabs named after the server and the channel, and per-person notification rules keyed to TeamSpeak identity so they survive a nickname change. |
| **Plugins** | A soundboard that streams clips into the channel through your own voice stream, with the Myinstants catalogue built in, and a remote control for a SinusBot instance. |
| **Self-updating** | Signed and notarized builds. Installed copies check this repository's release feed at launch and every six hours, and tell you when there is something new. |

## Install

1. [**Download LavderTS**](https://github.com/Lavder-Enterprise/lavderts-releases/releases/latest/download/LavderTS-arm64.zip) — that link always points at the newest build.
2. Unzip and drag **LavderTS.app** to Applications. No Gatekeeper warning: builds are signed and notarized by Apple.
3. Grant the microphone when asked. Keyboard attenuation additionally needs Input Monitoring, in System Settings ▸ Privacy & Security.

Requirements: macOS 14 or later on Apple Silicon.

## Updates

The app checks this repository's `latest.json` at launch and every six hours, and tells you when a newer version is published. To ask at any other moment, **LavderTS ▸ Check for Updates…**. The feed URL is in Settings ▸ Updates for anyone running their own builds.

## Audio notes

Two things about macOS are worth knowing before you file them as bugs.

**Bluetooth microphones cost you both directions.** Choosing the microphone on a Bluetooth headset makes macOS switch the headset to hands-free mode, which drops playback *and* capture to 24 kHz narrowband — everyone sounds robotic, including you. Pick a wired or built-in microphone and the headset stays in high-quality playback mode. The app says so where you choose the device.

**Echo cancellation is done in software, on purpose.** Apple's voice-processing unit binds itself to the system default input and rejects any attempt to point it elsewhere, so it cannot honour a microphone you chose. LavderTS runs the processing over its own samples instead, which is why it works with any combination of devices.

## Privacy

Voice and chat go to the TeamSpeak server you connect to and nowhere else. The app talks to two other hosts, both only when you ask it to: this repository, for the update check, and myinstants.com, when you search or play a sound from the soundboard's browser. No analytics, no accounts, no telemetry.

Protocol logging is off in released builds. Turning it on in Settings ▸ Updates writes commands, nicknames and channel names to `~/Library/Logs/LavderTS.log` — useful when reporting a bug, and off unless you choose otherwise.

## Reporting a problem

Open an issue with what you were doing, what happened, and the server's software version if you know it. If the problem is audio or connection related, turn on the verbose protocol log, reproduce it once, and attach the relevant part of `~/Library/Logs/LavderTS.log` — read it first, it contains the names of the channels and people you were with.

---

<div align="center">
<sub>Built by <a href="https://lavder.com">Lavder Enterprise</a>. Not affiliated with TeamSpeak Systems GmbH.</sub>
</div>
