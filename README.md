# 🧭 Atlas Stack — Repositorio de Proyectos y Prácticas

Bienvenidos al repositorio central del equipo **Atlas Stack**. Aquí vivirá **todo**: prácticas, mini‑proyectos, entregas por sprint y documentación técnica.

> **Objetivo:** trabajar como un equipo profesional de Ing. en Sistemas: código limpio, comunicación clara y aprendizaje continuo.

---

## 📂 Estructura del repo

```
/docs/                # guías, diagramas, especificaciones
/practicas/           # ejercicios individuales por módulo
  └── <modulo>/
      └── <usuario>/  # carpeta personal (ver "Convenciones")
/proyectos/           # proyectos por sprint o módulo
  └── <nombre-proyecto>/
/plantillas/          # templates de código, PR, issues, README
/scripts/             # utilidades de automatización
CHANGELOG.md          # registro de cambios
README.md             # este archivo
```

**Convenciones de nombres**
- Usuario: `nombre-apellido` (minúsculas, guiones) → `diego-lopez`
- Proyecto: `kebab-case` → `api-rest-notas`
- Módulo: `modNN_tema-corto` → `mod01_git-basico`

---

## 👥 Equipo (10)
- Líder/Jefe de equipo: **Diego López**
- Miembros: _completar_
  - [ ] Nombre 1 — rol
  - [ ] Nombre 2 — rol
  - [ ] Nombre 3 — rol
  - [ ] Nombre 4 — rol
  - [ ] Nombre 5 — rol
  - [ ] Nombre 6 — rol
  - [ ] Nombre 7 — rol
  - [ ] Nombre 8 — rol
  - [ ] Nombre 9 — rol

> Roles sugeridos: Backend, Frontend, DevOps, QA/Testing, Documentación, Investigación.

---

## 🌿 Flujo de trabajo (ramas)

- `main` → estable, **release** / demo.
- `dev`  → integración de sprint.
- `feature/<tema>` → trabajo diario (una tarea/feature por rama).

**Reglas rápidas**
1. Crea tu rama desde `dev` → `git checkout -b feature/<tema>`
2. Commits pequeños con **Conventional Commits** (ver abajo).
3. Abre PR a `dev` (no a `main`), solicita revisión de 1 compañero.
4. Merge squash cuando aprueben. Releases: `dev` → `main` por tag.

---

## ✍️ Estilo de commits (Conventional Commits)

Formato: `tipo(scope): resumen`  
Tipos comunes: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`

Ejemplos:
- `feat(auth): login con JWT y refresh token`
- `fix(api): corrige 500 al crear tareas vacías`
- `docs(readme): agrega guía de instalación`

---

## 🔀 Pull Requests

**Checklist**
- [ ] La rama parte de `dev`
- [ ] Descripción clara (qué y por qué)
- [ ] Pruebas/ejemplos incluidos (si aplica)
- [ ] Documentación actualizada
- [ ] Sin *console.log*/*print* de debugging

**Plantilla sugerida**
```
## Resumen
Breve descripción del cambio.

## Evidencia
Capturas / curl / GIF / enlaces.

## Cómo probar
Pasos para reproducir.

## Checklist
- [ ] Pruebas
- [ ] Docs
- [ ] Sin cambios rompientes
```

---

## 📌 Issues (gestión de trabajo)

Tipos: `bug`, `feature`, `doc`, `chore`, `question`  
Etiqueta adicional: `prioridad: alta|media|baja`

**Plantilla sugerida**
```
**Descripción**
Qué sucede / Qué se necesita.

**Criterios de aceptación**
- [ ] ...
- [ ] ...

**Notas**
Links, decisiones, contexto.
```

---

## 💻 Configuración de entorno

1) **Clonar**  
```bash
git clone <URL_DEL_REPO>
cd <carpeta>
git switch -c dev || git checkout dev
```

2) **Node/Python** (según proyecto)
- Node LTS: `nvm use --lts`
- Python 3.11+: `python -m venv .venv && source .venv/bin/activate`

3) **Variables de entorno**  
Crea `.env` a partir de `.env.example` (si existe).

4) **Dependencias**  
```bash
# Node
npm i
# Python
pip install -r requirements.txt
```

---

## ✅ Entrega de prácticas

Cada práctica va en `/practicas/<modulo>/<usuario>/` con su propio `README.md` que incluya:
- Descripción breve
- Comandos para correr
- Capturas o GIF (si aplica)
- Notas o aprendizajes

Ejemplo:
```
/practicas/mod01_git-basico/diego-lopez/
  ├── README.md
  ├── src/
  └── assets/
```

---

## 🧪 Calidad

- Pruebas unitarias cuando aplique (`jest`, `pytest`, etc.).
- Linters y formateo (`eslint`, `prettier`, `black`, `flake8`).
- CI (opcional): GitHub Actions para test/lint en PRs.

---

## 🔒 Seguridad

- No subir credenciales ni claves; usar `.env` y variables de entorno.
- Revisar dependencias vulnerables (`npm audit`, `pip-audit`).

---

## 📘 Documentación

- Documenta lo mínimo necesario para **reproducir**.
- Diagrama simple (plantillas en `/plantillas/`).
- Cambios destacables → `CHANGELOG.md` (por versión/sprint).

---

## 🗓️ Calendario y cadencia

- **Lunes:** anuncio de objetivos.
- **Miércoles:** checkpoint breve.
- **Viernes:** demo/avance y registro en `CHANGELOG.md`.

---

## 🤝 Código de conducta

Respeto, inclusión y apoyo mutuo. La retro se da **con respeto** y con foco en el **producto** y el **aprendizaje**.

---

## 📄 Licencia

Este repositorio se publica inicialmente bajo licencia **MIT** (ajustar si el profe/curso requiere otra).

---

## 📅 Historial

- 2025-09-18 — creación del README inicial.
