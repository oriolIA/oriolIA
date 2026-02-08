# MEMORY.md - Long-Term Memory

## Core Identity

**Name:** clawbot
**Vibe:** Concise, friendly, helpful
**Preferred Language:** Catalan

## User Preferences

**User:** Oriol
**Timezone:** Europe/Madrid (Barcelona)
**Preferences:**
- Concise, friendly responses
- Work in Catalan when possible
- Proactive but ask before external actions
- Never auto-reply in group chats

## Projects

### 1. Continuum Web
**Status:** v2.1 Complete
**URL:** https://github.com/oriolIA/Continuum_web
**Stack:** Python/FastAPI + React frontend
**Features:**
- Met Data Filtering (QC, tower shadow, ice detection)
- MCP (Orthogonal, Bins, Matrix methods)
- Neural MCP (PyTorch MLP)
- Wake Modeling (Jensen, Larsen)
- Layout Design (Grid, Staggered, GA optimization)
- Project Management (create, save, load, export)
- GIS File Loaders (.nc, .tiff, .tif, .csv, .txt, .shp)

### 2. SRDownscalling
**Status:** Configured with d02 → d05
**URL:** https://github.com/oriolIA/SRDownscaling
**Stack:** PyTorch ESRGAN + UNetSR
**Note:** d02 used as LR instead of missing d01

### 3. UNET4DownscalingWRF-v2
**Status:** ResUNet Implemented
**URL:** https://github.com/oriolIA/UNET4DownscalingWRF-v2
**Features:**
- ResUNet with residual connections
- Attention gates
- MSE, MAE, PSNR, SSIM metrics

## Repositories

| Repo | Location |
|------|----------|
| oriolIA | /home/oriol/git/oriolIA |
| Continuum_web | /home/oriol/git/Continuum_web |
| SRDownscalling | /home/oriol/git/SRDownscaling |
| UNET4DownscalingWRF-v2 | /home/oriol/git/UNET4DownscalingWRF-v2 |

## Technical Notes

### GitHub Access
- Token stored in environment variables
- Commands: `git remote set-url origin https://ghp_TOKEN@github.com/...`

### Data Paths
- WRF Data: /home/oriol/data/WRF/1469893/
- d02: /home/oriol/data/WRF/1469893/d02/ (LR, ~3km)
- d05: /home/oriol/data/WRF/1469893/d05/ (HR, ~100m)

### Continuum Original
**Location:** /home/oriol/git/Continuum
**Analyzed:** All menus and tabs documented
**Reference:** 102,895 lines of C# code

## Lessons Learned

1. **Always work in /home/oriol/git/ directories**, not sandbox
2. **Python version compatibility matters** (3.11 vs 3.13)
3. **Document all original features before replicating**
4. **Use tokens for GitHub operations in sandboxed environments**

## Working Directory

**Main workspace:** /home/oriol/git/oriolIA/

## Wave Watcher

**Automated cron job** for Barcelona wave forecasting:
- Triggers when Hs >= 1.0m AND Tp >= 7s
- Data source: Open-Meteo Marine API
