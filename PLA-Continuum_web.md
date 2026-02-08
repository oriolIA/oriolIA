# PLA - Continuum Web

## Resum del Projecte

**Continuum** és un toolkit eòlic open-source desenvolupat per One Power Company per a anàlisi de recursos eòlics. La versió original és una aplicació Windows Forms (C#). L'objectiu és portar a interfície web/servidor.

## Funcionalitats Principals Identificades

### 1. Met Data Filtering
- **Arxiu:** `Met_Data_Filter.cs` (~127KB)
- Filtratge de dades metereològiques (CSV)
- Filtres: ombra de torre, gel, desviació estàndard vent
- Càlcul de shear power law i extrapolació a hub height
- Suport per anemòmetres, vetuments, sensors temperatura/pressió

### 2. MCP (Measure-Correlate-Predict)
- **Arxiu:** `MCP.cs` (~92KB)
- Correlació de dades entre estacions de referència i objectiu
- Mètodes: Orthogonal Regression, Method of Bins, Matrix-LastWS
- Anàlisi d'incertesa per finestres temporals
- Suport per sectors de direcció, hora del dia i estacions

### 3. Wake Loss Modeling
- **Arxiu:** `WakeCollection.cs` (~96KB) i `Wake_Model.cs`
- Modelat de pèrdues per wake (efecte d'ombra entre turbines)
- Mapes de wake 2D/3D
- Càlculs sector-wise i globals
- Múltiples models de wake suportats

### 4. Altres Funcionalitats
- **Topografia:** `TopoInfo.cs` - Models digitals d'elevació, coberta del sòl
- **Reanalysis Data:** `MERRA.cs`, `Reanalysis_Download.cs` - Dades ERA5, MERRA-2
- **Turbines:** `Turbine.cs` - Curva de potència, paràmetres turbines
- **Anàlisi:** `SiteSuitability.cs`, `Exposure.cs` - Complexitat terreny, exposició

## Dependències i Requisits Tècnics (C# Original)

### Paquets NuGet
- `MathNet.Numerics` - Càlculs numèrics
- `Microsoft.Research.Science.Data` - Lectura dades científiques
- `NLog` - Logging
- `OSGeo.GDAL`, `OSGeo.OGR`, `OSGeo.OSR` - GIS/Topografia (GDAL)

### Requisits Sistema
- .NET Framework / C#
- Windows Forms (GUI)
- GDAL per dades geoespacials
- Python (scripts ERA5/MERRA)

## Decisió: Stack Tecnològic

### Opció A: Python/FastAPI (RECOMANAT)
**Avantatges:**
- Compatible amb scripts Python existents (ERA5, MERRA)
- Llibreries científiques madures (NumPy, SciPy, pandas)
- API moderne, asíncron, escalable
- Millor per ML/IA
- Open-source friendly

**Desavantatges:**
- Diferent del codi original C#
- Cal portar lògica de negoci

### Opció B: C# + ASP.NET Core
**Avantatges:**
- Reutilització de codi existent (classes C#)
- Continuïtat tècnica
- Rendiment elevat

**Desavantatges:**
- Menys llibreries web modernes
- Ecosistema menys flexible

### Opció C: Node.js
**Avantatges:**
- Javascript/TypeScript a tot arreu
- NPM ecosistema vast
- Ideal per frontends React/Vue

**Desavantatges:**
- Cal riscribir lògica científica
- Menys adequat per càlculs numèrics

## Recomanació Final

**Python/FastAPI** és l'opció més adequada per:
1. Compatibilitat amb scripts Python existents
2. Ecosistema científic superior
3. Facilitat de portar algoritmes de C# a Python
4. Trend en aplicacions web modernes
5. Possibilitat d'usar Jupyter per anàlisi interactiva

## Estat Actual

- **Repo C# original:** `/home/oriol/git/Continuum` (pujat a GitHub)
- **Repo Web:** `/home/oriol/git/Continuum_web` (cal netejar i pujar)

## Següents Passos (Fase 2)

1. Netejar fitxers contaminats de Continuum_web
2. Portar core logic (MCP, Wake, Filtering) a Python
3. Crear API FastAPI amb endpoints per cada funcionalitat
4. Desenvolupar frontend web (React/Vue)
5. Integrar dades GIS/GDAL

## Referències
- Web: https://www.continuumwind.com/
- GitHub Original: https://github.com/oneenergy-software/Continuum
