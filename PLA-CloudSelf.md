# Pla: CloudSelf - Servei Cloud Personal/PIME

**Objectiu:** Oferir serveis al núvol (correu, drive, etc.) amb eines open source per a particulars i petites empreses

**Mercat:** Particulars + PIME (petites i mitjanes empreses)

---

## Proposta de Valor

| Aspecte | Descripció |
|---------|------------|
| **Privacitat** | Dades allotjades a servidors propis |
| **Control** | Cap dependència de multinacionals |
| **Cost** | Més econòmic que Google/Microsoft/Gmail |
| **Simplicitat** | Interfície intuïtiva |

---

## Serveis Oferits

### 🟢 Tier 1 - Essentials (Core)

| Servei | Eina | Llicència | Complexitat |
|--------|------|-----------|-------------|
| **Correu** | Mailcow | GPL-2.0 | ⭐⭐⭐ |
| **Drive/Fitxers** | Nextcloud | AGPL-3.0 | ⭐⭐⭐ |
| **Calendari/Contactes** | Nextcloud (integrat) | AGPL-3.0 | - |
| **Webmail** | SOGo o Roundcube | GPL-3.0/SIL | ⭐⭐ |

### 🟡 Tier 2 - Extended (Complementari)

| Servei | Eina | Llicència | Ús |
|--------|------|-----------|-----|
| **Drive Avançat** | Seafile | GPL-2.0 | Millor sincronització grans fitxers |
| **Drive Simple** | FileRun | GPL-3.0 | Interfície minimalista |
| **Drive Alternatiu** | Pydio Cells | AGPL-3.0 | Seguretat + Compliance |
| **Notes** | StandardNotes | MIT | Notes cifrades |
| **Passarel·la correu** | Mail-in-a-Box | BSD-3 | Solució all-in-one per correu |

### 🟠 Tier 3 - Professional (PIME)

| Servei | Eina | Llicència |
|--------|------|-----------|
| **Videoconferència** | Jitsi Meet | Apache-2.0 |
| **Xat/Comunicació** | Mattermost | MIT/Enterprise |
| **Projectes/Task** | Wekan | MIT |
| **CRM** | EspoCRM | GPL-3.0 |
| **Wiki/Documentació** | BookStack | MIT |
| **Backup** | BorgBackup + Attic | BSD-3 |

---

## Comparativa d'Eines per Servei

### 📧 Correu

| Eina | Característiques | Millor per |
|------|-----------------|------------|
| **Mailcow** | All-in-one: Postfix, Dovecot, SOGo, Rspamd | Tot-en-un, fàcil |
| **Mail-in-a-Box** | Solució mínima, Ubuntu | Principiants |
| **iRedMail** | Flexible, RHEL/CentOS/Debian | Admins avançats |
| **Poste.io** | 5 min deploy, Docker | Ràpid inici |
| **Modoboa** | Instal·lació <10 min, suport comercial | Enterprise |

### ☁️ Drive/Cloud

| Eina | Velocitat | Ús | Punts Forts |
|------|-----------|-----|-------------|
| **Nextcloud** | ⭐⭐ | All-in-one | Apps, calendar, col·laboració |
| **Seafile** | ⭐⭐⭐⭐ | Grans fitxers | Velocitat, lectió offline |
| **FileRun** | ⭐⭐⭐ | Simple | Interfície neta |
| **Pydio Cells** | ⭐⭐ | Enterprise | Seguretat, compliance |
| **ownCloud** | ⭐⭐ | Legacy | Compatible |

---

## 📊 Anàlisi de Mercat

### Competidors Existents

| Empresa | Localització | Model | Estat |
|---------|-------------|-------|-------|
| **Disroot** | EU (Països Baixos) | No-profit | ⚠️ Riscos financers |
| **Mailbox.org** | Alemanya | Subscripció | ✅ Actiu |
| **Posteo** | Alemanya | Subscripció | ✅ Actiu |
| **Tutanota** | Alemanya | freemium | ✅ Actiu |
| **ProtonMail** | Suïssa | Freemium | ✅ Actiu |
| **Webempresa** | Espanya | Hosting tradicional | ✅ Actiu |
| **Arsys** | Espanya | Hosting | ✅ Actiu |
| **Neoxea** | Espanya | Cloud | ✅ Actiu |

### Empreses que han Fallit/Tancat

| Empresa | Motiu del tancament | Lliçons |
|---------|---------------------|---------|
| **Migadu** | Models de negoci insostenibles | Cal preu mínim viable |
| **FastMail** (original) | Competència gegants | Cal diferenciar-se |
| **Lavabit** | Pressió governamental (NSA) | Jurisdicció important |

### Tendències de Mercat (2024-2025)

1. **Augment demanda privacitat** post-GDPR
2. **Fatiga de subs** - usuaris busquen alternatives més barates
3. **Cloud outsourcing** - empreses volen delegar infraestructura
4. **Regulació** - cada cop més complexa (DMA, AI Act)

---

## 🏢 Opcions d'Housing/Colocation

### Proveïdors Comparats

| Proveïdor | Localització | Preu/mes | Característiques |
|-----------|--------------|-----------|-----------------|
| **Hetzner** | Alemanya/EU | 5-20€/mes | ⭐ Millor preu/qualitat |
| **OVHcloud** | França/EU | 6-25€/mes | Suport 24h |
| **Scaleway** | França/EU | 8-30€/mes | Object storage inclòs |
| **Ionos** | Alemanya/EU | 10-30€/mes | Dominis inclosos |
| **OVH Spain** | Espanya | 15-40€/mes | Suport castellà |
| **Dinahosting** | Espanya | 12-35€/mes | Suport local |

### Recomanació per Fase

| Fase | Proveïdor | Motivació |
|------|-----------|-----------|
| **MVP** | Hetzner | Millor preu, bones specs |
| **Escala** | OVHcloud | Suport + redundancy |
| **Enterprise** | Multi-proveïdor | HA + backup geogràfic |

---

## Model de Negoci

### Tier Pricing (Proposta)

| Tier | Preu/mes | Inclou |
|------|----------|--------|
| **Particular** | 5€/mes | Correu (10GB) + Drive (50GB) |
| **Familiar** | 12€/mes | 5 comptes + Drive (250GB) |
| **PIME Starter** | 25€/mes | 10 comptes + Drive (1TB) |
| **PIME Pro** | 50€/mes | 25 comptes + Drive (5TB) + Backup |

### Ingressos vs Costos (estimació)

| Concept | Particular | Familiar | PIME Starter | PIME Pro |
|---------|------------|----------|--------------|----------|
| **Preu client** | 5€ | 12€ | 25€ | 50€ |
| **Cost servidor** | 2€ | 5€ | 10€ | 20€ |
| **Cost backup** | 1€ | 2€ | 3€ | 5€ |
| **Marge brut** | **40%** | **42%** | **48%** | **50%** |

---

## ⚠️ Riscos Identificats

| Risc | Impacte | Mitigació |
|------|---------|-----------|
| **Deliverability correu** | 🔴 Alt | SPF/DKIM/DMARC, bones pràctiques |
| **Costos servidor** | 🟠 Mitjà | Escalat progressiu |
| **Competència** | 🟠 Mitjà | Diferenciació: suport local + privacitat |
| **Jurisdicció** | 🟠 Mitjà | Servidors a UE (GDPR) |
| **Suport tècnic** | 🔴 Alt | Documentació + tutorials |
| **Seguretat** | 🔴 Alt | Updates automàtics + monitorització |

---

## Stack Tecnològic Recomanat

### Opció A: Nextcloud + Mailcow (Principal)
```
├── Nextcloud (Drive + Calendar + Contacts + Notes)
├── Mailcow (Correu + Webmail SOGo)
├── Jitsi Meet (Videoconferència)
└── Mattermost (Xat d'equip)
```

### Opció B: Separat per servei (Modular)
```
├── Seafile (Drive - velocitat)
├── Mail-in-a-Box (Correu - simple)
├── BookStack (Wiki)
└── Wekan (Projectes)
```

---

## Infrastructura Necessària

### Mínima (Particular/Familiar)
- **CPU:** 2 vCPU
- **RAM:** 4 GB
- **Disc:** 100 GB SSD + NAS per backup

### Estàndard (PIME Starter)
- **CPU:** 4 vCPU
- **RAM:** 8 GB
- **Disc:** 500 GB SSD + NAS (2TB)

### Professional (PIME Pro)
- **CPU:** 8 vCPU
- **RAM:** 16 GB
- **Disc:** 1 TB NVMe + NAS (10TB RAID)

---

## Fonts i Referències

- **Awesome-Selfhosted:** https://github.com/awesome-selfhosted/awesome-selfhosted
- **Comparativa Clouds:** Reddit r/selfhosted
- **Mail Servers:** https://runcloud.io/blog/best-self-hosted-email-server
- **Nextcloud:** https://nextcloud.com/
- **Seafile vs Nextcloud:** https://www.logicweb.com/
- **Hetzner vs OVH:** https://www.vpsbenchmarks.com/
- **Competidors EU:** European-alternatives.eu
- **Hosting Spain:** whtop.com/top.10-alexa-ranking/country-es

---

## Fase 1: Estudi de Mercat (2 setmanes) ✅ COMPLETAT
- [x] Analitzar competidors existents
- [x] Identificar empreses que han fallit
- [x] Definir opcions housing
- [x] Definir preus exactes

## Fase 2: MVP (1 mes)
- [ ] Implementar Nextcloud + Mailcow
- [ ] Configurar domini i certificats
- [ ] Testeig privat
- [ ] Landing page

## Fase 3: Llançament (2 setmanes)
- [ ] Onboarding automatitzat
- [ ] Documentació d'usuari
- [ ] Suport tècnic bàsic
