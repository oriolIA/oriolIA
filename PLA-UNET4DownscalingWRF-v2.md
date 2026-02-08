# Pla: UNET4DownscalingWRF-v2

**Repositori:** git/UNET4DownscalingWRF-v2  
**Objectiu:** Millorar l'arquitectura UNET original per downscaling de dades WRF  
**Base:** git/UNET4downscallinngWRF-main (codi original d'Oriol)

---

## Fases

### Fase 1: Anàlisi Comparativa (1 dia)
- [ ] Revisar codi de UNET4downscallinngWRF-main (original)
- [ ] Revisar codi de UNET4DownscalingWRF-v2 (millores existents)
- [ ] Documentar diferències entre v1 i v2
- [ ] Identificar quines millores s'han implementat

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

## Dependències Externes
- Dades WRF originals (mateix dataset que v1 per comparació)
- Scripts de preprocessament

---

## Prioritat: ⭐⭐⭐ (Alta)  
**Nota:** Basat en codi existent d'Oriol. Millorar el que ja funciona.
