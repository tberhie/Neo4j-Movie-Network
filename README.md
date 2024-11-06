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
```
**Purpose**: This query returns all movies directed by Rob Reiner, which is useful for understanding a director's influence in the dataset.

### 2. List All Co-actors of a Specific Actor
```cypher
MATCH (actor:Person {name: "Tom Hanks"})-[:ACTED_IN]->()<-[:ACTED_IN]-(coActor)
RETURN DISTINCT coActor.name AS CoActor
```
**Purpose**: This query finds actors who have acted alongside Tom Hanks, revealing collaboration patterns.
### 3. Find Movies and Actors Exactly 3 "Hops" Away from the Movie “Hoffa”
```cypher
MATCH (movie:Movie {title: "Hoffa"})-[*3]-(connectedNode)
WHERE NOT (movie)-[*1..2]-(connectedNode)
RETURN connectedNode
```
**Purpose**: This query identifies all nodes exactly three relationships away from "Hoffa," filtering out closer connections. This could highlight less obvious relationships within the network.

### 4. Find Actors Who Have Collaborated on More Than 3 Movies
```cypher
MATCH (a1:Person)-[:ACTED_IN]->(movie)<-[:ACTED_IN]-(a2:Person)
WHERE a1 <> a2
WITH a1, a2, COUNT(movie) AS collaborations
WHERE collaborations > 3
RETURN a1.name AS Actor1, a2.name AS Actor2, collaborations
ORDER BY collaborations DESC
```
**Purpose**: This query finds frequent collaborators, which could be useful for casting directors or analysts studying actor partnerships.

## Visualization Examples

<img width="851" alt="Screenshot 2024-11-06 at 11 38 26 AM" src="https://github.com/user-attachments/assets/4db93813-179d-418b-84d9-1b6bde87feab">

<img width="1028" alt="Screenshot 2024-11-06 at 11 23 22 AM" src="https://github.com/user-attachments/assets/f39d2502-d92b-46a0-9d7c-e54e8d3c56dc">




