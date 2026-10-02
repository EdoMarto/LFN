# Airport Network Analysis (Learning From Networks)

A graph mining project for the *Learning From Networks* course (MSc Computer Engineering, University of
Padova). It builds the European air route network from live flight data and compares exact against
approximate algorithms for node centrality and clustering, looking at both how accurate they are and how
long they take.

## What it does

1. Downloads airports and routes from the [Travelpayouts data API](https://support.travelpayouts.com/hc/en-us/articles/203956163)
   and builds an undirected graph (airports are nodes, routes are edges), restricted to EU countries.
2. Finds the most central airports two ways: with exact algorithms (NetworkX) and with randomized
   approximations whose sample size comes from theoretical error bounds (ε, δ).

| Metric | Exact | Approximate |
|---|---|---|
| Degree centrality | yes | n/a |
| Closeness centrality | yes | Eppstein-Wang sampling (our own implementation) |
| Betweenness centrality | yes | Sampling with *k* derived from the graph diameter |
| Local clustering coefficient | yes | Randomized permutation-based estimator (our own implementation) |

3. Plots the network, the metric distributions, and the sub-graph of the top *n* airports for each
   metric.

## Running it

```bash
pip install -r requirements.txt
python AirportNetwork.py
```

It runs on the European network by default. To analyse the whole world, follow the comment in
`ComputeGraph()` and use all the airports instead of the EU filter. A few lines in each function are
commented out; uncomment them for extra prints and zoomed-in plots.

## Code structure

* `ComputeGraph()` is the entry point: it loads the data, builds the graph and runs every metric.
* `importAirportDataFromJson()` and `importRoutesDataFromJson()` download the data.
* `DegreeCentrality`, `ClosenessCentrality`, `ApproximateClosenessCentrality`, `BetweennessCentrality`,
  `ApproximateBetweennessCentrality`, `LocalClusteringCoefficent`, `ApproximateLocalClusteringCoefficent`
  are the metrics.
* `SubGraphWithTopNodes(graph, centrality, n)` and `GraphDrawing(routes, graph)` do the plotting.

## Built with

Python, NetworkX, pandas and Matplotlib.

## Authors

Edoardo Martorelli ([@EdoMarto](https://github.com/EdoMarto)),
[@FeVe98](https://github.com/FeVe98) and [@filo1110](https://github.com/filo1110).
