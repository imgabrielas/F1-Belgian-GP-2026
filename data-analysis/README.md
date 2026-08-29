# 🏎️ Project Overview

This project explores Formula 1 data using the **FastF1** Python library, combining exploratory data analysis and interactive visualisations to better understand race performance throughout the season.

The project follows the current Formula 1 calendar (2026).

## Repository Structure

* `F1_EDA.ipynb` — main exploratory data analysis notebook covering the season as a whole
* `monaco2026/` — race-weekend deep dive for the Monaco Grand Prix
  * `weekend_analysis.ipynb` — qualifying and race analysis for the weekend
  * `weekend_data/` — extracted qualifying, practice, and race CSVs for the weekend
  * `cache/` — local FastF1 cache (session data and HTTP cache)

## Objectives

* Collect and clean race data using FastF1
* Explore driver and constructor performance throughout the season
* Create interactive visualisations using Plotly

---

# Planned Analyses

## Championship Progression

* Driver championship points over the season
* Constructor championship standings
* Championship momentum after each race

## Driver Performance

* Average finishing position
* Qualifying vs race performance
* Positions gained and lost
* Podium finishes
* Fastest laps
* Driver consistency throughout the season

## Team Performance

* Constructor points
* Team race pace
* Reliability and DNF analysis
* Comparison of teammates
* Performance trends across the season

## Race Analysis

* Qualifying results
* Race results
* Grid position vs finishing position
* Circuit comparisons
* Performance at different track types

## Strategy Analysis

* Tyre compounds
* Stint lengths
* Pit stop strategies
* Undercut and overcut effectiveness
* Weather impact on race outcomes

## Interactive Visualisations

Examples include:

* Championship progression line charts
* Constructor comparison bar charts
* Heatmaps of finishing positions
* Scatter plots comparing qualifying and race performance
* Driver and team performance dashboards
* Interactive Plotly visualisations

> **Note:** Plotly charts currently don't render when viewing the notebooks directly on GitHub (reason unclear at this point) — open the notebooks locally (e.g. via Jupyter) to see them.

---

# Technologies

* Python
* FastF1
* Pandas
* NumPy
* Plotly
* Matplotlib

---

# Getting Started

1. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

2. Launch Jupyter and open a notebook:

   ```bash
   jupyter notebook F1_EDA.ipynb
   ```

FastF1 caches downloaded session data locally (see the `cache/` folders) to avoid re-fetching from the API on every run.

---

# Project Status

This project is currently under active development.

As each Formula 1 Grand Prix takes place, new data will be collected and analysed. The repository will continue to evolve throughout the season with additional analyses and visualisations.


lol