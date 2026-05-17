# 📊 Monitor de Liquidez Global

Dashboard automático que se actualiza solo todos los días.

## 📁 Estructura

```
liquidez-monitor/
├── index.html          ← Tu dashboard (abrir en navegador)
├── .github/
│   └── workflows/
│       └── update-data.yml  ← Robot que descarga datos
└── data/               ← Se crea solo, acá van los JSON
```

## 🚀 Pasos para activarlo

### 1. Crear cuenta en GitHub
- Andá a https://github.com
- Creá una cuenta (gratis)

### 2. Crear un repositorio nuevo
- Apretá el botón verde **"New"** (o **"+"** → **"New repository"**)
- **Repository name**: `liquidez-monitor`
- Marcá **"Public"** (público)
- Apretá **"Create repository"**

### 3. Subir estos archivos
- Dentro del repo, apretá **"Add file" → "Upload files"**
- Subí **todos los archivos** de esta carpeta (arrastrá todo)
- Apretá **"Commit changes"**

### 4. Pedir API Key de FRED (gratis)
- Andá a https://fred.stlouisfed.org/docs/api/api_key.html
- Creá cuenta → "Request API Key"
- Copiá la key (32 caracteres)

### 5. Guardar la key en secreto
- En tu repo, andá a **"Settings"** (pestaña de arriba)
- Menú izquierdo: **"Secrets and variables" → "Actions"**
- Apretá **"New repository secret"**
- **Name**: `FRED_API_KEY`
- **Secret**: pegá tu key de 32 caracteres
- Apretá **"Add secret"**

### 6. Activar la página web
- En tu repo, andá a **"Settings"**
- Menú izquierdo: **"Pages"**
- **Source**: elegí **"Deploy from a branch"**
- **Branch**: `main` / **folder**: `/ (root)`
- Apretá **"Save"**

### 7. Correr el robot una primera vez
- Andá a la pestaña **"Actions"** de tu repo
- Apretá **"Actualizar datos FRED"** en la lista de la izquierda
- Apretá el botón gris **"Run workflow"** → **"Run workflow"**
- Esperá 1-2 minutos a que termine (se pone verde ✅)

### 8. Listo
- Tu dashboard va a estar en:
  `https://TU-USUARIO.github.io/liquidez-monitor/`
- Reemplazá `TU-USUARIO` con tu nombre de GitHub
- Se actualiza **solo todos los días a las 10:00 AM** (hora Argentina)

## 🔧 Si querés actualizar manualmente

Andá a **Actions** → **"Actualizar datos FRED"** → **"Run workflow"**

## ❓ ¿Qué hace el robot?

Todos los días descarga automáticamente:
- Balance de la Fed (WALCL)
- Reverse Repo (RRPONTSYD)
- TGA / Cuenta del Tesoro (WTREGEN)
- M2 (M2SL)
- Tasa 10 años (DGS10)
- Dólar DXY (DTWEXBGS)
- Spreads de crédito HY (BAMLH0A0HYM2)

Y los guarda en la carpeta `data/` para que tu dashboard los lea sin problemas.
