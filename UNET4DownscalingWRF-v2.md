# UNET4DownscalingWRF-v2.md

**Repo:** https://github.com/oriolIA/UNET4DownscalingWRF-v2

**Descripció:** Versió millorada del UNET per downscaling WRF

**Objectiu:** Millorar l'arquitectura UNET original

**Estat:** ✅ IMPLEMENTAT (2026-02-08)

---

## Nou Model: ResUNet

**Característiques:**
- ✅ Residual connections (skip connections)
- ✅ Attention gates
- ✅ Encoder/decoder millorat

**Arquitectura:**
```
Encoder: ResidualBlock ×4 (64→512 canals)
Bottleneck: ResidualBlock ×1 (512→1024 canals)
Decoder: Upsample + AttentionGate + ResidualBlock ×4
Output: Conv1×1 (64→2 canals per U,V)
```

---

## Mètriques disponibles

| Mètrica | Implementada |
|---------|-------------|
| MSE | ✅ |
| MAE | ✅ |
| PSNR | ✅ |
| SSIM | ✅ |

---

## Scripts

| Arxiu | Descripció |
|-------|------------|
| `src/models/resunet.py` | Model ResUNet |
| `src/training/trainer.py` | Loop d'entrenament |
| `src/utils/metrics.py` | Mètriques |
| `src/utils/scheduler.py` | LR Schedulers |
| `train.sh` | Script de training |

---

## Millores pendents

- [ ] Entrenar ResUNet (necessita GPU)
- [ ] Comparar amb v1 (SRDownscalling UNetSR)
- [ ] Hyperparameter tuning
- [ ] Mixed Precision (FP16)
- [ ] Early Stopping

---

## Ús

```bash
# Entrenar
./train.sh

# O directament
python3 -m src.training.trainer --lr_dir /home/oriol/data/WRF/1469893/d02 --hr_dir /home/oriol/data/WRF/1469893/d05 --model resunet
```
