# 🎚️ Stratum Audio

**Stratum Audio** is a granular volume controller for macOS that allows you to manage audio levels on a per-application basis. 

Unlike Windows, macOS lacks a native per-app volume mixer. Stratum fills this gap by utilizing a custom **CoreAudio HAL (Hardware Abstraction Layer) Driver** to intercept and process audio streams before they reach your hardware.

---

## 🚧 Status: Work in Progress
This project is currently in early-stage development (**Phase 1 & 2**). 
Current focus: *CoreAudio Driver Handshake & Virtual Device Setup.*

---

## ✨ Features (Planned)
- **Individual App Sliders:** Adjust volume for Spotify, Zoom, Chrome, etc., independently.
- **Menu Bar Interface:** A lightweight SwiftUI-based menu bar app for quick access.
- **Low Latency:** A high-performance C++ driver backend ensuring minimal audio lag.
- **Granular Control:** Precise gain adjustment beyond the standard 16-step macOS increments.

## 🏗️ Technical Architecture
Because macOS does not provide a public API for per-app volume, Stratum uses a two-part system:
1. **The Driver (C++):** A HAL Plug-in that creates a virtual audio device. It identifies audio streams by their Process ID (PID).
2. **The Controller (SwiftUI):** A user-facing app that communicates with the driver to adjust gain coefficients for specific PIDs.

## 🛠️ Requirements
- **macOS:** 12.0+ (Monterey or later)
- **Xcode:** 14.0+
- **Hardware:** Intel or Apple Silicon (Universal)

## 📂 Project Structure
- `/GranularAudio`: The SwiftUI frontend application.
- `/GranularAudioDriver`: The C++ CoreAudio Server Plug-in.

---

## 🤝 Contributing
Since this involves low-level CoreAudio C++ development, contributions are welcome! If you have experience with `AudioServerPlugIn.h` or IOKit, feel free to open an issue or PR.

## ⚖️ License
[MIT](LICENSE)
