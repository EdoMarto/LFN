## Learning From Networks Project: A Case of Study on an Airport Network

### CODE:
The code is divided into functions. 

Utility functions:
- ComputeGraph(): it's the main function that parse the dataset, call all other functions and set the visualization of the results;
- GraphDrawing(routes, graph): it allows us to visualize the network; 
- importRoutesDataFromJson(): it calls the API to download the routes data from the site;
- importAirportDataFromJson(): it calls the API to download the airports data from the site.  

Feature functions:
- DegreeCentrality(graph)
- ClosenessCentrality (graph)
- ApproximateClosenessCentrality(graph)
- BetweennessCentrality(graph)
- ApproximateBetweennessCentrality(graph)
- LocalClusteringCoefficent(graph)
- ApproximateLocalClusteringCoefficent(graph,k)
- SubGraphWithTopNodes(graph, centrality, n)

In each function there are some commented lines. They concern print or code that allow us to visualize in a better way the results (e.g. zoom of histogram). 
If necessary, they can be decommented.

### EXECUTION:
To execute the application, it's possible:
- Run the code from command prompt. You can enter in the file folder and execute the "phyton AirportNetwork.py" command.
- Run the code from python IDE.

### EUROPE OR WORLD:
The code is setted to analyse the European network. 
In order to consider the whole World graph, you can just uncomment the lines 33-34 and comment the 'for' loop in lines 28-30 (this loop select only airports in european countries).





