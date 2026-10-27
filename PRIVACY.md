# Política de privacidad propuesta de LaptopBridge

**Borrador técnico — requiere revisión y aprobación del titular antes de publicar en Microsoft Store.** Última revisión: 27 de octubre de 2026.

## Descripción del funcionamiento

LaptopBridge es una aplicación de escritorio para Windows 11 que permite gestionar archivos y carpetas elegidos expresamente por el usuario. Cuenta con un panel local de autorización y un servidor MCP mediante entrada/salida estándar (stdio).

## Datos tratados por la aplicación

LaptopBridge puede procesar rutas, nombres, metadatos y contenido de archivos ubicados dentro de carpetas autorizadas. Conserva localmente configuraciones de permisos, registros técnicos de operaciones y copias de seguridad para recuperación. El software no incluye en su código base publicidad, analítica externa ni envío directo de archivos a un servidor operado por el desarrollador.

## Conexiones a herramientas de IA

Si el usuario conecta LaptopBridge a un cliente MCP, ese cliente puede solicitar y recibir nombres y contenido de archivos autorizados. Si ese cliente envía información a un servicio remoto de IA, **la información puede salir del equipo y quedar sometida a la política de datos del proveedor de ese cliente**. LaptopBridge por sí mismo no controla cómo el cliente utiliza o almacena la información una vez entregada.

## Control del usuario

El usuario puede autorizar y revocar carpetas desde el panel local, y puede pausar operaciones. La eliminación solicita una confirmación visible y crea una copia previa cuando la operación se realiza correctamente. Los registros, la configuración y los respaldos se guardan en el perfil local de Windows y pueden permanecer tras desinstalar, según el comportamiento del empaquetado y del sistema. El titular debe ofrecer instrucciones verificadas de eliminación completa antes de la publicación.

## Seguridad y limitaciones

El sistema restringe operaciones mediante validación de rutas dentro del propio programa. **No constituye un sandbox de seguridad del sistema operativo**. No se recomienda autorizar carpetas con datos sensibles o contenido que otros procesos no confiables puedan modificar hasta completar una auditoría de seguridad específica para Windows.

## Responsable y contacto

**Pendiente de completar por el propietario/publicador:** nombre del responsable y dirección de contacto para consultas sobre privacidad. Este borrador no debe presentarse como política final antes de completar esos datos y revisar las obligaciones legales aplicables.
