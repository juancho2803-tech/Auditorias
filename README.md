# Auditor OT — Maipú Automotores

Sistema de auditoría de órdenes de trabajo multi-marca con procesamiento por lote e IA.

## Archivos

```
auditor_maipu/
├── index.html        → Auditor (carga OTs, procesa, guarda)
├── dashboard.html    → Métricas y reportes
└── apps_script.gs   → Código para Google Apps Script
```

## Deploy en GitHub Pages

### 1. Crear repositorio

1. Entrá a github.com → New repository
2. Nombre: `auditor-ot` (o el que prefieras)
3. Visibilidad: **Private** (recomendado)
4. Create repository

### 2. Subir archivos

```bash
git init
git add index.html dashboard.html
git commit -m "Auditor OT v1.0"
git remote add origin https://github.com/TU_USUARIO/auditor-ot.git
git push -u origin main
```

O simplemente arrastrá los archivos desde la interfaz web de GitHub.

### 3. Activar GitHub Pages

1. Settings → Pages
2. Source: Deploy from a branch
3. Branch: main → / (root)
4. Save

La URL va a ser: `https://TU_USUARIO.github.io/auditor-ot/`

### 4. Configurar Google Sheets

1. Creá un Google Sheet nuevo
2. Extensiones → Apps Script
3. Borrá todo el código y pegá el contenido de `apps_script.gs`
4. Guardá (Ctrl+S)
5. Implementar → Nueva implementación
   - Tipo: Aplicación web
   - Ejecutar como: Yo
   - Acceso: Cualquier persona
   - Implementar
6. Copiá la URL que aparece

### 5. Configurar el sistema

En `index.html` y `dashboard.html`, completá:
- **Anthropic API Key**: obtenela en console.anthropic.com
- **Google Apps Script URL**: la URL del paso 4
- **Auditor**: tu nombre

## Uso

### Auditar un lote

1. Abrí `index.html`
2. Seleccioná la marca (VW / Audi / Ford / Chevrolet)
3. Arrastrá todos los PDFs del mes
4. Hacé clic en **Procesar lote**
5. El sistema procesa de a uno automáticamente (2 segundos entre cada OT)
6. Al terminar, hacé clic en **Guardar todos en Sheets**

### Ver métricas

1. Abrí `dashboard.html`
2. Ingresá la URL del Apps Script
3. Hacé clic en **Cargar datos**
4. Usá los filtros para explorar

## Costos estimados

| Modelo | Costo por OT | 700 OTs/mes |
|--------|-------------|-------------|
| claude-haiku-4-5 | ~$0.005 | ~$3.5 USD |
| claude-sonnet-4-5 | ~$0.02 | ~$14 USD |

## Marcas soportadas

| Marca | Tabla inferior garantía |
|-------|------------------------|
| VW | Obligatoria (A.T., Defecto, Locación, etc.) |
| Audi | Obligatoria (igual a VW) |
| Ford | No aplica |
| Chevrolet | No aplica |

## Asesores → Sucursal

- **Sabattini**: Ferrer, Toledo, Bruno
- **DQ**: todos los demás
