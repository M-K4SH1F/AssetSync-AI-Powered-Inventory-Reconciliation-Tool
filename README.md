# AssetSync — AI-Powered Inventory Reconciliation Tool

## Project Overview

AssetSync is a browser-based inventory reconciliation tool built with vanilla JavaScript and the Claude AI API. It ingests two CSV datasets — an expected inventory (system-of-record) and an actual inventory (physical count) — and automatically detects discrepancies, classifies asset statuses, and generates a professional AI-powered analysis report aligned with ISO 55000 asset lifecycle management standards.

Inspired by real-world transit asset management workflows (e.g., PRESTO fare payment systems), AssetSync is designed to support operations teams in maintaining data integrity across large equipment inventories.

---

## Key Features

- **Dual CSV Upload** — Drag-and-drop or browse to load expected and actual inventory files
- **Automated Reconciliation Engine** — Joins datasets by `asset_id` and computes delta for every record
- **Status Classification** — Each asset is flagged as: `MATCH`, `SHORTAGE`, `SURPLUS`, `MISSING`, or `NEW ITEM`
- **Live Statistics Dashboard** — Displays total assets, accuracy rate, discrepancy count, and critical item count
- **Filterable Results Table** — Filter by any status category and export a timestamped CSV report
- **AI Analysis Report** — Streams a structured report via the Claude API covering executive summary, critical findings, root cause hypotheses, recommended actions, and an ISO 55000 alignment note
- **Sample Data** — Built-in PRESTO-style transit asset sample data for instant demo

---

## Tech Stack

- **Frontend:** HTML, CSS, JavaScript (Vanilla — no frameworks)
- **AI Integration:** Anthropic Claude API (`claude-sonnet-4-20250514`) with real-time streaming
- **Data Handling:** Client-side CSV parsing, in-memory reconciliation logic
- **Export:** Blob-based CSV download

---

## How to Use

**1. Open the tool:**
Simply open `asset-reconciliation-tool.html` in any modern browser — no installation or server required.

**2. Load your inventory files:**
Upload two CSV files with the following structure:
```csv
asset_id,name,category,quantity
A001,Fare Card Reader,Ticketing,42
A002,Turnstile Gate,Access Control,18
```

Or click **"↓ Load sample data"** on both cards to use the built-in PRESTO-style transit dataset.

**3. Add your Anthropic API key:**
Paste your `sk-ant-...` API key into the field at the top to enable the AI analysis report.

**4. Run Reconciliation:**
Click **⚡ RUN RECONCILIATION** to generate the full report.

**5. Review & Export:**
- Use the filter buttons to drill into specific discrepancy types
- Click **↓ Export** to download a timestamped CSV of the reconciliation results

---

## Reconciliation Logic

| Status | Condition |
|--------|-----------|
| `MATCH` | Expected quantity equals actual quantity |
| `SHORTAGE` | Actual quantity is less than expected |
| `SURPLUS` | Actual quantity is greater than expected |
| `MISSING` | Asset exists in expected inventory but not found in actual count |
| `NEW ITEM` | Asset found in actual count but not present in expected inventory |

---

## AI Report Structure

When an Anthropic API key is provided, AssetSync streams a structured report containing:

1. **Executive Summary** — Overall inventory health assessment
2. **Critical Findings** — Highest-priority discrepancies
3. **Root Cause Hypotheses** — Likely reasons for each discrepancy type
4. **Recommended Actions** — Prioritized, actionable next steps
5. **ISO 55000 Alignment Note** — Asset lifecycle management implication

---

## Sample Data (Built-in)

The tool ships with a realistic transit asset dataset modeled after PRESTO-style infrastructure:

| Asset ID | Name | Category | Expected | Actual |
|----------|------|----------|----------|--------|
| A001 | Fare Card Reader | Ticketing | 42 | 39 |
| A002 | Turnstile Gate | Access Control | 18 | 18 |
| A003 | PRESTO Kiosk | Self-Service | 12 | 14 |
| A004 | Security Camera | Surveillance | 88 | 82 |
| A005 | Network Switch | IT Infrastructure | 24 | 24 |
| A006 | UPS Battery Unit | Power | 15 | 11 |
| A007 | Platform Display | Signage | 30 | 30 |
| A008 | Validator Terminal | Ticketing | 56 | 61 |
| A009 | Emergency Phone | Safety | 22 | 19 |
| A010 | Bench Unit | Furniture | 64 | 64 |
| A011 | Charging Station | Amenities | — | 8 |

---

## File Structure
```
AssetSync-Inventory-Reconciliation/
│
├── asset-reconciliation-tool.html   # Full application (single file)
└── README.md                        # Project documentation
```

---

## Installation

No installation needed. Just clone and open:
```bash
git clone https://github.com/M-K4SH1F/AssetSync-Inventory-Reconciliation.git
cd AssetSync-Inventory-Reconciliation
open asset-reconciliation-tool.html
```

---

## API Key Setup

This tool uses the [Anthropic Claude API](https://www.anthropic.com). To enable AI reporting:

1. Sign up at [console.anthropic.com](https://console.anthropic.com)
2. Generate an API key
3. Paste it into the **API KEY** field at the top of the app

> ⚠️ Your API key is never stored or transmitted anywhere other than directly to Anthropic's API endpoint.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
