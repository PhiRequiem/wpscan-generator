# Changelog

## [1.5.0] - 2026-05-25

### Fixed
- `shellQuote` solo cotizaba valores con espacios y no escapaba comillas simples internas — un valor como `my list's.txt` producía shell roto o inyección; ahora la función envuelve en comillas simples y escapa las internas con `'\''`, y también activa el cotizado para cualquier metacarácter de shell (`$`, backtick, `;`, `|`, `"`, etc.)
- `--user-agent` era el único campo usando comillas dobles en lugar de `shellQuote`, exponiendo la expansión de variables de shell (`$VAR`) e inyección de argumentos mediante `"`; ahora usa `shellQuote` consistentemente
- `--url`, `--proxy`, `--login-uri`, `--password-attack` y `--api-token` no pasaban por `shellQuote` a pesar de ser campos de texto libre; ahora todos los valores user-supplied se shell-cotizan
- El set `sens` (indicador de color rojo para credenciales) almacenaba los valores sin cotizar, pero `renderCmd` los comparaba contra los valores ya cotizados del comando — credenciales con espacio se mostraban en naranja en lugar de rojo; ahora `sens` almacena los valores en su forma cotizada
- El conflicto `--stealthy` + `aggressive` no resaltaba en rojo los controles responsables (el toggle Stealthy y el radio aggressive) porque el sentinel `__stealthy_aggressive__` nunca coincidía con ningún `.check-item`; ahora se aplica `.conflict` directamente a esos elementos con CSS específico para `.radio-item.conflict` y `.toggle-item.conflict`

---

## [1.4.0] - 2026-05-22

### Fixed
- Conflicto `--stealthy` + `aggressive` nunca se mostraba ni deshabilitaba el botón Copiar — `isStealthy` se computaba después de que `hasConflict` ya estaba fijado; movido antes de la evaluación
- Rutas de archivo (`--usernames`, `--passwords`, `--output`) y credenciales (`--proxy-auth`, `--http-auth`) con espacios no se cotizaban para la shell — ahora se envuelven en comillas simples automáticamente
- `setVersion` aplicaba `display:none` a elementos `<option>` vía el loop `[data-v4only]`, lo cual Firefox ignora; el loop ahora salta `<option>` (el `disabled` explícito ya era el guard funcional correcto)

---

## [1.3.0] - 2026-05-21

### Fixed
- `ENUM_GROUPS` se declaraba dentro de `generate()` recreándose en cada keystroke — movido a constante de módulo
- `copyCommand()` no verificaba el estado `disabled` del botón — un llamado directo podía copiar un comando inválido
- `--wp-auth` con Application Passwords (que contienen espacios) no se escapaba para la shell — ahora se envuelve en comillas simples automáticamente cuando el valor contiene espacios
- Los dos loops de detección de conflictos hacían el mismo trabajo — unificados en un solo `forEach`
- `userRange` / `mediaRange` tenían `width:180px` fijo — cambiado a `max-width` para no romper en móvil

### Added
- Los toggles **Random User-Agent** y **No Banner** se dimean visualmente con badge `vía --stealthy` cuando `--stealthy` está activo, indicando que ya están cubiertos
- Conflicto detectado cuando `--stealthy` + modo de detección `aggressive` están activos simultáneamente (contradicción: stealthy implica passive)

---

## [1.2.0] - 2026-05-21

### Fixed
- Preset "Con Auth" seleccionaba `vp+ap` y `vt+at` simultáneamente, generando conflicto inmediato al aplicarlo
- `--stealthy` emitía flags redundantes: ya implica `--detection-mode passive`, `--random-user-agent` y `--no-banner`; ahora esos flags se suprimen automáticamente cuando stealthy está activo
- Comando seguía generándose (y siendo copiable) aunque hubiera conflictos de enumeración; ahora el botón copiar se deshabilita y el terminal muestra borde rojo
- El tick interno del checkbox no cambiaba de color al entrar en conflicto
- `display:none` duplicado en los inline styles de `#saveTokenNotice` y `#enumConflict`

### Added
- Rango de usuarios `-e u[1-X]`: campo para especificar hasta qué ID de usuario enumerar (default 25)
- Rango de medios `-e m[1-X]`: campo para especificar el rango de IDs de media (default 100)
- `<meta name="description">` para GitHub Pages / SEO

---

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
