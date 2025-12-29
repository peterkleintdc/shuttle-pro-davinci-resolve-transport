# Changelog

All notable changes to this project will be documented in this file.

The format is inspired by [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project follows semantic versioning.

---

## [1.0.0] – Initial Public Release

### Added
- Advanced jog/shuttle transport logic based on DaVinci Resolve native **J / K / L** playback
- Smooth playback speed ramping (0.25× → 0.5× → 1× → 2×+)
- Immediate stop behavior when returning shuttle to center position
- Jog dial mapped to mouse scroll for timeline navigation and zooming
- Complete button mapping for editing, transport, selection, and mouse interaction
- Support for left-hand Shuttle Pro + right-hand touchpad workflows

### Documented
- Requirement to release mouse-hold (Button 2) using Button 1
- Requirement to assign a custom keyboard shortcut for **Split Clip** in DaVinci Resolve
- Timeline scroll and zoom behavior depending on cursor focus

### Philosophy
- Transport-first, muscle-memory-driven editing workflow
- Compact, mouse-free editing optimized for laptops and small desks
- Designed as a reference implementation rather than a generic preset

---

## [Unreleased]

### Planned
- Optional alternative button layouts
- Additional macro presets for large timeline jumps
- Version-specific notes for future DaVinci Resolve releases

