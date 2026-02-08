# Continuum_web.md

**Repo:** https://github.com/oriolIA/Continuum_web

**Descripció:** Toolkit eòlic portat de C# a Python/FastAPI

**Estat:** ✅ COMPLET v2.0 (2026-02-08)

---

## Funcionalitats

| Mòdul | Arxiu | Descripció |
|-------|--------|------------|
| **Core** | `src/core/met.py` | Estructures MetData, MetStats |
| **Core** | `src/core/turbine.py` | Estructures Turbine, WindFarm |
| **Met Filter** | `src/calculations/met_filter.py` | QC, ombra torre, gel, shear |
| **MCP Clàssic** | `src/calculations/mcp.py` | Orthogonal, Bins, Matrix |
| **Neural MCP** | `src/calculations/neural_mcp.py` | Xarxa neuronal MLP |
| **Wake** | `src/calculations/wake.py` | Jensen, Larsen, mapes |
| **Layout** | `src/calculations/layout.py` | GA optimització, Grid, Staggered |
| **API** | `src/api/main.py` | FastAPI + 5 routers |

---

## API Endpoints

| Endpoint | Mètode | Descripció |
|----------|--------|------------|
| `/health` | GET | Health check |
| `/met-filter/filter` | POST | Filtrar dades |
| `/met-filter/upload-csv` | POST | Pujar CSV |
| `/mcp/analyze` | POST | MCP clàssic |
| `/mcp/neural/train` | POST | MCP Neural |
| `/wake/calculate` | POST | Calcular pèrdues |
| `/layout/grid` | POST | Crear layout |
| `/layout/optimize` | POST | Optimitzar GA |
| `/layout/metrics` | POST | Mètriques layout |

---

## Frontend Web

| Arxiu | Descripció |
|-------|------------|
| `frontend/index.html` | Interfície SPA |
| `frontend/styles.css` | Disseny modern |
| `frontend/app.js` | Lògica + API calls |

**Per запустити:**
```bash
python3 serve_frontend.py
# Obrir: http://localhost:8080
```

---

## Millores pendents

- [ ] Tests unitaris
- [ ] Integració GIS/GDAL
- [ ] API docs millorats
- [ ] Sistema d'autenticació
- [ ] Export PDF

---

## Docker

```bash
docker-compose up -d
# API: http://localhost:8000/docs
```
