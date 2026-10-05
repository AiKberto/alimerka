# it-ia · Código del departamento IT - IA

Este repositorio **replica el árbol de carpetas de Google Drive `IT - IA` tal cual**, pero solo con el código y la configuración. Los documentos (PDF, Docs, Sheets, Slides) siguen solo en Drive.

🔗 Carpeta de Drive: `REEMPLAZAR_URL_DRIVE`
🔗 Listado de proyectos: `REEMPLAZAR_URL_LISTADO`

## ¿Dónde edito mi código?

Mira el modo de tu proyecto en [`sync/proyectos.yml`](sync/proyectos.yml):

| Modo | Dónde se edita | Qué pasa después |
|---|---|---|
| **A – Git manda** | Aquí, en Git (rama → PR → revisión → merge) | Al hacer merge en `main`, el código se copia solo a Drive en la misma ruta |
| **B – Drive manda** | En Drive, como siempre | Cada hora se copia solo a Git, con tu nombre como autor |

⚠️ No edites un proyecto en el sitio que no le toca: la sincronización sobrescribiría tu cambio. El CI rechaza los PR que tocan proyectos en Modo B.

## Primeros pasos (Modo A)

```bash
git clone https://REEMPLAZAR_GHES/alimerka/it-ia.git
cd it-ia
git config core.hooksPath .githooks   # activa el bloqueo de secretos
git config core.longpaths true        # rutas largas en Windows
```

Solo te interesa tu proyecto? Clónalo parcialmente:

```bash
git clone --filter=blob:none --sparse https://REEMPLAZAR_GHES/alimerka/it-ia.git
cd it-ia && git sparse-checkout set "0111_Proyectos/01_IA_AlimerkAI"
```

Chuleta de Git y uso con Claude Code: `docs/chuleta_git_y_claude.md` (en el repo `drive-git-sync`).

## Reglas

1. Nada de contraseñas, tokens ni claves en el código: usa `.env` (ignorado) y `config/*.example.yml` como plantilla.
2. `main` está protegida: todo cambio entra por PR y lo aprueba un responsable del proyecto (`.github/CODEOWNERS`).
3. No crees carpetas fuera de tu proyecto: la estructura es la de Drive.
