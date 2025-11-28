# 🧠 Network Analysis: Zachary’s Karate Club and Wikipedia Vote Network

This project explores two different networks using Python, NetworkX, igraph, the Louvain community detection method and visualization tools like Gephi. The goal was to understand how network structure behaves at different scales, how communities form and how to identify important nodes using graph metrics.

---

## 1️⃣ Zachary’s Karate Club Graph

I started with the Zachary Karate Club dataset because it is small and simple. It contains:

| Metric | Value |
|--------|-------|
| Nodes | 34 |
| Edges | 78 |
| Average Clustering Coefficient | **0.5706384782076823** |

This dataset helped me test loading a graph, computing clustering and visualizing it. Since it is tiny, metrics run instantly and results are easy to understand.

---

## 2️⃣ Wikipedia Vote Network

After that I worked with the wiki-Vote dataset from SNAP which is much larger and more realistic. It represents voting behavior in Wikipedia admin elections.

| Property | Value |
|----------|-------|
| Nodes | 7,115 |
| Edges | 100,762 |
| Graph Type | Directed (analyzed as undirected) |

Each edge indicates that one user voted for another user. This network is large enough to show real properties like hubs, long-tail degree distribution and community structure.

---

### 📌 Average Clustering Coefficient

0.1408978458938873


This value is lower than the Karate Club graph because this network is larger and less tightly interconnected. Still, it is higher than a random network which means users form local groups.

---

### 📌 Local Clustering Coefficient

Local clustering varies between nodes. A few sample values:

(30, 0.1573...)
(1412, 0.0492...)
(3352, 0.1184...)
(5254, 0.1855...)
(5534, 0.0431...)


Some nodes behave as tightly clustered members while others act as bridges.

---

### 📌 Degree Distribution

I plotted degree vs frequency. The plot showed a long tail meaning:

- Most nodes have very few connections  
- A small number of users have many connections  

This shape indicates a **power-law distribution**, which is common in social networks.


---

### 📌 Largest Connected Component

The entire graph is not fully connected so I worked with the largest connected component to compute distance-based metrics.

| Metric | Value |
|--------|-------|
| LCC Nodes | **2,524** |
| LCC Edges | **24,875** |

---

### 📌 Average Path Length

Computing this exactly is expensive so I used sampling.

Approx average path length: 4.326446928955568187


This small value suggests a **small-world effect** where most nodes are only a few hops apart.

---

### 📌 Community Detection (Louvain Algorithm)

To detect natural groups I applied the Louvain community detection method.

| Result | Value |
|--------|-------|
| Number of Communities | **30** |

These community clusters most likely reflect groups of users with similar voting behavior or shared interests.

---

### 📌 Centrality Measures

To identify influential or structurally important nodes I computed centrality values.

#### Top nodes by Degree Centrality:

(2565, 0.1497...)
(726, 0.1086...)
(1140, 0.1044...)


#### Top nodes by Betweenness Centrality:

(2565, 0.0740...)
(457, 0.0344...)
(1166, 0.0275...)


Nodes appearing in both lists are likely key actors in the network.

---

### 📌 Clustering Coefficient Distribution

I plotted the distribution of clustering coefficients. Most nodes have low clustering which suggests sparse global connectivity but small, close embedded groups.



---

### 📌 Graph Density and Assortativity

| Metric | Value |
|--------|-------|
| Graph Density | **0.003981420144693063** |
| Degree Assortativity | **−0.08305248270816032** |

The low density is expected for large graphs.  
The slightly negative assortativity means high-degree nodes tend to connect with low-degree nodes which resembles a hub-and-spoke structure.

---

## 🎨 Visualization in Gephi

To better understand overall structure I exported the graph to Gephi and used:

- **ForceAtlas2 layout**
- Node size scaled by degree
- Colors based on Louvain community detection

This produced a visual representation where clusters and hubs become obvious and easy to interpret.


---

## ✅ Summary

This project helped me understand how network metrics relate to behavior in real-world graphs. Starting from the Karate Club graph and moving to the wiki-Vote dataset showed how methods must change when working with larger networks.

- The Karate Club graph demonstrated basic analysis concepts  
- The Wikipedia Vote network revealed real scaling behavior, power-law structure, community formation and key influencer nodes  

This workflow can be extended to other datasets and used for social analytics, recommendation systems, anomaly detection and graph-based machine learning.



