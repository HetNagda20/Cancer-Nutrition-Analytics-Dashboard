# Cancer Nutrition Analytics Dashboard

An interactive data visualization platform that connects diet, physical activity, and BMI to cancer outcomes across the U.S. population, built with React and D3.js for **UI Health** as a client engagement through UIC's CS529 (Visual Data Science) program.

🔗 **Live demo:** https://hetnagda20.github.io/Cancer-Nutrition-Analytics-Dashboard/
📊 **Dataset:** NHANES (National Health and Nutrition Examination Survey)

---

## Overview

UI Health needed a way to explore how nutrition and lifestyle factors relate to cancer risk across different populations and regions, without requiring stakeholders to dig through raw survey data themselves. This dashboard turns NHANES records into seven linked, interactive visualizations so a clinician, researcher, or analyst can go from a national-level pattern down to an individual patient's nutrition profile in a few clicks.

Every chart on the dashboard is cross-filtered: clicking a state on the map, a node in the Sankey diagram, or a dot in the beeswarm plot updates every other view to match.

---

## Key Features

- **BMI Beeswarm Plot**: every patient plotted individually, color-coded by cancer status and weight category. Click a patient to drill into their full profile.
- **U.S. Choropleth Map**: average lifestyle score by state; click a state to filter the entire dashboard down to that population.
- **Sankey Flow Diagram**: traces patients from fiber intake to sugar intake to BMI category, showing how dietary patterns funnel into weight outcomes.
- **Radar Chart**: a selected patient's nutritional profile plotted against national averages across five dimensions.
- **Parallel Coordinates**: Day 1 vs. Day 2 dietary intake for a patient across five tracked nutrients.
- **Diverging Bar Chart**: how a selected state's health scores deviate from the national average.
- **Neighboring States Plot**: cancer rate comparisons across geographically adjacent states, surfacing regional clusters.

**Filtering:** age range, BMI range, gender, patient ID search, state selection, and Sankey node/link selection, all of it synchronized across views via shared state in the dashboard layout component.

---

## The Data

- **724 patient-level records** from NHANES, each carrying ~30 raw survey fields (demographics, two-day dietary recall, physical activity, alcohol use, BMI) collapsed into five normalized 0 to 100 scores: diet, physical activity, BMI, cancer risk, and a combined lifestyle score.
- **54 state/territory-level aggregates** used to drive the choropleth and diverging bar views.
- State assignment is **synthetic**: NHANES doesn't release real geography at this resolution, so states were randomly assigned to enable geographic exploration. This is called out directly in the UI so it's never mistaken for real patient geography.

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI Framework | React 18 |
| Visualization | D3.js v7 |
| Flow Diagram | d3-sankey |
| Map Topology | TopoJSON / us-atlas |
| Styling | Custom CSS, dark theme |
| Fonts | DM Sans, DM Mono |
| Deployment | GitHub Pages (gh-pages) |

---

## Architecture

```
src/
├── App.js                       # Loads & parses both CSVs on mount
├── components/
│   ├── Dashboard.js             # Shared filter state, lays out all 7 charts
│   ├── BeeswarmPlot.js
│   ├── UsChoropleth.js
│   ├── SankeyDiagram.js
│   ├── RadarChart.js
│   ├── ParallelCoordinates.js
│   ├── DivergingBarChart.js
│   ├── NeighboringStatesPlot.js
│   └── Statecomparison.js       # State score cards
└── styles/                      # Per-component CSS (dark theme)

public/
├── Complete_file_with_scores_and_states.csv   # Patient-level dataset
└── state_level_scores_for_map.csv             # State-level aggregates
```

All charts read from a single shared filter state owned by `Dashboard.js`. There's no separate state management library; cross-filtering is handled with React state and D3 selections directly, which kept the data flow easy to reason about for a 7-chart dashboard at this scale.

---

## Getting Started

**Prerequisites:** Node.js v16+ and npm

```bash
git clone https://github.com/HetNagda20/Cancer-Nutrition-Analytics-Dashboard.git
cd Cancer-Nutrition-Analytics-Dashboard
npm install
npm start
```

App runs at `http://localhost:3000`.

**Build for production:**
```bash
npm run build
```

**Deploy to GitHub Pages:**
```bash
npm run deploy
```

---

## Why This Project

This was built as a real client engagement rather than a synthetic course exercise. The requirements, scope, and target audience came from UI Health, which meant making design calls (what's worth visualizing, how much filtering is too much, what a non-technical clinician needs vs. what a data analyst needs) rather than just satisfying a rubric. The dark theme redesign and the cross-filtering model across all seven charts were the parts I owned most directly.

---

## Team

| Name | GitHub |
|---|---|
| Het Nagda | [HetNagda20](https://github.com/HetNagda20) |
| Madhura Dongare | [maddon22](https://github.com/maddon22) |
| Santhosh | [Santhosh1408](https://github.com/Santhosh1408) |

Built for CS529, Visual Data Science, University of Illinois Chicago, in partnership with UI Health. Data sourced from the publicly available NHANES survey.cd Cancer-Nutrition-Analytics-Dashboard
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
