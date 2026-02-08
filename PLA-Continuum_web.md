# PLA-Continuum_web - Port C# → Python/FastAPI

**Objectiu:** Portar el toolkit eòlic Continuum de C# Windows Forms a web Python/FastAPI

**Font:** git/Continuum (C# original)
**Destí:** Continuum_web (Python/FastAPI)

---

## 📦 Features a Portar (per ordre)

| Ordre | Mòdul | Arxiu C# | Complexitat | Prioritat |
|-------|-------|----------|-------------|-----------|
| 1 | **Core: Estructures de dades** | `Met.cs`, `Turbine.cs` | ⭐⭐ | Alta |
| 2 | **Met Data Filtering** | `Met_Data_Filter.cs` | ⭐⭐⭐ | Alta |
| 3 | **MCP (Measure-Correlate-Predict)** | `MCP.cs` | ⭐⭐⭐⭐ | Alta |
| 4 | **Wake Loss Modeling** | `WakeCollection.cs`, `Wake_Model.cs` | ⭐⭐⭐⭐⭐ | Mitjana |
| 5 | **Topografia** | `TopoInfo.cs` | ⭐⭐⭐ | Baixa |
| 6 | **Reanalysis Data** | `MERRA.cs`, `Reanalysis_Download.cs` | ⭐⭐⭐ | Baixa |

---

## 🔧 Stack Tecnològic

| Capa | Eina | Raó |
|------|------|-----|
| **API** | FastAPI | Modern, asíncron, swagger auto |
| **Càlcul numèric** | NumPy, SciPy | Reemplaça MathNet.Numerics |
| **DataFrames** | pandas | Dades tabulades |
| **GIS/Topografia** | GDAL (via rasterio/xarray) | Reemplaça OSGeo.GDAL |
| **Serialització** | Pydantic | Validació, JSON |
| **Logging** | structlog o loguru | Reemplaça NLog |
| **Frontend** | React + Vite | Modern, component-based |

---

## 📁 Estructura del Projecte

```
continuum_web/
├── src/
│   ├── api/
│   │   ├── __init__.py
│   │   ├── main.py              # FastAPI app
│   │   ├── routers/
│   │   │   ├── met_filter.py
│   │   │   ├── mcp.py
│   │   │   ├── wake.py
│   │   │   └── topo.py
│   │   └── schemas/             # Pydantic models
│   ├── core/
│   │   ├── __init__.py
│   │   ├── met.py               # Met class ported
│   │   ├── turbine.py           # Turbine class ported
│   │   └── utils.py
│   ├── calculations/
│   │   ├── __init__.py
│   │   ├── met_filter.py        # Met_Data_Filter ported
│   │   ├── mcp.py               # MCP ported
│   │   ├── wake.py              # WakeCollection ported
│   │   └── topo.py              # TopoInfo ported
│   └── data/
│       ├── __init__.py
│       ├── loaders.py           # CSV, NetCDF loaders
│       └── writers.py
├── tests/
│   ├── test_met_filter.py
│   ├── test_mcp.py
│   └── test_wake.py
├── docs/
│   ├── deployment.md           # HOWTO Deploy
│   ├── usage.md                # HOWTO Ús
│   └── api.md                  # API Reference
├── scripts/
│   └── setup_dev.sh            # Entorn de desenvolupament
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
└── README.md
```

---

## 🔄 Mapping C# → Python

### Tipus de dades

| C# | Python | Notes |
|----|--------|-------|
| `double` | `float` | |
| `int` | `int` | |
| `List<T>` | `List[T]` | |
| `Dictionary<K,V>` | `Dict[K,V]` | |
| `DataFrame` | `pandas.DataFrame` | |
| `Vector3` | `np.ndarray` o dataclass | |
| `DateTime` | `datetime.datetime` | |
| `TimeSpan` | `datetime.timedelta` | |

### Paquets NuGet → Python

| C# NuGet | Python | Ús |
|----------|--------|-----|
| `MathNet.Numerics` | `numpy`, `scipy` | Àlgebra lineal, estadístiques |
| `pandas` | Taules de dades |
| `NLog` | `structlog` | Logging |
| `OSGeo.GDAL` | `rasterio`, `xarray`, `gdal` | GIS/Topografia |

---

## 📋 Fases d'Execució

### Fase 1: Setup i Estructura
- [ ] Crear estructura de directoris
- [ ] Crear requirements.txt
- [ ] Crear Dockerfile
- [ ] Crear FastAPI skeleton
- [ ] Configurar logging

### Fase 2: Core (Estructures de Dades)
- [ ] Portar `Met.cs` → `src/core/met.py`
- [ ] Portar `Turbine.cs` → `src/core/turbine.py`
- [ ] Crear tests per estructures bàsiques

### Fase 3: Met Data Filtering
- [ ] Portar `Met_Data_Filter.cs` → `src/calculations/met_filter.py`
- [ ] Implementar: tower shadow, ice detection, std filtering
- [ ] Implementar: shear extrapolation (power law)
- [ ] Crear tests

### Fase 4: MCP
- [ ] Portar `MCP.cs` → `src/calculations/mcp.py`
- [ ] Implementar: Orthogonal Regression
- [ ] Implementar: Method of Bins
- [ ] Implementar: Matrix-LastWS
- [ ] Crear tests

### Fase 5: Wake Loss
- [ ] Portar `WakeCollection.cs` → `src/calculations/wake.py`
- [ ] Portar `Wake_Model.cs` → `src/calculations/wake_model.py`
- [ ] Implementar: mapes wake 2D/3D
- [ ] Implementar: càlculs sector-wise
- [ ] Crear tests

### Fase 6: API Endpoints
- [ ] Crear router `/met-filter` (POST)
- [ ] Crear router `/mcp` (POST)
- [ ] Crear router `/wake` (POST)
- [ ] Documentació OpenAPI automàtica

### Fase 7: Documentació
- [ ] Crear `docs/deployment.md` (HOWTO Deploy)
- [ ] Crear `docs/usage.md` (HOWTO Ús)
- [ ] Crear `docs/api.md` (API Reference)

### Fase 8: Frontend (Opcional)
- [ ] Crear React app bàsica
- [ ] Connectar amb API
- [ ] UI per cada funcionalitat

---

## 🐳 Docker Setup

### Dockerfile
```dockerfile
FROM python:3.11-slim

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY src/ ./src/
COPY docs/ ./docs/

EXPOSE 8000
CMD ["uvicorn", "src.api.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

### docker-compose.yml
```yaml
version: '3.8'
services:
  continuum-api:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - ./data:/app/data
    environment:
      - LOG_LEVEL=INFO
```

---

## 📖 Documentació Requerida

### docs/deployment.md (HOWTO Deploy)

```
# HOWTO: Desplegar Continuum Web

## Requisits
- Docker + Docker Compose
- Servidor amb Linux (recomanat)
- 4GB RAM mínim

## Pas 1: Instal·lar Docker
```bash
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER
```

## Pas 2: Clonar repositori
```bash
git clone https://github.com/oriolIA/Continuum_web.git
cd Continuum_web
```

## Pas 3: Configurar
```bash
cp .env.example .env
# Editar .env amb les teves configuracions
```

## Pas 4: Desplegar
```bash
docker-compose up -d
```

## Pas 5: Verificar
```bash
curl http://localhost:8000/health
```

## Logs
```bash
docker-compose logs -f continuum-api
```

## Actualitzar
```bash
docker-compose pull
docker-compose up -d
```
```

### docs/usage.md (HOWTO Ús)

```
# HOWTO: Ús de Continuum Web

## Accés
- API: http://localhost:8000
- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

## Exemple: MCP Analysis

```bash
curl -X POST "http://localhost:8000/mcp" \
  -H "Content-Type: application/json" \
  -d '{
    "reference_data": "data/reference.csv",
    "target_data": "data/target.csv",
    "method": "orthogonal_regression",
    "sectors": 12
  }'
```

## Més informació
Vegeu docs/api.md
```

---

## ⚠️ Complicacions Esperades

| Problema | Solució |
|----------|---------|
| GDAL complex | Usar `rasterio` + `xarray` més simple |
| C# → Python types | Pydantic dataclasses |
| Rendiment càlculs | NumPy vectorització |
| Dependències GIS | Contenidor Docker amb GDAL pre-instal·lat |

---

## 📚 Referències

- **FastAPI:** https://fastapi.tiangolo.com/
- **Pydantic:** https://docs.pydantic.dev/
- **Rasterio:** https://rasterio.readthedocs.io/
- **Pandas:** https://pandas.pydata.org/

---

**Inici:** 2026-02-08
**Estat:** PLA creat
