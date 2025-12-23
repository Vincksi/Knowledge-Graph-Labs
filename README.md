# Knowledge Graph Labs

A collection of hands-on labs exploring graph databases, machine learning on graphs, and AI-powered knowledge graph construction.

## Overview

This course covers the practical side of knowledge graphs—from querying graph databases to building intelligent systems that understand relationships in data. Each lab builds on fundamental concepts while introducing new tools and techniques.

## Labs

### Lab 1: Introduction to Neo4j
**What I learned:** Graph databases and the Cypher query language

Getting hands-on with **Neo4j**, a leading graph database. This lab focuses on:
- Understanding nodes, relationships, and properties
- Writing Cypher queries to explore graph data
- Analyzing Twitter data (users, tweets, mentions, retweets)
- Key operations: `MATCH`, `WHERE`, `MERGE` vs `CREATE`
- Real-world queries: finding influencers, analyzing tweet distributions, tracking retweets

**Why it matters:** Cypher is intuitive for querying relationships. This lab showed me that graphs naturally represent how real-world data is connected—much better than traditional tables for relational data.

### Lab 2: Machine Learning for Graphs
**What I learned:** How to use ML algorithms on graph structures

Moving beyond queries, this lab dives into machine learning techniques designed for graphs:
- **Graph embeddings** (learned representations of nodes)
- **Node classification** (predicting node types/properties)
- **Link prediction** (anticipating missing connections)
- Visualization and analysis of graph patterns
- Working with popular graph ML libraries

**Why it matters:** Not all data fits neatly into features. Graphs encode structure directly—this lab taught me how to leverage that structure for better predictions.

### Lab 3: Knowledge Graphs with Ollama
**What I learned:** Building knowledge graphs using local AI models

The final lab brings it all together with **Ollama**, enabling local LLM-based processing:
- Extracting entities and relationships from text
- Constructing knowledge graphs from unstructured data
- Using AI to understand and query information semantically
- No need for external APIs—everything runs locally

**Why it matters:** This bridges the gap between NLP and graph databases. Now I understand how modern systems like ChatGPT could be enhanced with a knowledge graph backend.

## How to Use This Repository

```
cd Knowledge-Graph-Labs
```

### Lab 1
- Open `Lab 1 - Introduction to Neo4j/cypher_queries.md`
- Contains 13 Cypher queries with explanations
- Run these against a Neo4j instance with the Twitter dataset

### Lab 2 & 3
- Jupyter notebooks with step-by-step code and visualizations
- Run cells sequentially to see results
- Includes data preprocessing, model training, and evaluation

## Prerequisites

- **Neo4j** (local instance or cloud)
- **Python 3.8+** with common ML libraries (scikit-learn, pandas, networkx)
- **Ollama** (for Lab 3—download from ollama.com)
- **Jupyter Notebook** to run .ipynb files

## Key Takeaways

1. **Graphs are everywhere** in data—not just for social networks but for recommendations, knowledge bases, and biology
2. **Cypher is elegant** for relationship queries that would be complex in SQL
3. **Structure matters in ML**—algorithms designed for graphs outperform traditional approaches
4. **Local AI is practical**—with Ollama, I can run sophisticated models without cloud dependence

## Personal Reflection

This course transformed how I think about data structure. Traditional databases treat data as isolated records; graphs treat it as an interconnected web. Once I started thinking in graphs, so many real-world problems became clearer. The progression from querying → learning → extracting mirrors how AI systems actually work.

---

*ESSEC Y3 - Knowledge Graphs & Databases*
