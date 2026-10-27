# Seguridad de LaptopBridge

**Estado:** código y compilación Windows validados funcionalmente; no certificado, firmado, auditado de manera independiente ni probado con Smart App Control en el equipo final.

## Normas de uso

- Mantener Microsoft Defender, Smart App Control y SmartScreen activados.
- No instalar paquetes MSIX o EXE sin firma desde artefactos de CI.
- No conceder acceso a carpetas del sistema, a claves/credenciales o a directorios cuyos contenidos puedan cambiar procesos no confiables.
- Probar primero en un directorio de muestra vacío.
- El consentimiento para eliminación debe ser presencial en una ventana local; el MCP nunca debe permitir conceder permisos.
- No considerar las restricciones implementadas en Python equivalentes a control de acceso del núcleo de Windows.

## Limitaciones de ingeniería por resolver

- Potenciales carreras TOCTOU al resolver rutas y abrir archivos bajo cambios concurrentes.
- Compatibilidad de estado y alias de ejecución en entorno MSIX.
- Certificación y ensayos dinámicos de la instalación Store.
- Verificación de que el cliente MCP concreto no exfiltra archivos fuera de lo esperado.

## Reportar vulnerabilidades

No publicar rutas de usuario, tokens, logs con datos privados ni contenido de archivos en incidencias públicas. Configurar un canal de divulgación privada en el repositorio antes de distribuir públicamente.
