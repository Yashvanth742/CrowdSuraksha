# CrowdSuraksha

**Smart Crowd Safety and Disaster Management for Large Gatherings**

CrowdSuraksha is a proposed prototype for improving crowd-risk awareness and emergency preparedness at festivals, pilgrimages, concerts, sporting events, fairs, rallies, and other large gatherings.

## Key features
- GIS-based risk mapping for entrances, exits, roads, medical facilities, water points, and risk zones.
- Crowd-risk monitoring with configurable green/yellow/red alerts.
- Incident reporting and status tracking.
- Emergency-response support with route suggestions that avoid known blocked roads.

> **Prototype notice:** Sample counts and incidents are simulated. This is not a certified emergency-management or dispatch system. Do not describe features as implemented unless they exist in your code.

## Proposed technology stack

| Component | Technology | Purpose |
|---|---|---|
| Frontend | React, Vite, Tailwind CSS | Dashboard |
| Mapping | Leaflet + OpenStreetMap | Map layers and locations |
| Backend | Python + FastAPI | API and application logic |
| Database | SQLite | Prototype records |
| Route analysis | NetworkX | Graph-based route suggestions |
| Optional future work | OpenCV + YOLO | Video-based person detection/crowd estimation |

OpenCV + YOLO is optional and not required for the initial prototype.

## System Architecture

The following diagram illustrates the CrowdSuraksha system architecture, data flow, and emergency route-planning process.

![CrowdSuraksha System Architecture](docs/architecture.png)

## Repository structure

```text
CrowdSuraksha/
├── README.md
├── LICENSE
├── .env.example
├── .gitignore
├── docs/TECHNICAL_DESIGN.md
├── sample_data/zones.json
├── sample_data/incidents.json
├── sample_data/routes.json
└── tests/TEST_CASES.md
```

## Setup

### Prerequisites
- Python 3.10+
- Node.js 18+ (if using the React frontend)
- Git

### 1. Clone
```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd CrowdSuraksha
```

### 2. Environment variables
Copy `.env.example` to `.env`.

Windows PowerShell:
```powershell
Copy-Item .env.example .env
```

macOS/Linux:
```bash
cp .env.example .env
```

Edit `.env` for your setup. Never commit real secrets.

### 3. Backend (FastAPI)
Create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows PowerShell:
```powershell
.venv\Scripts\Activate.ps1
```

macOS/Linux:
```bash
source .venv/bin/activate
```

After adding a `requirements.txt` for your actual backend:
```bash
pip install -r requirements.txt
```

If your entry point is `backend/main.py`, run:
```bash
uvicorn backend.main:app --reload
```

Then visit `http://127.0.0.1:8000/docs`. Adjust the command to match your actual file layout.

### 4. Frontend (React/Vite)
If your frontend is in `frontend/`:
```bash
cd frontend
npm install
npm run dev
```
Use the local URL printed by Vite, commonly `http://localhost:5173`.

### 5. Sample data
The JSON files in `sample_data/` contain fictional examples. Load them using your application's data-loading mechanism; they are not automatically imported.

## Example alert thresholds
- Green: below 60% occupancy
- Yellow: 60% to below 85%
- Red: 85% or above

These are illustrative demo thresholds, not validated safety standards. Validate with qualified safety professionals before real-world use.

## Testing
See [`tests/TEST_CASES.md`](tests/TEST_CASES.md). Add automated tests for the actual API, database, alert logic, and route-planning implementation.

## Safety, privacy, and limitations
- Clearly label simulated, stale, or missing data.
- Use fictional incident records in public demos.
- Do not commit `.env`, API keys, passwords, or tokens.
- Minimize personal data collection and restrict access to operational records.
- Crowd estimates and map information may be inaccurate or outdated.
- Route suggestions are decision-support only and require human verification.
- This prototype must not replace official emergency services.

## Roadmap
- [ ] Event map and configurable zone layers
- [ ] Occupancy display and alert thresholds
- [ ] Incident registration and status tracking
- [ ] Route suggestions around known blockages
- [ ] Automated unit and API tests
- [ ] Explore optional OpenCV/YOLO integration
- [ ] Expert review before any real-world deployment

## License
Released under the MIT License. See [`LICENSE`](LICENSE).
