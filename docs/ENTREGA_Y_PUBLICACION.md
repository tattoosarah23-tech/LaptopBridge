# LaptopBridge — Entrega, identidad Microsoft Store y validación

## Situación real

- GitHub Actions: [run 40499375311, SUCCESS](https://github.com/tattoosarah23-tech/LaptopBridge/actions/runs/40499375311).
- 29 pruebas pasadas en Windows hosted runner; dos ejecutables creados y MCP smoke test OK.
- Vista previa MSIX: `LaptopBridge_1.4.0.0_x64_PREVIEW_UNSIGNED_NOT_INSTALLABLE.msix`. No instalable en Windows protegido.
- No se ha creado ni enviado paquete con identidad Partner Center. Microsoft Store no ha emitido firma/certificación.

## Paso del propietario — cuenta e identidad

1. Visitar https://partner.microsoft.com/dashboard e iniciar sesión con la cuenta de desarrollador.
2. Si no se tiene cuenta habilitada, completar el registro y verificaciones que solicite Microsoft. **No compartir contraseña ni códigos de acceso con nadie**.
3. Apps & Games → New product → MSIX or PWA app → comprobar disponibilidad de LaptopBridge → reservar el nombre.
4. Product management / Product identity: obtener exactamente los campos `Package/Identity/Name`, `Package/Identity/Publisher`, `PublisherDisplayName`.
5. En GitHub https://github.com/tattoosarah23-tech/LaptopBridge/actions/workflows/windows-build.yml → Run workflow → `store_submission=true`, pegar esos tres campos. No configurar secretos: son valores de identidad públicos, no credenciales.
6. Comprobar resultados de build. Descargar candidato STORE_SUBMISSION_UNSIGNED, subirlo a Partner Center solo si las comprobaciones no fallan.

## Checklist de ficha Store

- Nombre único reservado.
- Descripción e información sobre tratamiento de datos veraces.
- Categoría, precio, disponibilidad y clasificación por edades.
- Política de privacidad confirmada por el titular; hay borrador en `PRIVACY.md`.
- Mínimo una captura REAL de la aplicación instalada, no un mockup. Microsoft recomienda varias.
- Logotipo de Store y datos de soporte.
- Notas para certificación que expliquen `runFullTrust`, el servidor MCP stdio y que no se exponen puertos públicos.
- Validar panel, estado persistente y alias MCP **dentro del contexto MSIX**.
- Pruebas Windows App Certification Kit (WACK) y respuesta a cualquier incidencia de Microsoft.

## Prueba definitiva en Windows 11 (solo después de certificación y publicación)

1. Smart App Control activado. Instalar exclusivamente desde Microsoft Store.
2. Ejecutar panel; comprobar cero carpetas autorizadas y ausencia de peticiones de administrador.
3. Crear directorio vacío `C:\LaptopBridge-Prueba` y autorizarlo desde panel.
4. Con cliente MCP compatible: comprobar listado; intentar ruta fuera y verificar denegación; crear, leer, escribir y restaurar archivo de prueba.
5. Planificar eliminación de archivo de prueba y probar Cancelar → no elimina; probar ELIMINAR → traslada a Papelera y conserva copia recuperable.
6. Revocar carpeta; comprobar que operaciones posteriores devuelven acceso denegado.
7. Probar persistencia tras reiniciar panel y Windows, actualizaciones y desinstalación.
8. **La conexión con ChatGPT no está verificada** y requiere una solución MCP compatible autorizada en el plan de la cuenta.

## Fuentes

- https://learn.microsoft.com/en-us/windows/apps/publish/publish-your-app/msix/create-app-submission
- https://learn.microsoft.com/en-us/windows/apps/publish/publish-your-app/msix/support-info
- https://learn.microsoft.com/en-us/windows/uwp/debug-test-perf/windows-app-certification-kit
- https://learn.microsoft.com/en-us/windows/msix/package/packaging-uwp-apps
