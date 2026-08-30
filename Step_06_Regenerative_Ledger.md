## MEES - The One
### Step 06: Regenerative Ledger (DATA ARCHITECTURE)
**Status:** DRAFT — Technical Specification  
**Purpose:** Define the data structure, schema, and access protocols for the Regenerative Ledger — the graph-based accounting system that tracks flows, stocks, and health scores.

---

### 1. The Ledger Principle

The Regenerative Ledger is **not a spreadsheet of money**.

It is a **graph database** that tracks:
- **Nodes:** Everything that matters (people, soil, water, forests, machines, communities, knowledge)
- **Edges:** Flows between nodes (energy, materials, care, information, capital)
- **Properties:** Health scores, timestamps, provenance, and quantitative values

This structure allows MEES to answer questions like:
- *"Is the soil health in Microclimate 001 improving or declining?"*
- *"How much community care work flows through this neighbourhood?"*
- *"What is the carbon drawdown per unit of investment in regeneration?"*
- *"Which nodes are deteriorating fastest — and why?"*

---

### 2. Node Schema

Every node has the following properties:

| Property | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| `id` | String (UUID) | Unique identifier for the node | Yes |
| `type` | Enum | Node type (see below) | Yes |
| `name` | String | Human-readable name | Yes |
| `location` | GeoJSON | Physical location (if applicable) | Optional |
| `health_score` | Float (0–100) | Current health status | Yes |
| `health_history` | Array of {timestamp, score} | Historical health scores | Yes |
| `created_at` | ISO 8601 timestamp | When the node was created | Yes |
| `updated_at` | ISO 8601 timestamp | When the node was last updated | Yes |
| `provenance` | Object | Source and methodology | Yes |

**Node Types:**

| Type | Description | Examples |
| :--- | :--- | :--- |
| `HUMAN` | Individual person | Participant, farmer, elder |
| `COMMUNITY` | Group of humans | Neighbourhood, cooperative, school |
| `SOIL` | Soil plot | Agricultural land, forest floor |
| `WATER` | Water body | River, lake, aquifer |
| `FOREST` | Forest or woodland | Managed forest, urban canopy |
| `BIOME` | Larger ecological unit | Watershed, ecosystem |
| `MACHINE` | Physical infrastructure | Solar panel, irrigation system |
| `KNOWLEDGE` | Information asset | Skills database, local wisdom |
| `CAPITAL` | Financial or material stock | Investment fund, building stock |
| `INSTITUTION` | Organizational entity | University, council, cooperative |
| `MICROCLIMATE` | MEES experimental unit | Microclimate 001 |

---

### 3. Edge Schema

Every edge has the following properties:

| Property | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| `id` | String (UUID) | Unique identifier | Yes |
| `source_id` | String | ID of source node | Yes |
| `target_id` | String | ID of target node | Yes |
| `type` | Enum | Flow type (see below) | Yes |
| `value` | Object | Quantitative value (unit + amount) | Yes |
| `timestamp` | ISO 8601 timestamp | When the flow occurred | Yes |
| `provenance` | Object | Source and methodology | Yes |
| `verification_status` | Enum | Unverified / Verified / Challenged | Yes |

**Edge (Flow) Types:**

| Type | Description | Unit Examples |
| :--- | :--- | :--- |
| `ENERGY` | Physical energy flow | kWh, MJ, calories |
| `MATERIAL` | Physical materials flow | kg, tonnes, m³ |
| `FOOD` | Food or agricultural product | kg, litres, units |
| `WATER` | Water flow | m³, litres |
| `CARE` | Care work (unpaid) | hours, N/A |
| `KNOWLEDGE` | Information flow | sessions, trainings |
| `CAPITAL` | Financial flow | currency units |
| `DEBT` | Debt obligation | currency units |
| `REGENERATIVE` | Active restoration flow | m² restored, tonnes sequestered |
| `SPILLOVER` | Cross-boundary flow | varies |

---

### 4. Health Score Calculation

Each node's health score (0–100) is calculated as a weighted composite:

| Node Type | Weighting |
| :--- | :--- |
| `HUMAN` | Based on FI components (survey, health records) |
| `SOIL` | Organic matter %, biodiversity, compaction |
| `WATER` | Chemical purity, biological activity, flow rate |
| `FOREST` | Canopy cover, species richness, age distribution |
| `COMMUNITY` | FI + RsI components aggregated |
| `MACHINE` | Maintenance status, efficiency, lifespan remaining |
| `KNOWLEDGE` | Accessibility, relevance, currency |

**Example Soil Health Score:**
