# UNET4DownscalingWRF-v2.md

**Repositori:** git/UNET4DownscalingWRF-v2

**Descripció:** Versió millorada del codi original d'Oriol (git/UNET4downscallinngWRF-main).

**Objectiu:** Millorar l'arquitectura UNET per downscaling de dades WRF.

**Estat:** ✅ IMPLEMENTAT (2026-02-08) - Nou model ResUNet

---

## Nou Model: ResUNet

**Característiques:**
- Residual connections (skip connections)
- Attention gates
- Encoder/decoder millorat

**Estructura:**
```
Encoder: ResidualBlock ×4 (64→512 canals)
Bottleneck: ResidualBlock ×1 (512→1024 canals)
Decoder: Upsample + AttentionGate + ResidualBlock ×4
Output: Conv1×1 (64→2 canals per U,V)
```

---

## Fitxers nous (2026-02-08)

| Fitxer | Descripció |
|--------|------------|
| `src/models/resunet.py` | Model ResUNet amb atenció |
| `src/training/trainer.py` | Loop d'entrenament |
| `train.sh` | Script de training |

---

## Pendent

- [ ] Git push manual
- [ ] Entrenar ResUNet
- [ ] Comparar amb v1
- [ ] Hyperparameter tuning
