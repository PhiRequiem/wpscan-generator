# WPScan Command Generator

Generador visual de comandos WPScan. Selecciona las opciones y copia el comando listo para ejecutar.  
No envía datos a ningún servidor. No ejecuta nada. 100% offline.

**[Demo en vivo →](https://phirequiem.github.io/wpscan-generator/)**

---

## Uso

Abre directamente en cualquier navegador moderno — sin servidor, sin instalación, sin internet.

```bash
git clone https://github.com/PhiRequiem/wpscan-generator
open wpscan-generator/index.html
```

O descarga solo `index.html` y ábrelo.

---

## Funcionalidades

| | |
|---|---|
| **Versiones** | Soporte completo para WPScan v4.0 (por defecto) y v3.x |
| **Enumeración** | Las 12 opciones de `-e` con descripciones y tooltips |
| **Detección de conflictos** | Avisa cuando se combinan opciones incompatibles (ej. `vp + ap`) |
| **Modos de detección** | Global (passive / mixed / aggressive) + overrides por tipo |
| **Fuerza bruta** | Usuarios, contraseñas, tipo de ataque, `--wordlist-skip` para reanudar |
| **HTTP / Red** | Proxy, autenticación, user-agent, `--proxy-target-only`, SAML |
| **Output** | `json`, `jsonl` streaming en tiempo real, `cli-no-color`, `xml` |
| **API Token** | Guardado opcional en localStorage con advertencia del navegador |
| **Presets** | Rápido, Completo, Stealth, Con Auth |
| **Vista previa** | Comando con sintaxis coloreada y copia con un clic |
| **Cambio de versión limpio** | Al cambiar entre v4/v3 se limpian automáticamente los parámetros exclusivos de la versión anterior |

---

## Novedades v4.0

Funcionalidades de WPScan v4.0 reflejadas en la herramienta:

| Funcionalidad | Flag |
|---|---|
| Escaneo autenticado vía REST API | `--wp-auth` |
| Reanudar fuerza bruta desde un offset | `--wordlist-skip` |
| Reintentos automáticos de requests fallidos | `--max-retries` |
| Proxy solo para el target | `--proxy-target-only` |
| Sitios con autenticación SAML | `--expect-saml` |
| Excluir IDs de vulnerabilidades | `--exclude-vulns` |
| Enumeración de carpetas de backup | `-e bf` |
| Output streaming en tiempo real | `--format jsonl` |
| Escaneo mínimo por defecto (cambio breaking) | sin plugins ni config backups automáticos |

**Eliminados en v4.0** (solo disponibles en modo v3):  
`--config-backups-detection`, `--db-exports-detection`, `--timthumbs-detection`, `--medias-detection`

---

## WPScan

- **Web oficial:** [wpscan.com](https://wpscan.com/)
- **Instalación:** [github.com/wpscanteam/wpscan#installation](https://github.com/wpscanteam/wpscan#installation)
- **Obtener API Token (gratis):** [wpscan.com/register](https://wpscan.com/register)

El API Token es necesario para obtener información de vulnerabilidades de la base de datos de WPScan. El plan gratuito incluye 25 consultas diarias.

---

## Stack

HTML + CSS + JavaScript plano — sin frameworks, sin build step, sin dependencias.  
Archivo único: `index.html` + `favicon.svg`.

---

## Licencia

MIT
