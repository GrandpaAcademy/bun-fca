# Changelog

All notable changes to **Bun-FCA** will be documented in this file.

## [2.0.0] - 2026-04-18

### ✨ Major Bun Port
- 🚀 **Initial Bun Release**: Complete migration of the ST-FCA library to the Bun runtime.
- ⚡ **Native Networking**: Replaced the legacy `request` and `bluebird` stack with Bun's native `fetch` API.
- 🍪 **BunCookieJar Implementation**: Engineered a custom synchronous cookie management layer to bridge `tough-cookie` with the library's legacy expectations.
- 🛡️ **Initialization Hardening**: Improved `appstate` loading reliability and error reporting.
- 📦 **Dependency Streamlining**: Removed legacy Node-only dependencies and optimized package resolution for Bun.

---

## [1.0.5] - 2025-01-13

### Added
- 🔄 Comprehensive update system that properly syncs all files
- 📂 Automatic file tree comparison between local and GitHub
- ➕ Smart file addition for new files in updates
- ♻️ Automatic modification detection and update
- 🗑️ Automatic deletion of removed files from old versions
- 🎯 No backup folder creation - cleaner updates

### Changed
- Improved update mechanism to handle version jumps (e.g., 1.0.3 → 1.0.6)
- Enhanced file synchronization to ensure no missing files
- Better error handling during updates
- Auto-restart after successful update

### Fixed
- Missing files when updating across multiple versions
- Outdated files not being properly replaced
- Orphaned files from old versions not being cleaned up

---

**Maintained & Ported by Grandpa Academy**  
GitHub: https://github.com/GrandpaAcademy/bun-fca
