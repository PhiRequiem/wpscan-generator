# WPScan Command Generator

A single-file web app for building WPScan CLI commands visually.  
No data is sent anywhere. No commands are executed. 100% offline.

**[Live demo →](https://phirequiem.github.io/wpscan-generator/)**

---

## Usage

Open directly in any modern browser — no server, no install, no internet required.

```bash
git clone https://github.com/phirequiem/wpscan-generator
open wpscan-generator/index.html
```

Or just download `index.html` and open it.

---

## Features

| | |
|---|---|
| **Version toggle** | Switch between WPScan v4.0 (default) and v3.x |
| **Enumeration** | All 12 `-e` options with descriptions and tooltips |
| **Conflict detection** | Warns when incompatible options are combined (e.g. `vp + ap`) |
| **Detection modes** | Global (passive / mixed / aggressive) + per-type overrides |
| **Brute force** | Usernames, passwords, attack type, `--wordlist-skip` to resume |
| **HTTP / Network** | Proxy, auth, user-agent, `--proxy-target-only`, SAML support |
| **Output** | `json`, `jsonl` real-time streaming, `cli-no-color`, `xml` |
| **API token storage** | Opt-in localStorage save with browser warning |
| **Presets** | Quick, Full, Stealth, With Auth |
| **Command preview** | Syntax-highlighted, one-click copy |

---

## WPScan v4.0 support

Key v4.0 changes reflected in this tool:

| Feature | Flag |
|---|---|
| Authentication-based scanning via REST API | `--wp-auth` |
| Resume brute force from a line offset | `--wordlist-skip` |
| Auto-retry failed requests | `--max-retries` |
| Route only the target through the proxy | `--proxy-target-only` |
| SAML-authenticated sites | `--expect-saml` |
| Exclude specific vulnerability IDs | `--exclude-vulns` |
| Backup folders enumeration | `-e bf` |
| Real-time streaming output | `--format jsonl` |
| Minimal default scan (breaking change) | no auto plugins / config backups |

**Removed in v4.0** (shown only in v3 mode):  
`--config-backups-detection`, `--db-exports-detection`, `--timthumbs-detection`, `--medias-detection`

---

## Stack

Plain HTML + CSS + JavaScript — no frameworks, no build step, no dependencies.  
Single file: `index.html` + `favicon.svg`.

---

## License

MIT
