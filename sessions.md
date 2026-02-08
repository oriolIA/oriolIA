# Sessions.md

## Tasques completades avui (2026-02-08)

### ✅ Continuum_web - Port C# → Python/FastAPI
- **Estat:** COMPLET
- **Features implementades:**
  - Core: met.py, turbine.py
  - Calculations: met_filter.py, mcp.py, wake.py
  - API: 3 routers (met-filter, mcp, wake)
  - Docker: Dockerfile + docker-compose.yml
  - Docs: deployment.md, usage.md
- **Repo local:** `/home/oriol/.openclaw/workspace/continuum_web`
- **Pendent:** Git push manual (sense credencials a l'entorn)

### ✅ SRDownscalling - Configuració d02→d05
- **Estat:** CONFIGURAT
- **Canvi:** Usar d02 com LR en lloc de d01 (que falta)
- **Fitxers modificats:**
  - src/data/wrf_sr_dataset.py
  - src/train.py
  - README.md
  - WORKING_STEPS.md
- **Dataset:** d02 (~3km, 100×100) → d05 (~100m, 125×119)
- **Pendent:** Git push

### ✅ UNET4DownscalingWRF-v2 - ResUNet implementat
- **Estat:** IMPLEMENTAT
- **Nou model:** ResUNet amb:
  - Residual connections
  - Attention gates
  - Skip connections millorades
- **Fitxers creats:**
  - src/models/resunet.py
  - src/training/trainer.py
  - train.sh
- **Pendent:** Git push

---

## TASQUES PENDENTS

### Git Push (manual)
- [ ] Continuum_web → GitHub
- [ ] SRDownscalling → GitHub
- [ ] UNET4DownscalingWRF-v2 → GitHub

### Continuum_web
- [ ] Tests unitaris
- [ ] Frontend React
- [ ] Integració GIS/GDAL

### SRDownscaling
- [ ] Entrenar model ESRGAN/UNetSR
- [ ] Implementar atenció (CBAM/Self-Attention)
- [ ] Mètriques SSIM

### UNET4DownscalingWRF-v2
- [ ] Entrenar ResUNet
- [ ] Comparar amb v1
- [ ] Hyperparameter tuning

---

## Actualitzacions
- 2026-02-08 18:00: Tots 3 projectes amb codi llest. Pendents de git push manual.
- 2026-02-08 10:13: Corregit sessions.md amb les tasques reals. Reconegut error de memòria.
- 2026-02-08 10:08: Creació inicial del fitxer (informació buida).
