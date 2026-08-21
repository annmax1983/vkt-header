# vkt-header
[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Modificador de cabeceras HTTP aislado por pestaña con URL matching para navegadores Chromium.

> Chromium · Manifest V3 · Reglas de sesión · Aislamiento por pestaña · URL Matching

---

## Función principal: URL Matching

Cada perfil tiene un campo **Match URL**. Al abrir el panel lateral, se detectan automáticamente los perfiles coincidentes.

**Prioridad de coincidencia:**

| Prioridad | Perfil MatchURL | URL de página | Puntos |
|---|---|---|---|
| 🥇 Exacta | `https://api.example.com/v1/users` | `https://api.example.com/v1/users` | 1000 |
| 🥈 Prefijo de ruta | `https://api.example.com/v1` | `https://api.example.com/v1/users` | 500+ |
| 🥉 Solo dominio | `https://api.example.com/` | `https://api.example.com/v1/users` | 100 |

- Coincidencia de dominio **sin distinción de mayúsculas/minúsculas**
- URLs más largas/específicas tienen mayor prioridad
- Barra verde de **sugerencia** con aplicación en un clic

---

## Funciones

| Función | Descripción |
|---|---|
| 🔧 **set / remove** | Establecer o eliminar cabeceras |
| ✏️ **Editor inline** | Editar directamente en el panel lateral |
| 📋 **Sistema de perfiles** | Guardar múltiples configuraciones |
| 🔗 **Vinculación URL** | Vincular perfiles a URLs |
| 🏷️ **URL Tags** | Clic en dominio/ruta para auto-rellenar |
| 🎯 **Sugerencia** | Detección automática de perfiles |
| ⚡ **Presets** | iPhone, Android, iPad, Googlebot, Referer, XFF |
| 🔒 **Aislamiento** | Estrictamente por tabId |
| 🧹 **Reglas de sesión** | Se limpian al reiniciar |
| 📥📤 **Import/Export** | Backup JSON |

---

---

## Aviso de código fuente

> ⚠️ **Este repositorio no publica el código fuente.** Contiene únicamente documentación de uso, notas de versión y recursos de soporte. La extensión se distribuye exclusivamente a través de Chrome Web Store. No se proporcionan paquetes de instalación sin conexión ni código fuente para usuarios finales.


## ❤️ Apoyo

**[👉 Apoyar vkt-header](https://annmax1983.github.io/vkt-header/)**
