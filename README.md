# Obsidian Vault + GitHub

Repositorio para versionar y respaldar mi Vault de Obsidian utilizando Git y GitHub.

## Objetivo

Este proyecto busca:

- Mantener historial de cambios de mis notas.
- Practicar Git en un caso de uso real.
- Centralizar documentación académica, profesional y personal.
- Tener una base de conocimiento portátil y reproducible.
- Preparar una estructura escalable para futuros proyectos.
    

---

# Estructura del Vault

```plaintext
Jonathan-Obsidian/
├── .obsidian/
├── Personal/
├── Profesional/
├── Universidad/
├── .gitignore
└── README.md
```

## Organización

- **Personal/** → proyectos personales, ideas y documentación propia.
- **Profesional/** → documentación relacionada con trabajo y procesos.
- **Universidad/** → teoría, apuntes, ejercicios y aprendizaje.
- **.obsidian/** → configuración del entorno y plugins.

---

# Decisión de arquitectura

Se decidió mantener:

- **1 Vault → 1 repositorio GitHub**

Separando el conocimiento del código.

Ejemplo recomendado:

```plaintext
GitHub
│
├── Obsidian-Notes ← documentación y conocimiento
│
├── proyecto-codigo-1
├── proyecto-codigo-2
└── laboratorio-universidad
```

Regla aplicada:

- Si se **ejecuta o compila → repositorio propio**
- Si se **documenta o estudia → Vault**

---

# Requisitos

Instalar previamente:

- Git
- Obsidian
- Plugin Obsidian Git (opcional)

Verificar instalación:

```bash
git --version
```

---

# Configuración inicial del repositorio

## 1. Abrir terminal en el Vault

Ubicarse en la carpeta raíz del Vault.

Ejemplo:

```plaintext
C:\Users\usuario\Documentos\Jonathan-Obsidian
```

Verificar contenido:

```bash
ls
```

---

## 2. Inicializar Git

```bash
git init
```

Verificar estado:

```bash
git status
```

Salida esperada:

```plaintext
On branch master
No commits yet
```

---

## 3. Conectar el repositorio remoto

Agregar repositorio remoto:

```bash
git remote add origin URL_DEL_REPOSITORIO
```

Verificar:

```bash
git remote -v
```

Salida esperada:

```plaintext
origin (fetch)
origin (push)
```

---

## 4. Cambiar rama principal a main

```bash
git branch -M main
```

---

## 5. Descargar contenido remoto (cuando el repo ya tiene README)

Si el repositorio ya fue creado con README:

```bash
git pull origin main --allow-unrelated-histories
```

Esto permite:

- Descargar archivos remotos.
- Unir historiales locales y remotos.

---

# Configuración de Git para Windows

Evitar advertencias de saltos de línea:

```bash
git config --global core.autocrlf true
```

Esto permite:

- Guardar internamente en formato compatible.
- Trabajar localmente con formato Windows.

---

# Configuración del .gitignore

Crear archivo:

```plaintext
.gitignore
```

Contenido:

```gitignore
.obsidian/cache/
.obsidian/workspace.json
.obsidian/workspace-mobile.json

.trash/

.DS_Store
Thumbs.db
```

Archivos ignorados:

- caché temporal
- estado de ventanas
- archivos del sistema

Archivos que sí se sincronizan:

```plaintext
.obsidian/
*.md
estructura del vault
plugins
```

---

# Primer commit

Agregar archivos:

```bash
git add .
```

Revisar:

```bash
git status
```

Crear commit:

```bash
git commit -m "feat: initialize obsidian vault"
```

---

# Subir cambios a GitHub

Primer push:

```bash
git push -u origin main
```

Esto:

- sube el Vault
- enlaza la rama local
- permite usar `git push` después sin parámetros

---

# Flujo de trabajo diario

Consultar cambios:

```bash
git status
```

Agregar cambios:

```bash
git add .
```

Guardar cambios:

```bash
git commit -m "docs: actualizar notas"
```

Subir:

```bash
git push
```

Descargar cambios:

```bash
git pull
```

---

# Convención de commits

Ejemplos:

```plaintext
feat: agregar apuntes de Docker
docs: actualizar teoría de paralelismo
refactor: reorganizar estructura del vault
fix: corregir enlaces rotos
```

---

# Consideraciones futuras

- Mantener el Vault separado del código.
- Evaluar repositorio privado para documentación sensible.
- Mantener sincronización limpia con OneDrive.
- Automatizar commits usando Obsidian Git.
- Considerar backups periódicos.
---

# Estado actual

Repositorio inicializado correctamente.

Checklist:

-  Vault creado
-  Git instalado
-  Repositorio conectado
-  Rama principal configurada
-  README integrado
-  .gitignore creado
-  Primer staging realizado
-  Primer commit
-  Primer push
-  Automatización con Obsidian Git