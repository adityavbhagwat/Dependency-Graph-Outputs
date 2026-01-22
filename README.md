# Dependency Graph Builder - Generated Outputs

This repository contains pre-generated dependency graphs for various OpenAPI specifications, created by the Dependency Graph Builder tool.

## Purpose

These dependency graphs are designed to support **automated API testing** by identifying the correct order in which API operations should be executed. For example, a `POST` (create) operation should be executed before `GET` (read) operations on the same resource.

## Contents

### Output Folders

Each `output_*` folder contains the generated dependency graph for an OpenAPI specification:

| Folder | API | Description |
|--------|-----|-------------|
| `output_petstore_fixed/` | Petstore | Classic pet store API example |
| `output_simple_api/` | Simple API | Basic CRUD example |
| `output_user/` | User API | User management endpoints |
| `output_market/` | Market API | Marketplace operations |
| `output_spotify/` | Spotify | Music streaming API |
| `output_person/` | Person API | Person CRUD operations |
| `output_project/` | Project API | Project management |
| `output_features/` | Features API | Feature flag management |
| `output_fdic/` | FDIC | Financial data API |
| `output_genome_nexus/` | Genome Nexus | Genomic data API |
| `output_rest_countries/` | REST Countries | Country information API |
| `output_language_tool/` | Language Tool | Grammar checking API |
| `output_ohsome/` | Ohsome | OpenStreetMap history API |
| `output_github/` | GitHub | GitHub REST API v3 |

### Files in Each Output Folder

| File | Format | Description |
|------|--------|-------------|
| `graph.json` | JSON | Complete graph data (nodes, edges, metadata) |
| `graph.dot` | GraphViz DOT | For visualization with Graphviz tools |
| `graph.graphml` | GraphML | Standard graph exchange format |
| `graph.html` | HTML | Interactive browser visualization |
| `graph_stats.json` | JSON | Graph statistics and metrics |
| `build_stats.txt` | Text | Build log with dependency summary |
| `annotated_spec.yaml` | YAML | Original spec with added annotations |

## Coverage Report

See [`coverage_report.txt`](coverage_report.txt) for a comprehensive analysis of graph quality across all APIs.

### Coverage Metrics Explained

| Metric | Description |
|--------|-------------|
| **Node Coverage** | % of API operations captured as graph nodes |
| **Connectivity Coverage** | % of operations that are connected in the graph |
| **Parameter Flow Coverage** | % of consumed parameters with producers connected |
| **CRUD Coverage** | % of expected CRUD relationships captured |
| **Semantic Correctness** | % of edges following correct ordering (POST→GET) |
| **Overall Score** | Weighted combination of all metrics (0-100) |

## How to Use

### View Interactive Graph
Open any `graph.html` file in a web browser for an interactive visualization.

### Use JSON Data
Load `graph.json` in your testing framework to get the execution order:

```python
import json

with open('output_petstore_fixed/graph.json') as f:
    graph = json.load(f)

# Get nodes (operations)
for node in graph['nodes']:
    print(f"{node['method']} {node['path']} - {node['id']}")

# Get edges (dependencies)
for edge in graph['edges']:
    print(f"{edge['source']} → {edge['target']} ({edge['type']})")
```

### Generate with Graphviz
```bash
dot -Tpng output_petstore_fixed/graph.dot -o petstore_graph.png
```

## Quality Summary

From the coverage analysis:

- **14 APIs analyzed**
- **1611 total operations** captured
- **50,526 dependencies** identified
- **Average quality score: 72.3/100**
- All graphs are valid DAGs (Directed Acyclic Graphs)

## License

These outputs are generated from publicly available OpenAPI specifications for research and testing purposes.

## Related

- Source code: [Dependency-Graph-Builder](https://github.com/aditya15intern/Dependency-Graph-Builder)
