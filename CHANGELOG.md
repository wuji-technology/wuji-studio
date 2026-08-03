# Changelog

All notable changes to Wuji Studio will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

## [2026.8.3]

### Added

- **In-app updates**: Settings > About now shows the current version and installs new releases without leaving Studio. A Version History dialog lets you install a specific version, and update notifications open the in-app update flow directly.

### Fixed

- **Extensions**: Installing an extension from a `.wsix` file no longer strips executable permissions from the files inside it. Extensions that ship their own helper program failed to start after being installed this way. Installing the same extension from a folder was unaffected.
- **Firmware upgrade**: Fixed successful upgrades occasionally being reported as failed.
- **Device connection**: Connecting a Wuji Hand 2 no longer falsely reports "read-only mode".
- Fixed Hand Skeleton visibility in the 3D panel — joints and bones now stay visible when the hand mesh is enabled.

## [2026.7.16]

### Fixed

- Fixed some known issues

## [2026.7.15]

### Fixed

- **Online services**: Restored packaged Studio access to firmware information from Wuji's default API, update checks, and the extension marketplace, without allowing arbitrary network origins.

## [2026.7.14]

### Added

- **User data import and export**: Added export and import of user data — calibration hand models, tactile models, and captured runs — as a portable `.zip` from the user avatar menu. Import previews the archive, shows its owner, and warns that it overwrites matching data before you confirm. Data is restored to the archive's owner profile, which is created if it doesn't exist, and you can switch to that profile afterward. Desktop app only.

### Changed

- **Breaking change — Calibration**: Changed the calibration file format. Files created before this release are not compatible and are not migrated — calibrate the left and right hands again after upgrading.
- Changed where calibration results are saved: each result now belongs to the selected Wuji Studio user and hand, and Wuji Gloves for the same hand share that user's result.
- Renamed **Hand Profile** to **Hand Model Source**. The legacy Wuji Hand and Wuji Hand 2 profiles are deprecated. Existing layouts now show **SDK Managed**, which uses the matching calibrated model or the SDK default. **Custom URDF** remains available.

### Fixed

- **Calibration**: Fixed cases where a compatible Wuji Glove could appear unsupported or show the wrong calibration status. When the status cannot be checked, Wuji Studio now offers a retry.
- **Wuji Glove**: Blocked incompatible legacy tactile recordings during playback and added a clear warning, avoiding incorrect tactile rendering.
- **Tactile alerts**: Playing back tactile recordings in the older format (before v2026.6.18) shows an incompatibility warning as a message notification in the bottom-right corner.
- **Wuji Glove**: Fixed tactile matrix panels still rendering the old 24×32 preset layout after an in-place upgrade. The layout now migrates on startup, and custom column counts are preserved.
- **Firmware upgrade**: Grouped devices in the upgrade view by their actual product type, so Wuji Hand devices no longer appear under the "Wuji Glove" group. Unrecognized devices now appear under a new "Other Devices" group.

## [2026.7.1]

### Changed

- Updated the default Hand Skeleton URDF snapshots used by the bundled device SDK to the latest caliber versions.
- Restricted calibration to local user profiles — starting calibration as the SDK Default user is no longer allowed.

### Fixed

- Fixed Wuji Hand 2 firmware upgrade getting stuck at 95% during the upgrade reconnect.

## [2026.6.18]

### Changed

- **Wuji Glove**: Updated the tactile matrix and per-zone matrix panels to display the new 24×31 (744) layout (was 24×32, 768).
- **Wuji Glove**: MCAP playback now rejects legacy 24×32 (768) or corrupted tactile recordings at decode time and shows a warning, instead of rendering them at the wrong dimensions.

## [2026.6.15]

### Added

- Added **Modify Device Port** command in Device Tools to change a connected device's UDP data port from the device menu or command palette. The device reboots to apply.
- Added `wujistudio.recording` extension API so authorized extensions can start, inspect, and stop Studio-managed recordings with optional source or topic selection.
- Added Hand Skeleton profile switching in the 3D panel between **wujihand**, **wujihand2**, and **Custom URDF**. Selecting Custom URDF lets you enter a local URDF path for SDK-side IK solving. Switching back to wujihand or wujihand2 clears the custom override.
- Added a current-device debug recording at calibration start for later troubleshooting.

### Changed

- Restricted **Modify Device IP** in Device Tools to private (RFC1918) subnets (`10/8`, `172.16/12`, `192.168/16`). Public, loopback, link-local, and other reserved addresses are now rejected.
- Updated `wujistudio.devices.subscribeTopic(...)` to require the `robotics.topics.read` permission. Extensions that subscribe to device topics must add `"robotics.topics.read"` to `wujistudio.extension.json` under `permissions`.
- Updated the bundled device SDK integration for user-scoped calibration and SDK-managed hand profile selection.

### Fixed

- Fixed point cloud colors in the 3D panel appearing scrambled and washed-out or semi-transparent. Point cloud coloring now renders correctly and matches the selected color map.
- Fixed device logs not resuming after the device passively reconnects (for example, after a firmware-upgrade restart).

## [2026.6.2]

### Added

- Added local MCAP replay so recorded `.mcap` files open and play back directly in Studio.

### Changed

- Matrix panel: "Flip Horizontal / Flip Vertical" now mirror cell data only; row and column header indices stay in natural order, keeping alignment with the physical sensor layout.
- Visualization now loads built-in and extension panels through a single unified path.
- Improved recording and replay workflows, including episode handling and playback controls.
- Improved extension support with broader data access, custom views, and permission settings.

### Fixed

- Fixed native video preview and replay stability issues.

## [2026.5.18]

### Added

- Added the Extensions view with separate Development, Installed, and Built-in sections, including local extension loading, directory scanning, install/uninstall actions, and clearer override warnings.
- Added preinstalled first-party extensions for calibration, teleoperation, and device tools so packaged Studio builds can include these capabilities out of the box.
- Added extension-provided welcome content and view title actions, so extension views can show empty-state guidance and toolbar commands consistently.

### Changed

- Improved the Extensions page with clearer extension status, source labels, details, manifest viewing, and source-specific actions.
- Improved extension support so plugins integrate more reliably with the visualization view.

### Fixed

- Fixed layout presets, saved layouts, and user preferences being blank after a fresh install on Linux (caused by the WebView data directory not being created before first use)
- Fixed URDF local file loading failing on Windows in the 3D panel
- Fixed URDF meshes not tracking `/joint_states` in real time (mesh stayed in bind pose)

## [0.10.0] - 2026-04-27

### Added

- Auto-checks for Studio and device firmware updates, surfacing new versions in a toast and the notification center, with one-click navigation to the download page or upgrade view

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

[Unreleased]: https://github.com/wuji-technology/wuji-studio/compare/v2026.8.3...HEAD
[2026.8.3]: https://github.com/wuji-technology/wuji-studio/compare/v2026.7.16...v2026.8.3
[2026.7.16]: https://github.com/wuji-technology/wuji-studio/compare/v2026.7.15...v2026.7.16
[2026.7.15]: https://github.com/wuji-technology/wuji-studio/compare/v2026.7.14...v2026.7.15
[2026.7.14]: https://github.com/wuji-technology/wuji-studio/compare/v2026.7.1...v2026.7.14
[2026.7.1]: https://github.com/wuji-technology/wuji-studio/compare/v2026.6.18...v2026.7.1
[2026.6.18]: https://github.com/wuji-technology/wuji-studio/compare/v2026.6.15...v2026.6.18
[2026.6.15]: https://github.com/wuji-technology/wuji-studio/compare/v2026.6.2...v2026.6.15
[2026.6.2]: https://github.com/wuji-technology/wuji-studio/compare/v2026.5.18...v2026.6.2
[2026.5.18]: https://github.com/wuji-technology/wuji-studio/compare/v0.10.0...v2026.5.18
[0.10.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.9.0...v0.10.0
[0.9.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.8.0...v0.9.0
[0.8.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.7.0...v0.8.0
[0.7.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.6.0...v0.7.0
[0.6.0]: https://github.com/wuji-technology/wuji-studio/compare/v0.5.0...v0.6.0
[0.5.0]: https://github.com/wuji-technology/wuji-studio/releases/tag/v0.5.0
