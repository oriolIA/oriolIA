# Pla: Continuum_web

**Repositori:** git/Continuum_web  
**Objectiu:** Portar el toolkit eòlic Continuum a interfície web/servidor  
**Font:** https://www.continuumwind.com/ + git/Continuum  
**Tecnologia actual:** C# (.NET)

---

## Fases

### Fase 1: Anàlisi i Planificació (2-3 dies)
- [ ] Revisar codi de git/Continuum (1 dia)
- [ ] Revisar documentació a continuumwind.com (1 dia)
- [ ] Identificar funcionalitats a migrar:
  - Met data filtering
  - MCP (Measure-Correlate-Predict)
  - Wake loss modeling
- [ ] Decidir stack tecnològic web

### Fase 2: Disseny d'Arquitectura (2 dies)
- [ ] Dissenyar API REST/GraphQL
- [ ] Definir base de dades per projectes/usuaris
- [ ] Dissenyar interfície (frontend)
- [ ] Planificar separació codi C# → Web API

### Fase 3: Implementació Backend (2-3 setmanes)
- [ ] Crear projecte web (Python/FastAPI o Node.js)
- [ ] Migrar funcionalitats del toolkit C#:
  - [ ] Endpoint: upload de dades met
  - [ ] Endpoint: filtrat de dades
  - [ ] Endpoint: MCP
  - [ ] Endpoint: wake loss modeling
- [ ] Integració amb base de dades

### Fase 4: Implementació Frontend (2 setmanes)
- [ ] Crear interfície web
- [ ] Visualització de dades
- [ ] Dashboard de projectes
- [ ] Formulari d'uploads

### Fase 5: Desplegament (1 setmana)
- [ ] Configurar Docker/containers
- [ ] Desplegar a servidor
- [ ] Testing complet
- [ ] Documentació d'usuari

---

## Opcions Tecnològiques

### Opció A: Python (FastAPI)
- ✅ Python + ML/Numpy natural fit
- ⚠️ Cal traduir codi C# a Python
- **Recomanat:** Més fàcil per integració amb ML

### Opció B: Node.js
- ✅ Javascript/TypeScript end-to-end
- ⚠️ Cal API wrapper del C#
- Millor per interfície moderna

### Opció C: Mantenir C# + Blazor
- ✅ Codi C# existent reutilitzable
- ⚠️ Menys flexible per web modern
- Menys comunitat

---

## Dependències Externes
- Servidor web amb Docker
- Base de dades (PostgreSQL/MongoDB)
- Possible: API wrapper del C#

---

## Prioritat: ⭐⭐ (Mitjana)  
**Nota:** Repte complex - migració de codi + nova interfície. Molta feina.
