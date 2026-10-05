# Cambio de prueba realizado a las 13:32
# Instrucciones para Claude en este repositorio

## Qué es este repo
Réplica del árbol de Google Drive del departamento **IT - IA**, solo con código y configuración. Las rutas y nombres de carpetas son **exactamente los de Drive** (con espacios, tildes y numeraciones como `0111_Proyectos`). Los documentos (PDF, Docs, Sheets) no están aquí.

## Antes de cambiar nada
1. Averigua en qué proyecto vas a trabajar y mira su modo en `sync/proyectos.yml`.
2. **Solo puedes modificar proyectos en Modo A.** Si el proyecto está en Modo B, para y avisa al usuario: ese código se edita en Drive y la sincronización sobrescribiría tus cambios (el CI rechazará el PR).
3. Trabaja solo dentro de la carpeta de ese proyecto. No crees, muevas ni renombres carpetas fuera de él: la estructura tiene que seguir siendo la de Drive.

## Flujo de trabajo obligatorio
1. `git switch main && git pull`
2. Crea una rama: `git switch -c claude/<proyecto>-<tema-corto>` (p. ej. `claude/alimerkai-login-sso`).
3. Haz cambios pequeños y commits con mensajes en español que expliquen el porqué.
4. `git push -u origin <rama>` y abre un PR con `gh pr create --fill` (rellena la plantilla del PR).
5. **Nunca** hagas push a `main`, `--force` ni `--no-verify`. Un responsable del proyecto revisa y hace el merge.

## Seguridad
- Nunca escribas contraseñas, tokens, claves ni cadenas de conexión en el código. Usa variables de entorno (`.env`, ignorado por Git) y deja una plantilla en `config/*.example.yml` o `.env.example`.
- Si encuentras un secreto ya presente en el código, no lo copies ni lo muevas: avisa al usuario para que lo rote.
- No leas ficheros `.env`, `*.key` ni `*.pem`.
- El hook `pre-commit` ejecuta gitleaks. Si bloquea un commit, corrige la causa; no lo saltes.

## No tocar
`sync/`, `.github/`, `.githooks/`, `.gitleaks.toml` y este `CLAUDE.md` son de los administradores. Si crees que algo debe cambiar ahí, propónselo al usuario.

## Contexto de cada proyecto
Si existe un `CLAUDE.md` dentro de la carpeta del proyecto, léelo: tiene cómo se ejecuta, se prueba y sus convenciones.
