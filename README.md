# Consultas de Animales Web

Primera versión web del programa `Gui_Consulta7_v2_0.py`.

## Ejecutar localmente

```bash
cd /Users/jlbobba/Documents/Codex/2026-05-10/tengo-un-programa-phyton-que-hace/web_app
python3 app.py
```

Luego abrir:

```text
http://127.0.0.1:8000
```

## Qué incluye

- Consulta de animales.
- Consulta de pesos.
- Consulta de acciones.
- Filtros por IDE, fecha de nacimiento y acción.
- Opción "solo con pesajes".
- Exportación a CSV.
- Alta de acción para un animal.
- Cambio de IDE con registro en `Caravanas`.

## Base de datos

Por ahora usa SQLite con el archivo `animales.db`.

También se puede indicar otra ubicación:

```bash
DB_PATH=/ruta/a/animales.db python3 app.py
```

Para usar Supabase/PostgreSQL:

```bash
python3 -m pip install -r requirements.txt
DATABASE_URL="postgresql://postgres:TU_PASSWORD@HOST:5432/postgres?sslmode=require" \
APP_USERS="consulta:clave-consulta:consulta,admin:clave-editor:editor" \
SESSION_SECRET="una-clave-larga-aleatoria" \
python3 app.py
```

## Usuarios

La app tiene dos roles:

- `consulta`: puede ver consultas y exportar CSV.
- `editor`: puede ver consultas, exportar CSV, agregar acciones y cambiar IDE.

Los usuarios se configuran con la variable `APP_USERS`:

```text
usuario:contraseña:rol,usuario2:contraseña2:rol
```

Ejemplo:

```text
APP_USERS="consulta:clave1:consulta,admin:clave2:editor"
```

En Render también hay que configurar `SESSION_SECRET` con un texto largo y privado.

## Próximo paso: nube

Para usar base de datos en la nube conviene migrar de SQLite a PostgreSQL.
Buenas opciones para empezar:

- Supabase PostgreSQL.
- Neon PostgreSQL.
- Railway PostgreSQL.
- Render PostgreSQL.

El cambio recomendado para producción es:

1. Crear base PostgreSQL en la nube.
2. Migrar tablas y datos desde `animales.db`.
3. Reemplazar `sqlite3` por un conector PostgreSQL.
4. Publicar la app en Render, Railway, Fly.io, Azure o similar.
