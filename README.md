# Fichaje Almacén — Volta Baterías

Web de fichaje (registro de jornada) para la tablet del almacén.

- `index.html`: la web completa (sin dependencias, salvo las fuentes de Google).
- `netlify.toml`: cabeceras para Netlify (permiso de cámara, sin caché).

## Cómo funciona

1. El trabajador toca su nombre, se hace una foto y pulsa **Entrada** o **Salida**.
2. La web envía el fichaje (empleado, tipo, hora, foto) a un webhook de Make.
3. Make lo guarda en la base de Airtable **Fichaje Almacén** (tabla *Fichajes*) con la foto adjunta.
4. Si la tablet se queda sin conexión, el fichaje se guarda en el dispositivo y se envía solo al volver la red.

## Configuración

Todo está al principio de `index.html`, en el bloque `CONFIG`:

- `WEBHOOK_URL`: webhook de Make.
- `DISPOSITIVO`: nombre de la tablet.
- `EMPLEADOS`: lista de personas. `id` es el ID del registro en la tabla *Empleados* de Airtable; `pin` es opcional (4 dígitos).
- `INACTIVIDAD` / `CONFIRMACION`: segundos para volver al inicio y duración de la pantalla de confirmación.

## Despliegue

Netlify: conectar este repositorio, sin comando de build, directorio de publicación `.` (ya indicado en `netlify.toml`). Cada `git push` a `main` redespliega.

## Tablet

Abrir la URL de Netlify en Chrome y permitir la cámara. Para dejarla en modo kiosco, instalar Fully Kiosk Browser, poner la URL como página de inicio, dar permiso permanente de cámara y activar el modo kiosco con contraseña.
