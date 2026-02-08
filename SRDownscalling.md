# SRDownscalling.md

**Repositori:** git/SRDownscalling

**Descripció:** Implementació nova de Super-Resolution per downscaling de camps de vent WRF.

**Tecnologia:** ESRGAN + Attention

**Objectiu:** Crear un model de Super Resolution des de zero (no còpia del SRDownscalling original d'Oriol).

**Estat:** ⚠️ CONFIGURAT (2026-02-08) - Canviat d01 → d02

---

## Canvi (2026-02-08)

| Abans | Ara |
|-------|-----|
| d01 (LR, ~9km) | d02 (LR, ~3km) |
| 50×51 | 100×100 |
| Directori no existeix | 366 fitxers existents |

---

## Dataset

| Domini | Resolució | Dimensions | Path |
|--------|-----------|------------|------|
| d02 (pare) | ~3km | 100×100×48×9 | `/home/oriol/data/WRF/1469893/d02/` |
| d05 (fill) | ~100m | 125×119×48×9 | `/home/oriol/data/WRF/1469893/d05/` |

---

## Pendent

- [ ] Git push manual
- [ ] Entrenar model ESRGAN/UNetSR
- [ ] Implementar atenció (CBAM/Self-Attention)
- [ ] Afegir mètrica SSIM
