# Continuum_web.md

**Repositori:** git/Continuum_web (local: /home/oriol/.openclaw/workspace/continuum_web)

**Descripció:** Port del toolkit eòlic Continuum de C# a Python/FastAPI

**Font:** https://www.continuumwind.com/ + git/Continuum (fork de oneenergy-software/Continuum)

**Objectiu:** Portar el toolkit eòlic Continuum a una interfície web/servidor.

**Estat:** ✅ COMPLET (2026-02-08)

---

## Funcionalitats Implementades

| Mòdul | Arxiu | Descripció |
|-------|--------|------------|
| **Core - Met** | `src/core/met.py` | Estructures MetData, MetStats |
| **Core - Turbine** | `src/core/turbine.py` | Estructures Turbine, WindFarm |
| **Met Filter** | `src/calculations/met_filter.py` | Filtratge dades, shear calculation |
| **MCP** | `src/calculations/mcp.py` | Orthogonal Regression, Bins, Matrix |
| **Wake** | `src/calculations/wake.py` | Jensen/Larsen models, wake maps |
| **API** | `src/api/main.py` | FastAPI + 3 routers |

---

## API Endpoints

| Endpoint | Mètode | Descripció |
|----------|--------|------------|
| `/met-filter/filter` | POST | Filtrar dades meteorològiques |
| `/met-filter/upload-csv` | POST | Pujar CSV i filtrar |
| `/mcp/analyze` | POST | Executar MCP |
| `/wake/calculate` | POST | Calcular pèrdues de wake |

---

## Docker

```bash
docker-compose up -d
# Accés: http://localhost:8000/docs
```

---

## Pendent

- [ ] Git push manual a GitHub
- [ ] Tests unitaris
- [ ] Frontend React
- [ ] Integració GDAL

