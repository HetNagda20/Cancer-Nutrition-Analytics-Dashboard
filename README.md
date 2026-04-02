# Cancer Nutrition Analytics Dashboard

An interactive data visualization dashboard exploring the relationship between nutritional habits, lifestyle factors, BMI, and cancer outcomes across the United States — built with React and D3.js.

---

## Overview

This dashboard analyzes NHANES (National Health and Nutrition Examination Survey) data enriched with synthetic state-level assignments. It allows users to explore how diet, physical activity, and BMI correlate with cancer prevalence across demographic groups and U.S. states.

---

## Features

- **BMI Beeswarm Plot** — visualizes individual patient BMI distribution, color-coded by cancer status and weight category. Click any dot to select a patient.
- **U.S. Choropleth Map** — shows average lifestyle scores by state. Click a state to filter all charts.
- **Sankey Flow Diagram** — traces patient flow from fiber intake → sugar intake → BMI category. Click nodes or links to filter.
- **Radar Chart** — displays a selected patient's nutritional profile vs. national averages.
- **Parallel Coordinates** — compares a patient's Day 1 vs. Day 2 dietary intake across five nutrients.
- **Diverging Bar Chart** — shows how a selected state's health scores compare to the national average.
- **Neighboring States Plot** — compares cancer rates across geographically neighboring states.

### Filters
- Age range, BMI range, gender
- Patient ID search (highlights individual in beeswarm)
- State selection via map click
- Sankey node/link click filtering

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI Framework | React 18 |
| Visualization | D3.js v7 |
| Flow Diagram | d3-sankey |
| Map Topology | TopoJSON / us-atlas |
| Styling | CSS (custom dark theme) |
| Fonts | DM Sans, DM Mono |
| Deployment | GitHub Pages |

---

## Getting Started

### Prerequisites
- Node.js v16+ and npm

### Installation

```bash
git clone https://github.com/HetNagda20/Cancer-Nutrition-Analytics-Dashboard.git
cd Cancer-Nutrition-Analytics-Dashboard
npm install
```

### Running locally

```bash
npm start
```

Opens at `http://localhost:3000`

### Building for production

```bash
npm run build
```

### Deploying to GitHub Pages

```bash
npm run deploy
```

Live at: https://HetNagda20.github.io/Cancer-Nutrition-Analytics-Dashboard/

---

## Project Structure

```
src/
├── App.js                      # Data loading entry point
├── components/
│   ├── Dashboard.js            # Main layout and state management
│   ├── BeeswarmPlot.js         # BMI distribution chart
│   ├── UsChoropleth.js         # US map
│   ├── SankeyDiagram.js        # Flow diagram
│   ├── RadarChart.js           # Patient nutritional profile
│   ├── ParallelCoordinates.js  # Day 1 vs Day 2 nutrition
│   ├── DivergingBarChart.js    # State vs national comparison
│   ├── NeighboringStatesPlot.js# Regional cancer rate comparison
│   └── Statecomparison.js      # State score cards
└── styles/                     # Per-component CSS

public/
├── Complete_file_with_scores_and_states.csv  # Main patient dataset
└── state_level_scores_for_map.csv            # State-level aggregates
```

---

## Data

The dataset is derived from NHANES survey records with the following key fields:

| Field | Description |
|---|---|
| `DIET_SCORE_100` | Diet quality score (0–100) |
| `PA_SCORE_100` | Physical activity score (0–100) |
| `BMI_SCORE_100` | BMI score (0–100) |
| `CANCER_SCORE_100` | Cancer risk score (0–100) |
| `LIFESTYLE_SCORE_100` | Combined lifestyle score (0–100) |
| `synthetic_state_abbr` | Synthetically assigned U.S. state |
| `cancer_bin` | Binary cancer indicator (0/1) |

> Note: State assignments are synthetic and used for geographic visualization purposes only.

---

## License

MIT License — free to use and modify.

---

## Authors

Developed as part of CS529 — Visual Data Science coursework.

| Name | GitHub |
|---|---|
| Het Nagda | [HetNagda20](https://github.com/HetNagda20) |
| Madhura Dongare | [maddon22](https://github.com/maddon22) |
| Santhosh | [Santhosh1408](https://github.com/Santhosh1408) |