# MU Data – Salaries Dashboard

Panel analítico (ES/EN) sobre la reestructuración de la masa salarial del Manchester United desde 2024 (era INEOS).

## Contenido
- `mun-salary.html`: Dashboard principal
- `method.html`: Metodología y glosario bilingüe
- `players.json`: Dataset de operaciones (entradas / salidas y salarios)
- Carpeta `i18n/`: JSONs de internacionalización por dominio
- `favicon.svg`

## Características
- Bilingüe (ES/EN) con persistencia en `localStorage`
- Secciones: Balance, Finanzas (impacto anualizado), Evolución histórica, Big Six, Posiciones, Estructura salarial, Operaciones, Análisis narrativo dinámico, Observaciones, Glosario, Metodología
- Gráficos Chart.js con recolor dinámico e interpolación narrativa
- Cálculo de ahorro neto semanal, anualizado y comparación % sobre ingresos & EBITDA guía FY2025

## Deploy en GitHub Pages
1. Subir repo a GitHub (ya: https://github.com/DisruptivoLab/MU-Data)
2. Settings → Pages → Source: `Deploy from a branch`
3. Selecciona rama `main` y carpeta `/ (root)` → Guardar
4. Esperar build (~1 min). URL típica: `https://disruptivolab.github.io/MU-Data/`
5. Acceso directo: `https://disruptivolab.github.io/MU-Data/mun-salary.html`

## Deploy en Vercel
1. En Vercel: `Add New Project`
2. Importa el repositorio `DisruptivoLab/MU-Data`
3. Framework preset: `Other` (es estático)
4. Build Command: (vacío) – Output Directory: `.`
5. Deploy → Vercel servirá `index.html` y redirigirá a `mun-salary.html`

(Alternativa) Configurar `vercel.json` para headers y cache.

## vercel.json sugerido
Crear un archivo `vercel.json` en root:
```json
{
  "cleanUrls": true,
  "headers": [
    {"source": "/(.*)\.(json)", "headers": [{"key":"Cache-Control","value":"public, max-age=60"}]},
    {"source": "/(.*)\.(js|css|svg)", "headers": [{"key":"Cache-Control","value":"public, max-age=31536000, immutable"}]}
  ]
}
```

## Desarrollo local rápido
Abrir con Live Server, o:
```bash
python -m http.server 8000
# luego visitar http://localhost:8000/mun-salary.html
```

## Futuras mejoras
- Tooltips unificados por dominio
- Mejora ranking narrativo evolución
- Colores adaptativos extra en finanzas (rango guía visual)
- Tests de accesibilidad (contraste y focus states)

## Licencia
Uso analítico / educativo. Datos salariales basados en estimaciones públicas (Capology + ajustes manuales).
