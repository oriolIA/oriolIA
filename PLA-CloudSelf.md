# Pla: CloudSelf - Servei Cloud Personal/PIME

**Objectiu:** Oferir serveis al núvol (corre, drive, etc.) amb eines open source per a particulars i petites empreses

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
| **Notes** | standardNotes | MIT | Notes cifrades |
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
| **Postfix+Dovecot** | Manual | Màxima personalització |

### ☁️ Drive/Cloud

| Eina | Velocitat | Ús | Punts Forts |
|------|-----------|-----|-------------|
| **Nextcloud** | ⭐⭐ | All-in-one | Apps, calendar, collaboració |
| **Seafile** | ⭐⭐⭐⭐ | Grans fitxers | Velocitat, lectió offline |
| **FileRun** | ⭐⭐⭐ | Simple | Interfície neta |
| **Pydio Cells** | ⭐⭐ | Enterprise | Seguretat, compliance |
| **ownCloud** | ⭐⭐ | Legacy | Compatible |

---

## Model de Negoci

### Tier Pricing (Proposta)

| Tier | Preu/mes | Inclou |
|------|----------|--------|
| **Particular** | 5€/mes | Correu (10GB) + Drive (50GB) |
| **Familiar** | 12€/mes | 5 comptes + Drive (250GB) |
| **PIME Starter** | 25€/mes | 10 comptes + Drive (1TB) |
| **PIME Pro** | 50€/mes | 25 comptes + Drive (5TB) + Backup |

---

## Stack Tecnològic Recomanat

### Opció A: Nextcloud + Mailcow
```
├── Nextcloud (Drive + Calendar + Contacts + Notes)
├── Mailcow (Correu + Webmail SOGo)
├── Jitsi Meet (Videoconferència)
└── Mattermost (Xat d'equip)
```

### Opció B: Separat per servei
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
- **Comparativa Clouds:** https://www.reddit.com/r/selfhosted/
- **Mail Servers:** https://runcloud.io/blog/best-self-hosted-email-server
- **Nextcloud:** https://nextcloud.com/
- **Seafile vs Nextcloud:** https://www.logicweb.com/

---

## Fase 1: Estudi de Mercat (2 setmanes)
- [ ] Analitzar competidors locals
- [ ] Definir preus exactes
- [ ] Crear landing page

## Fase 2: MVP (1 mes)
- [ ] Implementar Nextcloud + Mailcow
- [ ] Configurar domini i certificats
- [ ] Testeig privat

## Fase 3: Llançament (2 setmanes)
- [ ] Onboarding automatitzat
- [ ] Documentació d'usuari
- [ ] Suport tècnic bàsic
