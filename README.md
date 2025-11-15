# Twitter Network Analysis — README

## 📌 Project Overview

This project is a **call for practice** where we explore and analyze a Twitter dataset using Python, Pandas, and NetworkX. The goal is to understand social graph structures, clean the data, and perform meaningful network analysis.

The dataset consists of:

* **Nodes file** (e.g., `nodes.csv`): information about Twitter users
* **Edges file** (e.g., `edges.csv`): follower/following relationships

We load, inspect, sample, clean, and analyze the data to build a working social graph.

---

## 📂 Dataset Structure

### **Nodes (users)**

The columns include:

* `id` — unique identifier
* `screenName` — Twitter handle
* `tags` — user metadata
* `avatar` — profile picture URL
* `followersCount`
* `friendsCount`
* `lang` — language
* `lastSeen`
* `tweetId`
* `friends`

### **Edges (relationships)**

The edges file contains:

* `source` — user ID
* `target` — user followed by source

---

## 🧪 Data Preparation & Sampling

We begin by:

* Loading the dataset with Pandas
* Inspecting shapes, types, and missing values
* Sampling 50 rows for quick testing
* Cleaning corrupted or malformed rows
* Ensuring IDs match between node and edge lists

Example:

```python
edges_df = pd.read_csv('edges.csv', names=["source", "target"])
sample_edges = edges_df.sample(50)
```

---

## 🧱 Building the Graph

Once cleaned, we load the edges into a NetworkX graph:

```python
G = nx.from_pandas_edgelist(sample_edges, source='source', target='target')
```

We then connect user attributes (from `nodes.csv`) to each node.

---

## 📊 Analysis Performed

The following metrics and analyses were implemented:

* Number of nodes & edges
* Degree distribution
* Connected components
* Clustering coefficients
* Centrality measures:

  * Degree
  * Closeness
  * Betweenness
* Detection of influential users
* Graph density & diameter (if connected)

---

## 📉 Visualization

We plot sample subgraphs using Matplotlib:

* Spring layout
* Circular layout
* Subgraph extraction of top-degree nodes

Optional filtering:

* Remove isolated nodes
* Only include users with +100 followers

---

## 🛠️ Additional Tools

We also experimented with:

* Removing special characters from comments
* Preprocessing for language detection
* Preparing inputs for later community detection

---

## ▶️ How to Run

```bash
python load_data.py
python analyze_graph.py
python visualize.py
```

Install dependencies:

```bash
pip install pandas networkx matplotlib
```

---

## 📖 Notes

This project’s purpose is educational, aimed at practicing:

* Data cleaning
* Graph analysis
* Manipulation of real-world noisy datasets

Feel free to extend it with community detection, sentiment analysis, or bot detection modules.
