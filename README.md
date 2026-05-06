# Wikipedia AI Editor Network Analysis

A social network analysis of collaborative editing behavior in the English Wikipedia Artificial Intelligence article cluster, 2018–2025.

**Author:** Arda Astam  
**Course:** Social Network Analysis  
**Department:** Computational Social Science, Koç University

---

## Project Overview

This project examines the social structure underlying knowledge production on Wikipedia by constructing and analyzing the co-editing network of contributors to the English Wikipedia Artificial Intelligence article cluster.

### Research Questions

1. Who are the central actors in the AI editor co-editing network?
2. How do editors organize into communities?
3. Does the network exhibit small-world properties?
4. How does the network respond to the removal of hub editors?
5. How has the network evolved between 2018 and 2025, particularly after ChatGPT's release in late 2022?

---

## Key Findings

- **Hub-dominated network:** Maxeto0910 and Jarble rank #1 and #2 across all four centrality metrics
- **No small-world structure:** Sigma = 0.21 indicates a core-periphery topology
- **High structural fragility:** Removing just Maxeto0910 fragments the network into 19 components
- **ChatGPT effect:** Editor count grew from 3,671 (2022) to 6,462 (2025)
- **Integration crisis:** 2025 cohort has 1/8 the average degree of the 2018 cohort

---

## Methodology

### Data Collection
- **Source:** MediaWiki REST API via mwclient
- **Category:** English Wikipedia "Artificial Intelligence"
- **Articles analyzed:** 186 (after filtering)
- **Total revisions:** 20,636
- **Time range:** 2018–2025

### Network Construction
- **Nodes:** Wikipedia editors
- **Edges:** Co-editing relationships (≥ 2 shared articles)
- **Final network:** 467 nodes, 3,705 edges

### Analysis Methods
- **Centrality:** Degree, Betweenness, PageRank, Closeness
- **Community detection:** Louvain algorithm
- **Small-world test:** Watts-Strogatz framework
- **Robustness test:** Sequential hub removal
- **Temporal analysis:** Annual cumulative snapshots
- **Cohort analysis:** New editor integration tracking

---

## Tools & Libraries

- `mwclient` — Wikipedia API client
- `networkx` — Network analysis
- `python-louvain` — Community detection
- `pyvis` — Interactive visualizations
- `pandas`, `numpy` — Data manipulation
- `matplotlib` — Static visualizations

---

## How to Reproduce

1. Clone this repository
2. Install dependencies: `pip install mwclient networkx python-louvain pyvis pandas numpy matplotlib`
3. Open `analysis.ipynb` in Jupyter Notebook or VS Code
4. Run all cells in order (data collection takes 5-10 minutes)

---

## Notes on Reproducibility

- **Data collection date:** January 2026
- **Random seed:** 42 (for Watts-Strogatz null model and spring layout)
- Wikipedia content changes continuously, so re-running the notebook may produce slightly different results.

---

## Limitations

- Sample limited to 186 articles in the main AI category
- Co-editing edges do not distinguish constructive collaboration from edit conflicts
- Bot detection relies on username heuristics
- Five large articles (>300 editors each) excluded to avoid noise

---

## Author

Arda Astam — Koç University, Computational Social Science Department
