# Pla: SRDownscalling

**Repositori:** git/SRDownscalling  
**Objectiu:** Crear un model de Super Resolution per downscaling de camps de vent WRF  
**Tecnologia:** ESRGAN + Attention

---

## Fases

### Fase 1: Anàlisi i Documentació (1-2 dies)
- [ ] Revisar codi existent a git/SRDownscalling
- [ ] Documentar arquitectura actual (capes, fluxes de dades)
- [ ] Identificar dependències (PyTorch, libraries, etc.)
- [ ] Verificar datasets disponibles per entrenament

### Fase 2: Millores d'Arquitectura (3-5 dies)
- [ ] Implementar mecanismes d'atenció si no existeixen
- [ ] Optimitzar arquitectura ESRGAN per camps de vent
- [ ] Afegir suport per múltiples resolucions d'entrada
- [ ] Implementar mixed precision training si cal

### Fase 3: Entrenament (1-2 setmanes)
- [ ] Configurar pipeline de dades
- [ ] Definir mètriques d'avaluació (PSNR, SSIM, mètriques específiques de vent)
- [ ] Entrenar model base
- [ ] Hyperparameter tuning

### Fase 4: Validació i Desplegament (1 setmana)
- [ ] Testejat amb dades reals de WRF
- [ ] Comparar amb baseline (SRDownscalling original d'Oriol)
- [ ] Documentar resultats
- [ ] Crear script d'inferència

---

## Dependències Externes
- Dades WRF per entrenament
- GPU per entrenament (recomanat: NVIDIA amb >=16GB VRAM)

---

## Prioritat: ⭐⭐⭐ (Alta)  
**Nota:** Desenvolupament des de zero, sense referència del codi original.
