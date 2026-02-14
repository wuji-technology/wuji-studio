# Changelog

All notable changes to Wuji Studio will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

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

[Unreleased]: https://github.com/wuji-technology/wuji-studio/compare/v0.6.0...HEAD
[0.6.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.5.0...v0.6.0
[0.5.0]: https://github.com/wuji-technology/wuji-studio/releases/tag/v0.5.0
