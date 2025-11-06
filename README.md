# Karate Club Community Detection

**Made by Ayush Siddha**

This project analyzes Zachary's Karate Club network using spectral modularity partitioning to detect communities.

## Background

The Karate Club dataset is a classic social network from a study by Wayne Zachary in the 1970s. He observed 34 members of a university karate club and recorded their social interactions outside of classes. The club eventually split into two groups due to a dispute between the instructor and the administrator.

This is interesting because we can use network analysis to see if we can predict the split just from the friendship structure.

## What's in this repo

- `karate_club_community_detection.ipynb` - main notebook with all the code and analysis

## Method

I used **recursive spectral modularity partitioning** which works by:
1. Computing the modularity matrix B for the network
2. Finding the leading eigenvector of B
3. Splitting nodes based on the sign of eigenvector components
4. Repeating on each community until no split improves modularity

The algorithm stops when we can't find any split that gives a positive modularity gain (ΔQ > 0).

## What I analyzed

- How many communities the algorithm finds
- Visualizations showing the graph after each split (different colors for each community)
- Node centrality metrics:
  - Degree centrality
  - Betweenness centrality
  - Closeness centrality
  - Clustering coefficient
- How these metrics change as we recursively detect communities

## Key findings

- The algorithm finds multiple communities through recursive splitting
- Nodes 0 and 33 (the two leaders) consistently have the highest centrality
- Betweenness centrality changes the most across iterations - nodes that bridge communities lose importance when those communities are separated
- Degree centrality stays constant (it only depends on direct connections)
- The first split usually matches the actual historical split of the club

## Running the code

Just open `karate_club_community_detection.ipynb` in Jupyter and run all cells from top to bottom. You'll need:
- networkx
- numpy
- matplotlib
- pandas

## References

Newman, M. E. J. (2006). "Modularity and community structure in networks." PNAS 103(23):8577–8582.

Zachary, W. W. (1977). "An information flow model for conflict and fission in small groups." Journal of Anthropological Research 33(4):452–473.
