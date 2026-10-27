# LaptopBridge Desktop — Windows 11

**Estado comprobado (27 de octubre de 2026): compilación Windows y generación de MSIX preview correctas; aún NO se ha firmado, certificado ni publicado.**

## Resultado de GitHub Actions

- [Ejecución #2 — SUCCESS](https://github.com/tattoosarah23-tech/LaptopBridge/actions/runs/40499375311)
- 29 pruebas automáticas, ejecutables `LaptopBridge-Control.exe` y `LaptopBridge-MCP.exe`, prueba MCP e inventario PE correctos.
- `LaptopBridge_1.4.0.0_x64_PREVIEW_UNSIGNED_NOT_INSTALLABLE.msix` creado y validado mediante MakeAppx pack/unpack.
- SHA-256 del MSIX interno: `B9B91A9CDDF4807154A82CFBD4DEFB4AD0CF7167A33BD1FC6D37B9EFAA0C0F4D`.
- Artefactos temporales de compilación: **SIN FIRMA — NO INSTALAR NI DESACTIVAR SMART APP CONTROL**.

## Organización actual

Este repositorio contiene el archivo fuente `LaptopBridge_Desktop_v1_4_PROYECTO_MSIX_COMPLETO.zip` y el workflow `.github/workflows/windows-build.yml`. El workflow comprueba la huella del ZIP, extrae los archivos en Windows y genera los binarios de prueba.

## Qué hace la aplicación

Panel local para autorizar o revocar carpetas, servidor MCP stdio, lectura/escritura/copias/movimientos, respaldos, plan de borrado y confirmación local con la palabra ELIMINAR. No autoriza ninguna carpeta de forma predeterminada. Las políticas son controles del programa, **no** un sandbox del sistema operativo.

## Para producir la versión certificable

1. Tener una cuenta de desarrollador habilitada en [Partner Center](https://partner.microsoft.com/dashboard).
2. **New product → MSIX or PWA app**, reservar `LaptopBridge` si está disponible.
3. Obtener en **Product management → Product identity** los valores exactos: **Package/Identity/Name**, **Package/Identity/Publisher**, **PublisherDisplayName**.
4. Ir a [Actions](https://github.com/tattoosarah23-tech/LaptopBridge/actions/workflows/windows-build.yml) → **Run workflow** → establecer `store_submission=true` e ingresar la identidad. Nunca usar valores inventados.
5. Si la compilación termina correctamente, descargar el artefacto `STORE_SUBMISSION_UNSIGNED.msix`, revisar con el Windows App Certification Kit, completar privacidad y ficha en Partner Center y enviarlo para certificación. La firma para la distribución por Store la efectúa Microsoft al aprobar.
6. **Solo después de publicarse**, instalar desde Microsoft Store en un Windows 11 con Smart App Control activado y probar con una carpeta vacía autorizada localmente.

## Bloqueos conocidos

- Identidad de Partner Center no proporcionada.
- Aún no probado instalado con identidad de MSIX, ni ejecutado Windows App Certification Kit.
- Sin aprobación de certificación ni instalación final en la laptop.
- Conexión específica de ChatGPT aún no implementada o validada (el servidor es MCP stdio local).
- La política de archivos requiere auditoría de seguridad independiente antes de confiarle archivos importantes, por posibles condiciones de carrera en rutas Windows.

## Documentación

- [Instrucciones detalladas de publicación](docs/ENTREGA_Y_PUBLICACION.md)
- [Política de privacidad propuesta](PRIVACY.md) — revisar y aprobar antes de publicar.

**Protecciones Windows:** No desactivar Smart App Control, Defender o SmartScreen; no instalar ni abrir artefactos no firmados.
