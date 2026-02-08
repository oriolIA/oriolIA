# Pla: UNET4DownscalingWRF-v2

**Repositori:** git/UNET4DownscalingWRF-v2  
**Objectiu:** Millorar l'arquitectura UNET original per downscaling de dades WRF  
**Base:** git/UNET4downscallinngWRF-main (codi original d'Oriol)

---

## Fases

### Fase 1: Anàlisi Comparativa (1 dia) ✅ COMPLETADA
- [x] Revisar codi de UNET4downscallinngWRF-main (original)
- [x] Revisar codi de UNET4DownscalingWRF-v2 (millores existents)
- [x] Documentar diferències entre v1 i v2
- [x] Identificar quines millores s'han implementat

### Fase 2: Millores Tècniques (3-5 dies)
- [ ] Optimitzar arquitectura encoder/decoder
- [ ] Afegir skip connections més efectives
- [ ] Implementar attention gates si cal
- [ ] Millorar normalització de dades

### Fase 3: Entrenament i Avaluació (1 setmana)
- [ ] Comparar rendiment v1 vs v2
- [ ] Entrenar amb datasets ampliats
- [ ] Mètriques: MAE, RMSE, score específic per vent

### Fase 4: Documentació i Desplegament (2-3 dies)
- [ ] Documentar canvis respecte v1
- [ ] Crear benchmarks comparatius
- [ ] Exportar model per inferència

---

## Anàlisi Comparativa: V1 vs V2

### 📋 Resum de l'Arquitectura V1 (SRDownscalling)

**Ubicació:** `/home/oriol/.openclaw/workspace/git/SRDownscalling/`

**Components principals:**

| Component | Fitxer | Descripció |
|-----------|--------|-------------|
| **Model UNetSR** | `src/models/unet_sr.py` | UNet bàsic amb DoubleConv, MaxPool, ConvTranspose2d |
| **Model ESRGAN** | `src/models/esrgan.py` | ESRGAN amb RRDB blocks per SR |
| **Dataset** | `src/data/wrf_sr_dataset.py` | Dataset paired LR-HR per WRF |
| **Training** | `src/train.py` | Loop d'entrenament bàsic |

**Arquitectura UNetSR (V1):**
```
Input (7 canals) → Conv3x3 + ReLU → Upsample(scale_factor)
    ↓
Encoder: DoubleConv ×3 (64→64→128→256 canals)
    ↓ MaxPool2d
Bottleneck: DoubleConv (512 canals)
    ↓ ConvTranspose2d
Decoder: Skip connections → DoubleConv ×3 (256→128→64→64)
    ↓
Output: Conv1x1 (2 canals: U, V)
```

**Característiques V1:**
- InstanceNorm2d a les capes de convolució
- ReLU inplace activation
- Upsample inicial amb Bilinear interpolation
- Mètriques: MSE, MAE, PSNR
- Optimitzador: Adam (lr=1e-4)
- Loss: L1Loss
- Variables WRF: U, V, W, T, P, HGT, TKE

---

### 📋 Resum de l'Arquitectura V2 (UNET4DownscalingWRF-v2)

**Ubicació:** `/home/oriol/.openclaw/workspace/git/UNET4DownscalingWRF-v2/`

**Components principals:**

| Component | Fitxer | Descripció |
|-----------|--------|-------------|
| **Mètriques avançades** | `src/utils/metrics.py` | MSE, MAE, PSNR, **SSIM** |
| **LR Schedulers** | `src/utils/scheduler.py` | Step, Exp, Cosine, **ReduceLROnPlateau** |
| **Factory pattern** | `src/utils/` | Sistema extensible de schedulers |
| **Scripts de deploy** | `scripts/` | Deploy a GPU, train, quick_test |

**Nova mètrica SSIM (V2):**
```python
def ssim(pred, target, window_size=11):
    """Structural Similarity Index - nova a V2"""
    # Calcula similaritat estructural entre predicció i target
    # Millor correlació perceptual amb dades meteorològiques
```

**Schedulers disponibles (V2):**
| Scheduler | Ús recomanat |
|-----------|--------------|
| `step` | Decaïment cada N èpoques |
| `exp` | Decaïment exponencial |
| `cosine` | Oscil·lació cosinusoidal |
| `plateau` | **Automàtic quan val_loss no millora** |

---

### 📊 Comparació de Canvis (V1 → V2)

| Aspecte | V1 (Original) | V2 (Millorat) | Millora? |
|---------|---------------|---------------|-----------|
| **SSIM** | ❌ No disponible | ✅ Implementat | ✅ Sí |
| **LR Scheduler** | ❌ Cap | ✅ 4 tipus (step, exp, cosine, plateau) | ✅ Sí |
| **ReduceLROnPlateau** | ❌ No | ✅ Automàtic | ✅ Sí |
| **Estructura modular** | ⚠️ Bàsica | ✅ Factory pattern | ✅ Sí |
| **Scripts de deploy** | ⚠️ Generats dinàmicament | ✅ Scripts preparats | ✅ Sí |
| **TensorBoard** | ❌ No | ✅ Preparat als scripts | ✅ Sí |
| **Mètriques** | MSE, MAE, PSNR | + SSIM | ✅ Sí |
| **Configuració** | Arguments CLI | YAML + CLI | ⚠️ En procés |

**Canvis principals implementats a V2:**

1. **Sistema de mètriques SSIM**
   - Similaritat estructural completa
   - Window size configurable
   - Millor per dades de vent (U, V)

2. **Sistema de schedulers**
   - Factory per crear schedulers dinàmicament
   - Suport per ReduceLROnPlateau (patience=10)
   - Configurable per èpoques i gamma

3. **Reorganització del codi**
   - Utils separats en mòduls
   - Factory pattern per extensibilitat
   - Scripts de deployment preparats

4. **Scripts de treball**
   - `quick_test.sh` - Test ràpid del model
   - `train.sh` - Entrenament a GPU
   - `deploy_to_gpu.sh` - Deploy a servidor remot

---

### 🔍 Recomanacions per a Futures Millores

**Prioritat alta (immediata):**
1. **Implementar model UNet millorat a V2**
   - Actualment V2 només té utils, no té modelsNous models basats en V1 amb millores
   - Afegir ResUNet amb skip connections millorades

2. **Completar sistema de configuració**
   - Afegir `src/config/config.py` amb ModelConfig
   - Suportar YAML/JSON configs
   - Factory per models (UNetFactory)

3. **Integrar training loop millorat**
   - Afegir `src/training/trainer.py` amb suport per:
     - Early stopping
     - Model checkpointing
     - Logging a TensorBoard

**Prioritat mitjana (properes setmanes):**
4. **Attention Gates**
   - Afegir mecanisme d'atenció al decoder
   - Millor focus en regions importants

5. **Mixed Precision Training**
   - FP16 per accelerar entrenament
   - Reduir ús de memòria GPU

6. **Data Augmentation**
   - Rotacions aleatòries
   - Flip horizontal/vertical
   - Random crop

**Prioritat baixa (futur):**
7. **Hyperparameter Tuning**
   - Optuna o Ray Tune
   - Buscar millors n_filters, lr, etc.

8. **Ensemble Models**
   - Combinar UNetSR + ESRGAN
   - Millor robustesa

9. **Temporal Modeling**
   - Afegir components LSTM per dades temporals
   - 3D convolutions per time-series

---

## 📁 Fitxers Clau

**V1 (Base):**
- `/home/oriol/.openclaw/workspace/git/SRDownscalling/src/models/unet_sr.py`
- `/home/oriol/.openclaw/workspace/git/SRDownscalling/src/train.py`
- `/home/oriol/.openclaw/workspace/git/SRDownscalling/src/data/wrf_sr_dataset.py`

**V2 (Millores):**
- `/home/oriol/.openclaw/workspace/git/UNET4DownscalingWRF-v2/src/utils/metrics.py`
- `/home/oriol/.openclaw/workspace/git/UNET4DownscalingWRF-v2/src/utils/scheduler.py`
- `/home/oriol/.openclaw/workspace/git/UNET4DownscalingWRF-v2/setup_and_train.sh`

---

## Dependències Externes
- Dades WRF originals (mateix dataset que v1 per comparació)
- Scripts de preprocessament
- GPU server per entrenament

---

## Prioritat: ⭐⭐⭐ (Alta)  
**Nota:** Basat en codi existent d'Oriol. Millorar el que ja funciona.

**Resum de l'estat actual:**
- V1: Funcionant, model UNetSR bàsic
- V2: Utils preparats, cal implementar models millorats
- Pendent: Integrar millores tècniques i comparar rendiment
