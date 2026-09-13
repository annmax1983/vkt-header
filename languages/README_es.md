# vkt-header

[English](../README.md) | [中文](README_zh.md) | Español | [Deutsch](README_de.md) | [日本語](README_ja.md) | [Français](README_fr.md)

Modificador global de cabeceras HTTP de solicitud para navegadores Chromium. Las reglas se comparan por **solo dominio** (sin distinción de mayúsculas/minúsculas, la ruta se ignora) y se aplican en **todas las pestañas** — no hay aislamiento por pestaña ni estado por pestaña.

> Chromium · Manifest V3 · Session Rules · Coincidencia por dominio · Global

---

## ¿Por qué vkt-header?

La mayoría de modificadores de cabeceras las cambian globalmente, o requieren un estado tedioso por pestaña. vkt-header lo mantiene simple: una regla se compara con el **dominio** de la URL solicitada y se aplica en todas partes, en todas las pestañas, en el momento en que se activa.

| Ventaja | Detalle |
|---------|--------|
| 🌐 **Coincidencia por dominio** | Las reglas comparan solo el dominio, sin distinción de mayúsculas/minúsculas. Las rutas se ignoran. |
| 🔗 **Cualquier pestaña** | Una regla se aplica en todas las pestañas — nada está vinculado a una pestaña específica. |
| 🌍 **Reglas globales** | Deja la URL de coincidencia vacía y la regla se aplica a **todas las solicitudes**. |
| 🧹 **Re-aplicación automática** | Las session rules desaparecen al reiniciar el navegador; vkt-header vuelve a aplicar todas las reglas activas automáticamente al iniciar el navegador. |
| ⚡ **Edición en línea** | Añade/edita cabeceras directamente en el panel lateral. Sin editor separado. |
| 🎯 **Preajustes** | Preajustes con un clic: iPhone, Android, iPad, Googlebot, Referer, X-Forwarded-For. |

---

## Funcionalidad principal: Coincidencia por dominio

Cada regla tiene un campo **URL de coincidencia**, pero solo se usa la parte del **dominio**:

- La comparativa es **sin distinción de mayúsculas/minúsculas** (`EXAMPLE.COM` = `example.com`)
- Las rutas se ignoran (`https://example.com/api` se comporta exactamente como `example.com`)
- El `www.` inicial es opcional — `https://www.cnblogs.com/` y `https://cnblogs.com/` coinciden con la misma regla
- Otros subdominios (`pic.cnblogs.com`, `blog.cnblogs.com`, …) **no** coinciden
- Interruptor opcional **Incluir subdominios**: cuando está activado, `example.com` también coincide con cada subdominio (`pic.example.com`, `api.example.com`, …)
- La regla se aplica en **todas las pestañas**, a cualquier solicitud cuyo dominio coincida
- **URL de coincidencia vacía** = la regla se aplica a **todas las solicitudes**

| Lo que escribes | Dominio efectivo | Se aplica a |
|---|---|---|
| `example.com` | example.com | example.com y www.example.com, cualquier ruta |
| `HTTPS://EXAMPLE.COM/api` | example.com | igual — la ruta se ignora |
| `https://www.cnblogs.com/` | cnblogs.com | cnblogs.com y www.cnblogs.com |
| `pic.cnblogs.com` | pic.cnblogs.com | Solo pic.cnblogs.com y www.pic.cnblogs.com |
| *(vacío)* | — | **todas las solicitudes** |

Activa una regla con su interruptor en el panel lateral. El interruptor maestro en la parte superior detiene o reanuda todas las reglas a la vez.

---

## Funcionalidades

| Funcionalidad | Descripción |
|---------|-------------|
| **Establecer / Añadir / Eliminar cabeceras** | Sobrescribe, añade a (Cookie, X-Forwarded-For…) o elimina cualquier cabecera |
| **Cabeceras de solicitud y respuesta** | Modifica cabeceras de solicitud y respuesta de forma independiente por regla |
| **Editor en línea** | Edita cabeceras directamente en el panel lateral — sin cambiar entre popup/panel |
| **Sistema de reglas** | Guarda múltiples configuraciones de cabeceras como reglas |
| **Vinculación por dominio** | Vincula reglas a un dominio (sin distinción de mayúsculas/minúsculas, ruta ignorada) |
| **Incluir subdominios** | Interruptor opcional: coincide con cada subdominio (`*.example.com`) |
| **Filtro por método** | Restringe una regla a un método HTTP (GET, POST, …) o déjala abierta |
| **Reglas globales** | URL de coincidencia vacía → se aplica a todas las solicitudes |
| **Etiquetas de URL** | Haz clic en el dominio de la página actual para rellenar automáticamente la URL de coincidencia |
| **Interruptores por regla** | Activa/desactiva cada regla de forma independiente; el interruptor maestro detiene todo |
| **Preajustes** | Añade rápidamente cabeceras comunes: UA móvil, UA de bot, Referer, XFF |
| **Cualquier pestaña** | Las reglas son globales — sin aislamiento por pestaña, sin interruptores por pestaña |
| **Session Rules** | Session rules de `declarativeNetRequest` — se borran al reiniciar, se vuelven a aplicar al iniciar el navegador |
| **Importar / Exportar** | Respaldo y restauración JSON de todas las reglas *(Premium)* |

---

## Casos de uso

| Escenario | Cómo |
|----------|-----|
| **Pruebas móviles** | Aplica el preajuste de UA de iPhone/Android/iPad para simular dispositivos móviles |
| **Depuración de APIs** | Establece Authorization, X-Custom-Header para solicitudes REST/GraphQL |
| **Pruebas de Referer** | Modifica la cabecera Referer para probar la protección contra hotlinking |
| **Pruebas geográficas** | Establece X-Forwarded-For para simular distintas IPs de cliente |
| **Pruebas CORS** | Modifica la cabecera Origin para probar políticas cross-origin |
| **Simulación de bots** | Aplica el UA de Googlebot para ver cómo los sitios responden a los rastreadores |

---

## Gratis vs Premium

| | Gratis | Premium |
|---|---|---|
| Reglas | 5 como máximo | Ilimitadas |
| Cabeceras por regla | 5 como máximo | Ilimitadas |
| Coincidencia por dominio | ✅ | ✅ |
| Reglas globales (URL vacía) | ✅ | ✅ |
| Importar / Exportar | ❌ Solo Premium | ✅ |
| Preajustes | ✅ | ✅ |

---

## Vista previa

<p align="center">
  <img src="screenshot/preview.png" alt="Vista previa de vkt-header" width="640">
</p>

---

## Navegadores compatibles

| Navegador | Estado | Versión mínima |
|---------|--------|------------------|
| Google Chrome | ✅ Totalmente compatible | Chrome 114+ (SidePanel API) |
| Microsoft Edge | ✅ Totalmente compatible | Edge 114+ |
| Otros navegadores basados en Chromium | ⚠️ Básico compatible | Debe soportar SidePanel API |

---

## Instalación

Por tu seguridad, instala vkt-header solo a través de las tiendas oficiales de extensiones del navegador:

1. Abre **Chrome Web Store** o **Microsoft Edge Add-ons**
2. Busca: `vkt-header`
3. Haz clic en **"Añadir a Chrome"** / **"Añadir a Edge"**
4. Haz clic en el icono 🔧 de vkt-header en tu barra de herramientas para abrir el panel lateral

> ⚠️ No instales desde sitios web de terceros. Las versiones no autorizadas pueden comprometer la seguridad de tus datos.

---

## Privacidad

vkt-header sigue principios de privacidad desde el diseño:

- ✅ Todas las reglas se almacenan en `chrome.storage.local` — **no se suben datos a ningún servidor**
- ✅ Las session rules se borran al reiniciar el navegador y se vuelven a aplicar automáticamente al iniciar el navegador
- ✅ Sin analíticas, sin rastreo, sin cookies
- ✅ Algunas cabeceras (Host, Origin) están protegidas por el navegador y no pueden modificarse
- ✅ Solo para fines de desarrollo y depuración

### Permisos

| Permiso | Razón |
|------------|--------|
| `storage` | Guardar reglas de cabeceras y configuración localmente |
| `activeTab` | Acceder a la pestaña actual (ej. para leer su URL en el panel lateral) |
| `sidePanel` | Mostrar la interfaz de la extensión en un panel lateral |
| `declarativeNetRequestWithHostAccess` | Modificar cabeceras de solicitud HTTP |
| `tabs` | Leer la URL de la pestaña activa para la funcionalidad de etiqueta de dominio |

- [Política de privacidad completa](https://annmax1983.github.io/vkt-header/privacy-policy.html)

---

## Preguntas frecentes

1. **¿Las cabeceras no se aplican después de activar una regla?**
   Intenta recargar la página. Las session rules de DNR se aplican a nuevas solicitudes, no a recursos ya cargados.

2. **¿Las reglas desaparecen al reiniciar el navegador?**
   Las session rules se borran al reiniciar por diseño, y vkt-header vuelve a aplicar automáticamente todas las reglas activas al iniciar el navegador.

3. **¿Algunas cabeceras no se pueden modificar?**
   Las cabeceras protegidas por el navegador (Host, Origin, etc.) no pueden ser modificadas por extensiones. Es una restricción de seguridad del navegador, no un error.

4. **¿Cómo transfiero reglas a otro dispositivo?**
   Abre Configuración → Exportar para descargar un respaldo JSON, luego impórtalo en el otro dispositivo.

5. **¿La página principal / primera navegación no muestra la cabecera?**
   Las reglas DNR no se aplican a solicitudes servidas desde la caché del navegador. Después de activar una regla, recarga la página forzadamente (Ctrl+Shift+R) o vuelve a abrirla — la solicitud de navegación llevará la cabecera. Los sub-recursos en caché se comportan igual.

6. **¿Cabeceras que faltan justo después de iniciar el navegador?**
   El service worker se activa de forma diferida: las primeras solicitudes pueden dispararse antes de que vkt-header haya vuelto a aplicar sus session rules. Reintenta o recarga — todas las navegaciones posteriores llevan las cabeceras. Esto solo afecta a los primeros momentos después del inicio del navegador, no a la navegación normal.

---

## Aviso de derechos de autor

1. Esta extensión modifica las cabeceras de solicitud HTTP solo para fines de desarrollo y depuración. Todo el contenido y los servicios de los sitios web visitados pertenecen a sus respectivos propietarios.
2. Los usuarios no deberían usar esta extensión para eludir restricciones de seguridad de sitios web, acceder a contenido no autorizado o participar en actividades ilegales.
3. Los usuarios deberán cumplir con las leyes locales y los términos de servicio de las plataformas al usar esta extensión.

---

## Aviso sobre el código fuente

> ⚠️ **Este repositorio no publica código fuente.** Contiene únicamente documentación de uso, notas de lanzamiento y recursos de soporte. La extensión se distribuye exclusivamente a través de Chrome Web Store. No se proporcionan paquetes de instalación sin conexión ni código fuente para usuarios finales.

---

## Licencia

Copyright © 2026 vkt-header. Todos los derechos reservados.

Este software es de código cerrado y propietario. Sin autorización escrita oficial, quedan estrictamente prohibidos:
- Descompilar, piratear o modificar el código del programa
- Reempaquetar, redistribuir, compartir o reventa comercial
- Incorporar el programa a otro software para distribución conjunta

---

## ❤️ Apoyo

Si te resulta útil vkt-header, ¡considera invitar al desarrollador a un café!

**[👉 Haz clic aquí para apoyar](https://ko-fi.com/annmax?buyACoffee=true&ref=vkt-header)**
