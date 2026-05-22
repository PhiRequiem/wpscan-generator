# Changelog

## [1.1.0] - 2026-05-21

### Added
- localStorage support for API token — opt-in checkbox with browser storage warning
- Incompatibility validation for `--enumerate` groups: `vp/ap/p` and `vt/at/t` are mutually exclusive; conflicting options are highlighted in red with an explanatory banner
- Version toggle (v3.x / v4.0) — shows and hides options accordingly throughout the entire UI
- WPScan v4.0 new flags: `--wp-auth`, `--wordlist-skip`, `--max-retries`, `--proxy-target-only`, `--expect-saml`, `--exclude-vulns`
- New enumeration option: `-e bf` (backup folders, v4.0)
- New output format: `jsonl` real-time streaming (v4.0)
- v3.x-only detection options restored in v3 mode: `--config-backups-detection`, `--db-exports-detection`, `--timthumbs-detection`, `--medias-detection`
- Preset "Con Auth" using `--wp-auth`
- Tooltips on every option with usage details
- SVG icon set (inline, offline-compatible) replacing all emoji
- Favicon (`favicon.svg`)

### Fixed
- Removed invalid `-e ii` enumeration option that caused `Scan Aborted: Unknown choice: ii`
- Preset "Completo" no longer selects `vp + ap` simultaneously (incompatible)

### Changed
- Light mode UI
- Font sizes increased for readability; text contrast improved
- `--detection-mode mixed` is no longer emitted when it is the default value

---

## [1.0.0] - 2026-05-21

### Added
- Initial release
- URL, API token, enumeration, detection, performance, brute force, HTTP/network, output, and advanced sections
- Presets: Quick, Full, Stealth
- Real-time syntax-highlighted command preview with copy to clipboard
- 100% offline — single HTML file, no external dependencies
