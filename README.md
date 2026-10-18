# Netwrok-Science-Enzyme-Network-Analysis
Undirected network representing an enzyme structural graph. Investigation the structure of this network and development an evidence‑based description of its organization. 

# Structure of an Enzyme Network: a chain of dense blocks

Network analysis of an enzyme structural graph (51 nodes, 110 undirected edges) for the course **Network Science (HS26)**, Master Data Science, UZH.

**[Live notebook with all outputs](https://aleexgort.github.io/Netwrok-Science-Enzyme-Network-Analysis/)** · [Notebook source](analysis.ipynb)

## What this project does

The network is investigated with measures chosen to answer specific questions: global connectivity, important nodes, degree structure, degree correlations, local clustering, communities, and comparison with random, small-world and scale-free models. Every comparison uses a stated null model, and all numbers are computed directly from `edgelist.txt`.

## Key findings

- **Elongated, connected network.** Diameter 12 and mean path 5.04, versus 5-6 and 2.80 in randomisations that keep every node's degree. Removing just the two edges 11-12 and 26-27 splits off a block of 16 nodes.
- **Brokers, not hubs.** Betweenness is highest for nodes 8, 25, 26, 36 and 27, which form a chain through the network. Different centrality measures pick different nodes.
- **No hubs.** Degrees lie between 2 and 6 (variance/mean = 0.27, Poisson would give about 1).
- **Local neighbourhoods.** Clustering is 0.238 against 0.061 in the degree-preserving null; edges between neighbourhoods close no triangles.
- **Four communities** (Louvain, Q = 0.625 against 0.41 in random networks) arranged in a row and linked by 6, 3 and 2 edges.
- **Neither random, small-world nor scale-free**; closest to a lattice-like chain of blocks. The network is almost one-dimensional (algebraic connectivity 0.048 versus 0.777 in the null model).

![Louvain communities](figures/fig_communities.png)
![Triangles and clustering](figures/fig_triangles.png)

## Repository contents

| File | Content |
|---|---|
| `analysis.ipynb` | Notebook with all code and executed outputs |
| `index.html` | The same notebook as a web page (GitHub Pages) |
| `network_report.pdf` | Two-page written report |
| `edgelist.txt` | Supplied network (each edge listed in both directions) |
| `figures/` | Figures produced by the notebook |
| `requirements.txt` | Python packages |

## Data

`edgelist.txt` has two columns of node identifiers per row. Every edge appears twice (`i j` and `j i`), so the undirected graph has 51 nodes and 110 edges, no self-loops and one connected component.

## Methods in brief

- Centralities: degree, betweenness, closeness, eigenvector, PageRank.
- Null models (200 samples, fixed seeds): degree-preserving randomisation (edge swaps) and the random graph G(n,m).
- Communities: Louvain (40 runs) with modularity Q compared against the null model.
- Reference models for the small-world question: ring lattice and Watts-Strogatz rewiring.

## Reproduce

```bash
git clone https://github.com/aleexgort/Netwrok-Science-Enzyme-Network-Analysis.git
cd Netwrok-Science-Enzyme-Network-Analysis
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab analysis.ipynb
```

Run all cells from top to bottom (about a few minutes because of the null models).

## Author

Alexandra Gort, Master Data Science, University of Zurich. Coursework for Network Science HS26.
