# Wikipedia AI Editor Network Analysis

Social network analysis project examining the co-editing network of Wikipedia editors who contributed to AI-related articles between 2018 and 2025.

**Arda Astam**, Koç University, Computational Social Science  
*Social Network Analysis course project, Spring 2026*


## What is this project about?

Wikipedia is one of the most consulted reference sources in the world, but the social dynamics behind its content are still not very well studied. This project takes a closer look at one specific corner of Wikipedia: the Artificial Intelligence article cluster.

The basic idea: when two editors work on the same article, they form a connection. By collecting the revision histories of 186 AI-related articles, I built a network of 467 editors and 3,705 connections. Then I analyzed it.

The motivation came from ChatGPT. After November 2022, AI became a mainstream topic almost overnight, and I wanted to see whether and how this changed the editorial community on Wikipedia.


## Research questions

The project tries to answer five questions:

1. Who are the most central editors in this network?
2. Do editors group into communities, and if so, how distinct are these groups?
3. Does the network show small-world properties (high clustering plus short paths)?
4. What happens to the network if hub editors leave?
5. How has the structure changed between 2018 and 2025, especially after ChatGPT?


## Main findings

A few things stood out:

* Two editors, **Maxeto0910** and **Jarble**, dominate the network. They rank first and second on all four centrality metrics I used.
* The network is *not* small-world. Sigma came out to 0.21, which is much lower than 1. This indicates a core-periphery structure rather than the typical small-world pattern.
* Removing just Maxeto0910 fragments the network into 19 disconnected pieces. Removing the top 6 hubs creates 52 pieces. Pretty fragile.
* The number of editors grew sharply after 2022 (from 3,671 to 6,462 by 2025), but new editors aren't really integrating. The 2025 cohort has roughly 1/8 the average connectivity of the 2018 cohort.


## Data and method

Data was collected via the MediaWiki REST API using the `mwclient` Python library. I filtered out bots (221 accounts removed), excluded revisions outside 2018-2025, and skipped 5 articles that had over 300 editors each (these were too crowded to represent real collaboration). The final dataset has 20,636 revisions.

Network construction:

* Each editor is a node
* An edge means two editors edited at least 2 articles in common
* Edge weight equals the number of shared articles

For analysis I used `networkx` and `python-louvain`. The methods cover:

* Four centrality measures (degree, betweenness, PageRank, closeness)
* Louvain community detection
* Watts-Strogatz small-world test
* A robustness test that removes hubs one by one
* Yearly snapshots and editor cohort analysis
