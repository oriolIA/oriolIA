# Sessions.md

## Tasques completades (2026-02-08)

### ✅ Continuum_web - COMPLET v2.0
**Repo:** https://github.com/oriolIA/Continuum_web

| Mòdul | Estat | Arxius |
|-------|-------|--------|
| **Core** | ✅ | met.py, turbine.py |
| **Met Filter** | ✅ | met_filter.py |
| **MCP Clàssic** | ✅ | mcp.py |
| **Neural MCP** | ✅ | neural_mcp.py |
| **Wake Modeling** | ✅ | wake.py |
| **Layout Design** | ✅ | layout.py |
| **API** | ✅ | 5 routers |
| **Frontend Web** | ✅ | index.html, styles.css, app.js |
| **Docker** | ✅ | Dockerfile, docker-compose.yml |
| **Docs** | ✅ | deployment.md, usage.md |

---

### ✅ SRDownscalling - CONFIGURAT
**Repo:** https://github.com/oriolIA/SRDownscalling

| Component | Estat | Notes |
|-----------|-------|-------|
| Dataset | ✅ | d02 → d05 (100×100 → 125×119) |
| ESRGAN | ✅ | 680K params |
| UNetSR | ✅ | 2.5M params |
| Entrenament | ⏳ | Necessita GPU |

---

### ✅ UNET4DownscalingWRF-v2 - IMPLEMENTAT
**Repo:** https://github.com/oriolIA/UNET4DownscalingWRF-v2

| Component | Estat | Notes |
|-----------|-------|-------|
| ResUNet | ✅ | Residual + Attention gates |
| Training | ⏳ | Necessita GPU |
| Mètriques | ✅ | MSE, MAE, PSNR, SSIM |

---

## TASQUES PENDENTS

### 🔥 Prioritat Alta (avançar)

#### Continuum_web
- [ ] Tests unitaris (pytest)
- [ ] Integració GIS/GDAL
- [ ] MCP Neural API endpoint
- [ ] Deploy a producció

#### SRDownscaling
- [ ] Implementar atenció (CBAM/Self-Attention)
- [ ] Entrenar model (necessita GPU)
- [ ] Afegir mètrica SSIM

#### UNET4Downscaling
- [ ] Entrenar ResUNet (necessita GPU)
- [ ] Comparar amb v1
- [ ] Hyperparameter tuning

### 🔧 Prioritat Mitjana

- [ ] Documentació completa (README.md)
- [ ] Requirements.txt actualitzats
- [ ] CI/CD pipeline

---

## MILLORES PROPOSADES

### 1. Continuum_web
| Millora | Descripció |
|---------|-----------|
| GIS/GDAL | Suport per geotiffs, DEMs |
| API Docs | Swagger millorat |
| Auth | Login/usuaris |
| Export | PDF reports |

### 2. SRDownscaling
| Millora | Descripció |
|---------|-----------|
| Progressive SR | Múltiples etapes 4x→16x |
| attention | CBAM / Self-Attention |
| Ensemble | Combinar ESRGAN + UNet |

### 3. UNET4Downscaling
| Millora | Descripció |
|---------|-----------|
| Mixed Precision | FP16 training |
| Early Stopping | Patiència configurable |
| Model Checkpoint | Guardar millor model |

---

## SEGUIMENT

### Data | Acció
------|------
2026-02-08 | Continuum_web COMPLET v2.0
2026-02-08 | SRDownscalling configurat d02→d05
2026-02-08 | UNET4Downscaling ResUNet implementat
**2026-02-09** | **Continuum Web API DEBUGUEJAT** ✅
2026-02-09 | SRDownscalling actualitzat d02→d05
2026-02-09 | Wave Watcher actiu + dijous reminder

---

## ACTIVITAT 2026-02-09 (TARDE)

### Continuum Web - Debug Intensiu
**Estat:** ✅ **TOTS ELS ENDPOINTS FUNCIONEN**

| Endpoint | Mètode | Estat |
|----------|--------|-------|
| `/health` | GET | ✅ OK |
| `/projects/list` | GET | ✅ OK |
| `/projects/create` | POST | ✅ OK |
| `/projects/{name}` | GET | ✅ OK |
| `/files/upload` | POST | ✅ OK |
| `/files/list` | GET | ✅ OK |
| `/met-filter/filter` | POST | ✅ OK |
| `/wake/calculate` | POST | ✅ OK |
| `/layout/grid` | POST | ✅ OK |
| `/layout/optimize` | POST | ✅ OK |

**Arreglos fets (09/02 Tarde):**
- ✅ Arreglat `TurbineWake.wake_radius_at_downwind()` (error @property)
- ✅ Met-filter suporta dades column-based i sense temperature
- ✅ Pujat a GitHub: commit `602c7cc`

**Projecte de prova:** "Demo Project" amb:
- Fitxer met: `test_met.csv`
- 3 registres de dades

---

### 🌊 Wave Watcher - Actiu
**Estat:** Monitoritzant ✅

| Component | Estat |
|-----------|-------|
| Cron job | ✅ Actiu (cada 6h) |
| Open-Meteo API | ✅ Funcionant |
| Recordatori dijous 18:00 | ✅ Configurat |
| Alertes Telegram | ✅ Enviades |

**Darrer alert:** Divendres 13 Feb - Hs 1.5m, Tp 7.3s 🌊

### ☁️ CloudSelf
**Estat:** Pla de negoci creat
**Repo:** https://github.com/oriolIA/oriolIA (PLA-CloudSelf.md)

### 🌊 Wave Watcher (bonus)
**Estat:** Funcional + cron
**Funcionalitat:** Alertes Telegram quan Hs≥1m i Tp≥7s

---

## PER FER AVUI

1. Triar projecte per avançar
2. Executar entrenaments (quan hi hagi GPU)
3. Afegir tests
4. Millorar documentació
