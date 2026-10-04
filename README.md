<div align="center">

# Lite Wallpaper

### Lightweight native live wallpapers for Windows.

**Fast. Minimal. Native. Designed around performance.**

[Download](https://github.com/HM-dev3/lite-wallpaper/releases) •
[Report an Issue](https://github.com/HM-dev3/lite-wallpaper/issues) •
[GitHub](https://github.com/HM-dev3/lite-wallpaper)

</div>

---

## About Lite Wallpaper

**Lite Wallpaper** is a native Windows live-wallpaper application built around one simple idea:

> Your wallpaper should look great when you can see it — and consume as little of your system as possible when you cannot.

Lite Wallpaper uses a native Windows runtime rather than a browser-based UI or web rendering engine for wallpaper playback.

The control application can be completely closed while the wallpaper continues running.

The runtime is designed to stop unnecessary decode and presentation work when the wallpaper is paused, covered, or suspended by your selected performance policies.

---

## Performance First

Performance is one of the main reasons Lite Wallpaper exists.

In a local comparison against **Lively Wallpaper**, both applications played the exact same:

- 1920 × 1080
- H.264
- 30 FPS
- same Windows PC
- same display
- same GPU

### Local benchmark

| Resource | Lite Wallpaper | Lively Wallpaper | Difference |
|---|---:|---:|---:|
| CPU | 2.78% of one CPU core | 4.73% | **41.2% lower** |
| Private memory | 118 MiB | 333 MiB | **64.5% lower** |
| GPU 3D activity | 7.81% | 13.79% | **43.4% lower** |

### Lite Wallpaper

**41.2%**
lower CPU usage

**64.5%**
lower private memory

**43.4%**
lower GPU 3D activity

> **Important:** This was one local benchmark using one PC and one 1080p30 wallpaper.  
> Performance varies depending on hardware, video codec, resolution, settings, Windows version, drivers, and system configuration.

Lite Wallpaper is designed around efficiency, but these numbers should not be interpreted as universal performance guarantees.

---

## Features

### Native live wallpaper playback

- Native Windows runtime
- Hardware-accelerated video decode
- Direct3D 11 / DXGI presentation
- Media Foundation video pipeline
- No Electron
- No Chromium
- No WebView runtime required for wallpaper playback

---

### Wallpaper Library

Import your wallpapers once and keep them inside Lite Wallpaper.

- Persistent wallpaper library
- Cached thumbnails
- Search
- Favorites
- Pin wallpapers
- Recent wallpapers
- Instant switching
- Missing-file relink
- Original files are never deleted by removing a library entry

Browsing the library does not start decoding every wallpaper.

Only active content consumes playback resources.

---

### Playback Speed

Adjust playback from:

**0.10× → 4.00×**

Including presets such as:

- 0.10×
- 0.25×
- 0.50×
- 0.75×
- 1.00×
- 1.25×
- 1.50×
- 2.00×
- 3.00×
- 4.00×

Speed changes apply directly to the active wallpaper.

---

### Display & Framing

Choose how your wallpaper fits the display:

- Fill
- Fit
- Stretch

Lite Wallpaper also includes architecture for per-display wallpaper settings.

---

### Live Visual Controls

Adjust the active wallpaper without restarting playback:

- Brightness
- Contrast
- Saturation
- Hue / Color
- Sharpness where supported by the GPU
- Reset to neutral

Supported adjustments are applied through the native GPU video-processing path.

No CPU pixel conversion is used for normal live adjustments.

---

## Performance Policies

Lite Wallpaper can automatically reduce unnecessary background work.

### Fullscreen / Maximized applications

Choose what happens when another application occupies the display:

- Pause wallpaper
- Keep running
- Release playback resources

### Focused applications

- Keep running
- Pause wallpaper

### Fully covered desktop

- Pause automatically
- Keep running

### Battery / Energy Saver

Choose between:

- Normal
- Reduced activity
- Pause

These policies work independently, so one `Keep running` option does not override another active pause condition.

---

## Efficient When Hidden

When Lite Wallpaper is paused or fully covered, the runtime is designed to stop useful wallpaper work.

In qualified tests, settled paused/covered states reached:

- **0 new video reads**
- **0 Presents**
- **0 content-timer work**
- idle playback GPU engines

This behavior is one of the core architectural goals of Lite Wallpaper.

---

## Start with Windows

Lite Wallpaper can restore your active wallpaper automatically after Windows login.

When enabled:

1. Windows logs in.
2. The lightweight runtime starts directly.
3. Lite Wallpaper waits for the desktop shell if necessary.
4. Your last active wallpaper is restored.
5. Dynamic playback begins automatically.

The full control interface does **not** need to open.

No service or permanent launcher helper is required.

---

## System Tray

Closing the control window does not stop your wallpaper.

The lightweight runtime remains available through the Windows notification area.

Tray controls include:

- Open Lite Wallpaper
- Pause / Resume
- Previous wallpaper
- Next wallpaper
- Stop & restore
- Exit

---

## Playlists

Create wallpaper playlists directly from your library.

Features include:

- Create and rename playlists
- Reorder wallpapers
- Previous / Next
- Shuffle
- Loop
- Timed wallpaper rotation

Future playlist items are not pre-decoded.

Only the currently active wallpaper consumes video playback resources.

---

## Optimize for Lite Wallpaper

Lite Wallpaper includes an optional **offline optimizer**.

It can prepare a separate wallpaper copy designed to better match your hardware and display.

Available profiles:

### Efficiency

Prioritizes:

- lower resource usage
- smaller files
- sensible resolution
- lower frame rate where appropriate

### Balanced

A practical balance between:

- visual quality
- smoothness
- storage size
- decode cost

### High Quality

Preserves more:

- resolution
- frame rate
- detail
- bitrate

The optimizer can consider:

- display resolution
- source resolution
- source FPS
- bitrate
- codec/profile
- available hardware decoding
- aspect ratio
- audio

It can also remove unnecessary audio from prepared wallpaper files.

### Your original file is never modified.

Optimized copies are optional and reversible.

For some media, the original file may already be the best choice.

---

## Supported Media

Lite Wallpaper uses native Windows Media Foundation decoding.

Current playback architecture supports compatible native formats such as:

- H.264 / AVC
- HEVC / H.265 where Windows provides a compatible decoder
- AV1 where compatible native decoding is available
- frame rates up to 60 FPS within supported resource limits
- variable-frame-rate media when valid presentation timestamps are available
- resolutions within the current playback resource budget

Hardware support varies between systems.

Unsupported media can fall back to a static poster where possible.

Lite Wallpaper intentionally avoids adding a heavyweight runtime decoder stack merely to support every possible format.

---

## Windows Support

Lite Wallpaper is designed for:

- **Windows 11 x64**
- **Windows 10 x64**

The application includes separate desktop-host handling for modern and classic Windows shell configurations.

Hardware, drivers, codecs, and unusual desktop configurations can still affect compatibility.

---

## Lightweight Architecture

Lite Wallpaper is designed to avoid unnecessary resident software.

### While the control app is open

The UI uses native Windows rendering and local resources.

### After closing the control app

The UI process exits completely.

Only the wallpaper runtime remains.

There is no:

- permanent browser process
- Electron runtime
- Chromium wallpaper engine
- tray helper executable
- always-running UI
- background analytics process

---

## Why Lite Wallpaper?

Lite Wallpaper is built around a different priority order:

1. **Performance**
2. **Reliability**
3. **Useful features**
4. **Visual polish**

Not every possible wallpaper technology is included yet.

Instead, Lite Wallpaper 1.0 establishes a lightweight native foundation that future versions can build on without turning the application into a heavyweight background program.

---

## Built to Grow

Lite Wallpaper 1.0 is the beginning of the platform.

Future releases are planned to explore areas such as:

- broader media compatibility
- native shader wallpapers
- procedural scene wallpapers
- interactive wallpapers
- audio-reactive wallpapers
- improved low-end hardware support
- deeper battery optimization
- creator and wallpaper-package tools
- optional advanced wallpaper runtimes
- additional platforms

Features are added only when they can fit the project's performance-first philosophy.

No release dates are promised for planned features.

---

## Installation

Download the latest release from:

**https://github.com/HM-dev3/lite-wallpaper/releases**

### Installer

Download the installer from the release Assets section and run it.

Lite Wallpaper installs per-user and does not normally require administrator access.

### Portable version

Download the portable ZIP and:

1. Extract the entire archive.
2. Keep all included files together.
3. Run `LiteWallpaper.exe`.

Do not launch the executable directly from inside the ZIP.

---

## First Run

1. Open Lite Wallpaper.
2. Select **Add wallpapers**.
3. Choose a supported local video.
4. Select the target display.
5. Choose Fill / Fit / Stretch.
6. Click **Apply wallpaper**.

You can then close the Lite Wallpaper control window.

Playback continues through the lightweight runtime.

---

## Stop & Restore

`Stop & restore`:

- stops live wallpaper playback
- shuts down active wallpaper resources
- restores the previous supported static Windows wallpaper when possible

Lite Wallpaper avoids deleting or modifying your original wallpaper files.

---

## Privacy

Lite Wallpaper is designed to work locally.

Normal wallpaper playback does not require:

- an account
- cloud storage
- telemetry
- a remote wallpaper service

Your wallpaper files remain on your computer.

The application may open external links only when you explicitly click links such as the official GitHub repository.

---

## Official Repository

This is the official Lite Wallpaper repository:

**https://github.com/HM-dev3/lite-wallpaper**

You can use GitHub to:

- download releases
- report bugs
- request features
- follow development
- read release notes
- star the project

---

## Support the Project

Lite Wallpaper is independently developed.

If the project is useful to you, you can help by:

- ⭐ starring the GitHub repository
- reporting bugs
- testing Lite Wallpaper on different hardware
- sharing feedback
- recommending the project to others

A dedicated financial support link may be added separately in the future.

---

## Reporting Bugs

When reporting a problem, please include:

- Windows version
- CPU
- GPU
- display resolution
- wallpaper resolution
- wallpaper FPS
- codec if known
- whether the issue occurs after reboot, fullscreen, sleep, Explorer restart, etc.

Report issues here:

**https://github.com/HM-dev3/lite-wallpaper/issues**

---

## Current Limitations

Lite Wallpaper 1.0 focuses on native video wallpapers.

Some current limitations may include:

- no HDR wallpaper playback
- no clone/span wallpaper mode
- native hardware codec availability depends on Windows and GPU support
- some visual filters depend on GPU capabilities
- optimized copies are lossy
- still-image preview rather than a second continuously playing UI preview
- unusual multi-GPU / multi-monitor configurations may require additional testing
- Windows SmartScreen may warn about unsigned releases until trusted code signing is configured

These limitations will continue to be improved over future releases.

---

## Security

Only download Lite Wallpaper from the official repository:

**https://github.com/HM-dev3/lite-wallpaper**

Official releases should include SHA-256 checksums.

If the current build is unsigned, Windows may display an unknown publisher / SmartScreen warning.

Always verify downloaded release files when possible.

---

## Version

### Lite Wallpaper 1.0

**Platform:** Windows x64  
**Architecture:** Native Windows  
**Official repository:** https://github.com/HM-dev3/lite-wallpaper

Technical commit/build metadata is available inside the application for diagnostics.

---

<div align="center">

### Lite Wallpaper

**Your desktop, quietly alive.**

Built for efficiency. Designed for real desktops.

[Download](https://github.com/HM-dev3/lite-wallpaper/releases) •
[Issues](https://github.com/HM-dev3/lite-wallpaper/issues) •
[GitHub](https://github.com/HM-dev3/lite-wallpaper)

</div>
