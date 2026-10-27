# LaptopBridge — Ficha de Microsoft Store preparada para revisión

**No enviada a certificación.** Debe ser aprobada por el titular y acompañada de capturas reales de la versión instalable. Este texto no confirma que la aplicación esté certificada.

## Español (es-MX)

**Nombre:** LaptopBridge

**Descripción breve:** Gestiona carpetas autorizadas desde Windows 11 y controla operaciones de archivos mediante herramientas locales con confirmación antes de eliminar.

**Descripción:**
LaptopBridge es una herramienta de escritorio para Windows 11 que te permite elegir y revocar las carpetas de trabajo a las que puede acceder un servidor local MCP. Incorpora funciones de exploración, lectura de archivos UTF-8, creación de archivos y directorios, edición con control de integridad, copia, movimiento, renombrado y restauración de respaldos. Antes de eliminar se solicita un plan y una confirmación visible desde el equipo. De forma predeterminada no existe ninguna carpeta autorizada. El servidor de herramientas emplea entrada/salida estándar; no publica por sí mismo un servicio web.

**Advertencia visible:** La conexión a un cliente MCP o un modelo de IA externo puede implicar compartir el contenido solicitado con ese proveedor. Los permisos del programa no equivalen a un sandbox de Windows.

**Funciones destacadas:**
- Permisos por carpeta concedidos y revocados localmente
- Lectura y edición de texto con controles de tamaño e integridad
- Copia, movimiento y renombrado en ubicaciones autorizadas
- Confirmación local de eliminación y respaldos recuperables
- Registro de operaciones local
- Interfaz MCP por stdio para clientes compatibles

## English (en-US)

**Name:** LaptopBridge

**Short description:** Manage permitted local folders in Windows 11 and control file operations through a local MCP tool server, with interactive confirmation before deletion.

**Description:**
LaptopBridge is a Windows 11 desktop utility that lets users select and revoke work folders accessible to a local MCP server. Features include folder listings, UTF-8 text reading, file and directory creation, integrity-checked edits, copy, move, rename and recovery snapshots. Before deleting a file, the app requests a deletion plan and an on-device approval. No folders are granted by default. The MCP server communicates over standard input/output, without hosting a public web listener.

**Disclosure:** A connected MCP client or remote AI provider may receive any file content that the client requests. LaptopBridge's built-in path controls do not create a Windows operating-system sandbox.

## Suggested review notes for Microsoft certification (English)

This is a classic desktop utility packaged as MSIX and requests the restricted `runFullTrust` capability because it executes a Tkinter-based user-facing permission manager and a separate Win32 MCP stdio command-line server. It does not request administrator elevation or publish network listening ports. The server has no tool to grant folder permissions; the user grants and revokes folders through the local graphical UI. Deletion requires a prior plan plus a separate locally displayed dialog in which the user must type ELIMINAR. The deployment should be checked for the execution alias `laptopbridge-mcp.exe` and shared per-user persistent settings. A directory-only permission mechanism is not OS-enforced sandboxing.

## Required before submitting

- Enter exact reserved Partner Center package identity (not the preview identity).
- Capture **at least one genuine Windows desktop screenshot** of the actual packaged app; ideal size 1366x768 or higher. Do not submit a generated mockup as a screenshot.
- Verify GUI and MCP alias inside the installed MSIX, including actual Trash/Recycle Bin operations on test data.
- Review and finalize PRIVACY.md with publishing contact and deletion/retention instructions. Microsoft may require a privacy policy due to the app's access to personal information.
- Enter accurate category, markets, pricing, rating answers, and support contact.
- Run Windows App Certification Kit and inspect the report; respond to any certification failures.
- Obtain Microsoft Store certification; install exclusively from the Microsoft Store on the target Windows 11 system with Smart App Control left enabled.

## Official references

https://learn.microsoft.com/en-us/windows/apps/publish/publish-your-app/msix/create-app-submission

https://learn.microsoft.com/en-us/windows/apps/publish/publish-your-app/msix/support-info

https://learn.microsoft.com/en-us/windows/apps/publish/publish-your-app/screenshots-and-images
