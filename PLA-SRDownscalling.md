# Pla: SRDownscalling

**Repositori:** git/SRDownscalling  
**Objectiu:** Crear un model de Super Resolution per downscaling de camps de vent WRF  
**Tecnologia:** ESRGAN + Attention

---

## FASE 1 COMPLETADA: Anàlisi i Documentació

### 📊 Resum de l'Arquitectura Trobada

#### Models Implementats

**1. ESRGAN** (`src/models/esrgan.py`)
- **Arquitectura:** ESRGAN-like amb RRDB (Residual in Residual Dense Blocks)
- **Capas principals:**
  - `conv_first`: Extracció inicial de features (7→64 canals)
  - `rrdb_trunk`: 12 RRDB blocks en sèrie
  - `RRDB`: 3 ResidualDenseBlocks amb residual scaling (0.2)
  - `ResidualDenseBlock`: 5 capas densament conectades amb growth_channels=32
  - `upscale`: PixelShuffle per upscaling (factor configurable)
  - `conv_last`: Sortida final (64→2 canals per U,V)
- **Paràmetres estimats:** ~680K params
- **Flux de dades:** LR (7×50×51) → Features → RRDBs → Upsample ×N → HR (2×125×119)

**2. UNetSR** (`src/models/unet_sr.py`)
- **Arquitectura:** UNet encoder-decoder amb skip connections
- **Capas principals:**
  - `init_upsample`: Upsample inicial + convolució
  - `encoder`: 3 nivells (DoubleConv) amb MaxPool2d
  - `bottleneck`: DoubleConv(512 canals)
  - `decoder`: 3 nivells amb ConvTranspose2d + skip connections
  - `final`: Conv1×1 per sortirida
- **Paràmetres estimats:** ~2.5M params
- **Avantatge:** Millor preservació d'estructures fines amb skip connections

#### Dataset Pipeline (`src/data/wrf_sr_dataset.py`)

**Classes:**
- `WRFSuperResDataset`: Dataset parell LR-HR per entrenament
- **Variables suportades:** U, V, W, T, P, HGT, TKE (7 canals entrada, 2 canals sortida)
- **Normalització:** Stats pre-definits per variable
- **Format:** NetCDF (.nc) amb xarray

---

### 📦 Dependències Identificades

**Core:**
```
torch>=2.0.0
torchvision>=0.15.0
numpy>=1.24.0
```

**Dades WRF:**
```
xarray>=2023.0.0
netCDF4>=1.6.0
pandas>=2.0.0
```

**Visió i Augmentació:**
```
scikit-image>=0.21.0
albumentations>=1.3.0
```

**Training i Logging:**
```
tensorboard>=2.13.0
tqdm>=4.65.0
pyyaml>=6.0
```

---

### 📁 Estat dels Datasets

| Component | Estat | Notes |
|-----------|-------|-------|
| **d05 (HR)** | ✅ OK | 366 fitxers .nc (2020 any complet) |
| | | Ubicació: `/home/oriol/data/WRF/1469893/d05/` |
| | | Dimensions: 125×119 (lat×lon) |
| **d01 (LR)** | ⚠️ PROBLEMA | Directori no existeix com a d01 |
| | | Existeix: `d04.asd05/` amb 2 fitxers de mostra |
| | | Mida fitxer: ~212MB per dia |
| **d02** | ❌ No disponible | Carpeta existent però buida |
| **Link d01→d04.asd05** | ⚠️ Configuració errònia | El README diu d01 però el codi busca a d04.asd05 |

**Accions requerides:**
1. Verificar/crear enllaç o còpia de d01 des de d04.asd05
2. O generar d01 artificialment (downsampling de d05)
3. Crear train/val/test split (80/10/10 recomanat)

---

### 🎨 Decisions de Disseny Trobades

1. **Factor d'escala:** 2× (capa PixelShuffle), però el dataset real és ~90× (9km→100m)
   - Cal implementar upscaling progressiu o múltiples etapes

2. **Variables:**
   - Entrada: 7 variables (U, V, W, T, P, HGT, TKE)
   - Sortida: 2 variables (U, V - components del vent)
   - Justificació: Downscalling específicament per camps de vent

3. **Pèrdua:** L1Loss (MAE) - més robusta a outliers que MSE

4. **Optimizer:** Adam amb lr=1e-4

5. **Upsampling:** PixelShuffle a ESRGAN, Bilinear interpolació a UNet

6. **Mètriques:** MSE, MAE, PSNR - no implementat SSIM encara

---

### ⚠️ Issues Identificats

1. **Dataset incomplet:** Falta d01 per entrenar (necessita 366 dies com d05)
2. **No hi ha mecanisme d'atenció** implementat (contradicció amb requisits ESRGAN+Attention)
3. **Sense soporte per mixed precision training**
4. **Sense test set separat** (només train/val split)
5. **No hi ha script de predict.py** (referenciat a README però no existent)

---

### 📋 Tasques Pendents (Fase 2)

- [ ] Resoldre problema del dataset d01
- [ ] Implementar mecanisme d'atenció (CBAM, Self-Attention, etc.)
- [ ] Crear script de predict.py
- [ ] Implementar mixed precision training (opt.)
- [ ] Afegir mètrica SSIM
- [ ] Configurar configs/*.yaml per entrenament

---

## Fases Posteriors (per referència)

### Fase 3: Entrenament (1-2 setmanes)
- [ ] Configurar pipeline de dades
- [ ] Definir mètriques d'avaluació
- [ ] Entrenar model base
- [ ] Hyperparameter tuning

### Fase 4: Validació i Desplegament (1 setmana)
- [ ] Testejat amb dades reals de WRF
- [ ] Comparar amb baseline
- [ ] Documentar resultats
- [ ] Crear script d'inferència

---

## Resultats Esperats

| Mètrica | Valor inicial esperat | Objectiu |
|---------|----------------------|----------|
| PSNR | 25-28 dB | >32 dB |
| SSIM | 0.70-0.75 | >0.85 |
| MAE | 1.5-2.0 m/s | <1.0 m/s |

---

**Document actualitzat:** 2026-02-08  
**Estat Fase 1:** ✅ Completat
