# Airport Network Analysis – Learning From Networks

Graph-mining project for the *Learning From Networks* course (MSc Computer Engineering, University of Padova).
It builds the European air-route network from live flight data and compares **exact vs. approximate
algorithms** for node centrality and clustering, measuring both accuracy and running time.

## What it does
1. Downloads airports and routes from the [Travelpayouts data API](https://support.travelpayouts.com/hc/en-us/articles/203956163)
   and builds an undirected graph (airports = nodes, routes = edges) restricted to EU countries.
2. Computes the most central airports with exact algorithms (NetworkX) and with randomized approximations
   whose sample size is derived from theoretical error bounds (ε, δ):

| Metric | Exact | Approximate |
|---|---|---|
| Degree centrality | ✔ | – |
| Closeness centrality | ✔ | Eppstein–Wang sampling (own implementation) |
| Betweenness centrality | ✔ | Sampling with *k* derived from the graph diameter |
| Local clustering coefficient | ✔ | Randomized permutation-based estimator (own implementation) |

3. Plots the network, the metric distributions and the sub-graph of the top-*n* airports for each metric.

## Running it
```bash
pip install -r requirements.txt
python AirportNetwork.py
```
The analysis runs on the European network by default. To analyse the whole world, follow the comment in
`ComputeGraph()` and use all airports instead of the EU filter.

Some lines in each function are commented out; uncomment them for extra prints and zoomed plots.

## Code structure
- `ComputeGraph()`: entry point; loads data, builds the graph, runs every metric.
- `importAirportDataFromJson()`, `importRoutesDataFromJson()`: data download.
- `DegreeCentrality`, `ClosenessCentrality`, `ApproximateClosenessCentrality`, `BetweennessCentrality`,
  `ApproximateBetweennessCentrality`, `LocalClusteringCoefficent`, `ApproximateLocalClusteringCoefficent`: metrics.
- `SubGraphWithTopNodes(graph, centrality, n)`, `GraphDrawing(routes, graph)`: visualisation.

## Tech stack
Python · NetworkX · pandas · Matplotlib

## Authors
Edoardo Martorelli ([@EdoMarto](https://github.com/EdoMarto)) ·
[@FeVe98](https://github.com/FeVe98) · [@filo1110](https://github.com/filo1110)
