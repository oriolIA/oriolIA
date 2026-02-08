# SRDownscalling.md

**Repo:** https://github.com/oriolIA/SRDownscalling

**Descripció:** Super Resolution per downscaling de camps de vent WRF

**Tecnologia:** ESRGAN + Attention

**Estat:** ⚠️ CONFIGURAT (2026-02-08)

---

## Dataset

| Domini | Resolució | Dimensions | Path |
|--------|-----------|------------|------|
| d02 (pare) | ~3km | 100×100×48 | `/home/oriol/data/WRF/1469893/d02/` |
| d05 (fill) | ~100m | 125×119×48 | `/home/oriol/data/WRF/1469893/d05/` |

**Factor d'escala:** ~30×

---

## Models

### ESRGAN (~680K params)
```
Input (7×100×100) → Conv → RRDB×12 → Upsample ×2 → Output (2×125×119)
```

### UNetSR (~2.5M params)
```
Input (7×100×100) → Encoder → Bottleneck → Decoder → Output (2×125×119)
```

---

## Variables

**Input:** U, V, W, T, P, HGT, TKE (7 canals)
**Output:** U, V (2 canals)

---

## Millores pendents

- [ ] Implementar atenció (CBAM/Self-Attention)
- [ ] Entrenar model (necessita GPU)
- [ ] Afegir mètrica SSIM
- [ ] Progressive SR (múltiples etapes)

---

## Ús

```bash
python3 src/train.py --lr_dir /home/oriol/data/WRF/1469893/d02 --hr_dir /home/oriol/data/WRF/1469893/d05 --model esrgan
```
