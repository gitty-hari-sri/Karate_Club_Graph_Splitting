# Karate_Club_Graph_Splitting
This project aims at using the concept of Spectral Bipartite Clustering in Graph Theory to detect the hidden communities in the real world data set of Karate_Club. It uses just math to predict social fault line that will occur in the future.

# The core-logic used
I have made use of nested functions to implement the community splitting. Which works like, first there is a function to check the modularity score,  then we come to the nested functions, inside a function call graph() I define many functions like find_s, matrix,..etc for implementing each step in the algorithm. Before each split, the modularity score is checked, and the spplitting takes place only if the current modularity score is greater than the previous one. And also by checking whether the leading eigen value is positive. For reference the change in modularity score after each split is mentioned. Then, after checking the condition,if true, we are splitting and getting 2 subgraphs G1, G2 which are again passed on to graph() function again. This process continues until the modularity score starts decreasing. We have also included trivial cases such as communities zero or very less nodes, that time we do median split.

# Advantage of using Nested Functions
For this specific problem, nested functions provide the perfect balance of organization,encapsulation and simplicity, while keeping the Newman algorithm self-contained and readable.

# Visualization
I have used line plot to visualize the evolution of all centrality measures over each splits, for all nodes. However, for simplicity only few nodes are shown.

# Observation and Short Discussion
* Across all community splits, nodes 0,1,33 and 22 consistently maintain high centrality positions. These nodes represent the key influencers in the karate club graph, with 0,33 showing the highest centrality positions indicating either of them is the INSTRUCTOR and the other is the ADMINISTRATOR
*  Degree Centrality Evolution:
   Nodes in the 5-node community [4,5,6,10,16] show significant degree centrality drops after the final split as they       become isolated from the broader network
   Between-community connectors (nodes 0, 1, 3) maintain high degree centrality by preserving connections across            community boundaries
* The community detection process reveals that centrality is not an inherent node property but emerges from network position relative to community boundaries.
* Betweenness Centrality redistributes over time. After each split the betweenness further concentrates of fewer and fewer nodes , leading to the 3 final communities.
* Closeness Centrality Patterns:
  Nodes in the 18-node community maintain higher closeness centrality due to their larger, more connected structure.
  Peripheral nodes in smaller communities experience closeness decreases as path distances increase.
* Clustering Coefficient Changes:
  Tight-knit groups like the 5-node community show increased clustering coefficients when isolated.
  Bridge nodes experience clustering decreases as they maintain connections across less-interconnected communities
