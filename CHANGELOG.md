# Changelog

All notable changes to Wuji Studio will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

## [0.9.0] - 2026-04-07

### Added

- Built-in diagnostics for crash recovery and troubleshooting

### Fixed

- Fixed layout preset switching losing or overwriting panel configurations from other presets
- Fixed white screen after lock-screen wake on Linux
- Fixed UI freeze during long-running high-frequency visualizations on Linux

## [0.8.0] - 2026-03-23

### Added

- Support simultaneous connections from Studio and SDK to the same device

### Changed

- Removed maximum connected devices limit (previously capped at 2)

### Fixed

- Fixed device connection state lost when switching views
- Fixed device count showing incorrect number after connecting (e.g., connecting 1 device but showing 2)
- Fixed 3D panel crash when enabling the Statistics toggle on macOS/Linux
- Fixed firmware upgrade step indicator still clickable after completion
- Fixed view switching not locked during firmware upgrade

## [0.7.0] - 2026-03-09

### Added

- MCAP recording: one-click start/stop recording with auto channel discovery, real-time quality monitoring (frame drop rate, sync offset), episode management and file explorer integration
- **Wuji Glove**: Hand model mesh overlay in 3D panel, supporting mesh visibility, opacity, wireframe mode, and color settings
- Layout preset system: save, switch, rename, delete, import/export panel layout presets with built-in defaults and tab bar shortcuts (Alt+1..9)
- Choose a custom device name when connecting for the first time
- Device rename now properly updates all data stream paths
- Topics like `tf` and `/tf_static` are now lifted from device-specific to global resources.

### Changed

- Improved device log panel performance for smooth experience at high log volumes

### Fixed

- Fixed Custom Transforms panel crash when non-numeric characters are entered in number input fields
- Fixed duplicate log entries appearing after device disconnect and reconnect
- Fixed topic updates being intermittently dropped in Raw Messages panel

## [0.6.0] - 2026-02-14

### Added

- **Wuji Glove**: Hand skeleton and fingertip pose visualization with per-finger confidence coloring, joint axis display, and opacity settings
- **3D Panel**: Tactile point cloud pressure coloring with standard colormaps (plasma, viridis, etc.) and exp/gamma transfer functions, consistent with Matrix panel visuals; HSL single-hue mode available as alternative
- Topic list now displays as a hierarchical tree grouped by namespace, with expandable schema fields and array-of-struct support
- Layout panel in visualization sidebar with one-click reset to default panel layout
- Centralized design token color system for unified theme color management
- Color Vision accessibility setting with support for protanopia, deuteranopia, and tritanopia color remapping
- Safety (Okabe-Ito) colorblind-friendly color scheme with theme-reactive 3D axis colors
- Show accumulated changelog between current and target firmware version during upgrade
- ImuData schema support for displaying IMU raw and fused data in the Raw Messages panel
- Device log panel with real-time defmt log display, auto-scroll, and pause support
- Log filtering by source (device/sdk/studio) and log level for focused debugging
- Bottom bar log panel toggle for quick access to device logs

### Changed

- Upgraded Cividis colormap to standards-compliant matplotlib 256-entry LUT
- Removed non-standard Thermal colormap; reordered colormaps to Viridis > Cividis > Safety > Plasma > Magma > Turbo
- Matrix panel default colormap changed to Viridis; EMF poses default changed to Safety
- Wuji Glove positioning quality metric "error" has been changed to "confidence" for increased intuition
- A new default configuration of 3D view in Visualization panel has been added to better suit the revised TF tree of Wuji Glove

### Fixed

- Improved UI consistency: unified shadows, error status color, search bar and dropdown styles
- Fixed Raw Messages diff background colors always showing light theme regardless of current theme
- Fixed a race condition where a recently connected device could be incorrectly reset to disconnected by the ghost detection mechanism

## [0.5.0] - 2026-02-09

### Added

- Desktop application for Wuji device management and data visualization
- Visualization panels: 3D view, Plot, Raw Message, Tactile Matrix
- Multi-device connection with device discovery and connection history
- Device command palette supporting reconnect, disconnect, rename, calibrate, export calibration data, and device info
- Firmware upgrade with device discovery, firmware download, progress tracking, and error diagnostics
- Local firmware file upload with version, release date, and release notes display
- Device naming dialog with automatic left/right hand detection
- 3D glove landmark visualization with positioning error mapped to point color
- 3D view custom TF transform support
- Pre-configured tactile zone layouts
- Light and dark theme support

[Unreleased]: https://github.com/wuji-technology/wuji-studio/compare/v0.9.0...HEAD
[0.9.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.8.0...v0.9.0
[0.8.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.7.0...v0.8.0
[0.7.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.6.0...v0.7.0
[0.6.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.5.0...v0.6.0
[0.5.0]: https://github.com/wuji-technology/wuji-studio/releases/tag/v0.5.0
