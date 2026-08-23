# vkt-header
[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Modificador global de cabeceras HTTP para navegadores Chromium. Las reglas coinciden solo por **dominio** (sin distinguir mayúsculas/minúsculas, se ignoran las rutas) y se aplican en **cada pestaña** — sin aislamiento por pestaña ni estado por pestaña.

> Chromium · Manifest V3 · Reglas de sesión · Coincidencia por dominio · Global

---

## Función principal: coincidencia por dominio

Cada regla tiene un campo **Match URL**, pero solo se usa la parte del **dominio**:

- Coincidencia **sin distinción de mayúsculas/minúsculas** (`EXAMPLE.COM` = `example.com`)
- Se ignoran las rutas (`https://example.com/api` se comporta como `example.com`)
- El `www.` inicial es opcional — `https://www.cnblogs.com/` y `https://cnblogs.com/` coinciden con la misma regla
- Otros subdominios (`pic.cnblogs.com`, `blog.cnblogs.com`, …) **no** coinciden
- La regla se aplica en **cada pestaña** a cualquier petición cuyo dominio coincida
- **Match URL vacío** = la regla se aplica a **todas las peticiones**

| Lo que escribes | Dominio efectivo | Se aplica a |
|---|---|---|
| `example.com` | example.com | todas las peticiones a example.com, cualquier ruta |
| `HTTPS://EXAMPLE.COM/api` | example.com | igual — la ruta se ignora |
| *(vacío)* | — | **todas las peticiones** |

Activa cada regla con su interruptor en el panel lateral. El interruptor principal detiene o reanuda todas las reglas.

---

## Funciones

| Función | Descripción |
|---|---|
| 🔧 **set / remove** | Establecer o eliminar cabeceras |
| ✏️ **Editor inline** | Editar directamente en el panel lateral |
| 📋 **Sistema de reglas** | Guardar múltiples configuraciones |
| 🌐 **Vinculación por dominio** | Vincular reglas a dominios (sin mayúsculas, rutas ignoradas) |
| 🌍 **Reglas globales** | Match URL vacío → se aplica a todas las peticiones |
| 🏷️ **Etiquetas de dominio** | Clic en el dominio actual para autocompletar |
| 🔘 **Interruptores** | Activar/desactivar cada regla; el interruptor principal detiene todo |
| 🔗 **Cada pestaña** | Reglas globales — sin aislamiento por pestaña |
| 🧹 **Reglas de sesión** | Se limpian al reiniciar y se reaplican al iniciar |
| 📥📤 **Import/Export** | Backup JSON |

---

## Aviso de código fuente

> ⚠️ **Este repositorio no publica el código fuente.** Contiene únicamente documentación de uso, notas de versión y recursos de soporte. La extensión se distribuye exclusivamente a través de Chrome Web Store. No se proporcionan paquetes de instalación sin conexión ni código fuente para usuarios finales.


## ❤️ Apoyo

**[👉 Apoyar vkt-header](https://annmax1983.github.io/vkt-header/)**
