# MTConnectForge Pro

## ANSI/MTC1.4-2018 (MTConnect v2.x) Semantic Machine Tool Studio & OEE Analytics (v1.0.0)

[![Standard: ANSI/MTC1.4-2018](https://img.shields.io/badge/Standard-ANSI%2FMTC1.4--2018-00f2fe.svg)](https://www.mtconnect.org) [![Interoperability: ISO 23247 & umati](https://img.shields.io/badge/Interoperability-ISO_23247_%26_umati-10b981.svg)](https://umati.org) [![Auditor Score: 100%](https://img.shields.io/badge/Normative_Audit-100%25_PASS-10b981.svg)](./documentation/ARCHITECTURE.md) [![Tests: 10/10 Passed](https://img.shields.io/badge/Tests-10%2F10_Passed-10b981.svg)](./test_mtconnect.py)

**MTConnectForge Pro** is an open semantic manufacturing studio, 5-axis CNC digital twin simulator, and shopfloor OEE analytics platform conforming to **ANSI/MTC1.4-2018 (MTConnect v2.x)**. It accelerates Industry 4.0 data acquisition, cutting tool management under ISO 13399, and overall machine productivity tracking across heterogeneous CNC fleets (Mazak, DMG MORI, Okuma, Haas, Fanuc, Siemens Sinumerik).

---

### Key Capabilities

- **MTConnect Agent REST API Simulator**: Generates compliant XML and JSON payloads for `/probe` (Component Hierarchy), `/current` (Real-Time Snapshot), and `/assets` (Tooling Metadata) with monotonic buffer sequence tracking.  
- **Three-Tier Semantic Data Model**: Full support for continuous physical `SAMPLE` items, discrete machine `EVENT` states, and multi-state `CONDITION` diagnostics.  
- **5-Axis Simultaneous Kinematic Digital Twin**: Interactive 2D canvas displaying linear travel axes (\$X, Y, Z\$ in mm), rotary table (\$C\$ in degrees), trunnion tilt (\$A\$ in degrees), and real-time spindle load.  
- **SEMI E10 OEE & Carbon Analytics**: Calculates Availability, Performance, and Quality components, along with machine power consumption (kWh) and carbon emissions per part.  
- **ISO 13399 Cutting Tool Asset Tracker**: Models tool geometry, nominal dimensions, functional lengths, cutting diameters, and remaining cutting life countdowns.  
- **10-Point Normative Protocol Auditor**: Validates data streams against ANSI/MTC1.4, MTConnect schema rules, SI unit standards, and digital twin interoperability.  
- **Standalone Python 3 CLI**: Command-line tool (`build/mtconnect-cli.py`) for automated CI/CD pipeline verification and batch machine data collection.

---

### Getting Started

#### Web Studio

Open `source-code/index.html` in any web browser. Zero external dependencies or build servers required.

#### Command-Line Tool

\# Generate MTConnectStreams Current XML snapshot

./build/mtconnect-cli.py current \--exec ACTIVE \--rpm 8500 \--load 42.5

\# Generate MTConnectDevices Probe XML

./build/mtconnect-cli.py probe \--device "Mazak\_Variaxis\_i700"

\# Calculate OEE and productivity metrics

./build/mtconnect-cli.py oee \--planned 480 \--operating 410 \--parts 160 \--defects 4 \--cycle 140

\# Run 10-point normative compliance audit

./build/mtconnect-cli.py audit

\# Generate ISO 13399 cutting tool assets

./build/mtconnect-cli.py assets

---

### Automated Verification

Run the unit test suite:

python3 test\_mtconnect.py \-v

*Result: 10/10 tests passed in 0.54s.*