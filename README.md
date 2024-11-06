# Neo4j-Movie-Network

# Movie Graph Database with Neo4j

## Project Overview
This project uses Neo4j to create and analyze a graph database centered around movies, actors, directors, and other key connections in the film industry. By modeling movie data as a graph, we can explore intricate relationships and answer questions about collaborations, genre patterns, and network connectivity in a dynamic way. This project demonstrates how Neo4j can effectively manage and query interconnected data.

## Project Files
- **MoviesDB.txt**: Contains the Cypher commands to create nodes and relationships for movies, actors, and directors.
- **example_queries.md**: A file with additional queries to explore and analyze the dataset.

## Getting Started

### Prerequisites
- **Neo4j Desktop**: Download and install [Neo4j Desktop](https://neo4j.com/download/).
- **Neo4j Browser**: Included in Neo4j Desktop for running Cypher queries and visualizing the graph.
- **Basic Knowledge of Cypher**: Neo4j’s query language, similar to SQL but tailored for graph data.

### Setup Instructions

1. **Create a New Project in Neo4j Desktop.**
2. **Create a New Database:**
   - Name your database (e.g., `MovieGraphDB`).
   - Start the database to initialize.
3. **Load the Dataset:**
   - Copy the Cypher commands from `MoviesDB.txt`.
   - Paste them into the Neo4j Browser and run the commands to create the nodes and relationships.

## Project Goals and Learning Objectives
This project demonstrates how to:

- Model data as a graph to reveal insights into relationships and collaborations.
- Use Neo4j's Cypher language to query and analyze graph data.
- Create complex queries that highlight network properties, like shortest paths, mutual collaborators, and genre analysis.

## Example Queries
Here are some example queries that showcase the capabilities of this graph database.

### 1. Find All Movies by a Specific Director
```cypher
MATCH (director:Person {name: "Rob Reiner"})-[:DIRECTED]->(movie)
RETURN movie.title AS Movie


