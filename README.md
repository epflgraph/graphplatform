<img src="assets/icon-9ed65a81.png" alt="Project logo" height="64">

[![License](https://img.shields.io/github/license/epflgraph/graphproject)](https://github.com/epflgraph/graphproject/blob/master/LICENSE)
[![Latest Release on Github](https://img.shields.io/github/v/release/epflgraph/graphproject?sort=semver)](https://github.com/epflgraph/graphproject/releases/latest)
[![GitHub Stars](https://img.shields.io/github/stars/epflgraph/graphproject?style=social)](https://github.com/epflgraph/graphproject/stargazers)
[![Contributors](https://img.shields.io/github/contributors/epflgraph/graphproject)](https://github.com/epflgraph/graphproject/graphs/contributors)
[![Last Commit](https://img.shields.io/github/last-commit/epflgraph/graphproject)](https://github.com/epflgraph/graphproject/commits/master)
[![Open Issues](https://img.shields.io/github/issues/epflgraph/graphproject)](https://github.com/epflgraph/graphproject/issues)
[![Open PRs](https://img.shields.io/github/issues-pr/epflgraph/graphproject)](https://github.com/epflgraph/graphproject/pulls)
=

🏠 Project Home

**List of core services:**<br/>
[Registry](https://github.com/epflgraph/graphregistry) |
[AI](https://github.com/epflgraph/graphai) |
[Ontology](https://github.com/epflgraph/graphontology) |
[Search](https://github.com/epflgraph/graphsearch_ui) |
[Chat](https://github.com/epflgraph/graphchatbot)

**List of utilities:**<br/>
[Dash](https://github.com/epflgraph/graphdashboard) |
[DB client](https://github.com/epflgraph/graphdb-client) |
[ES client](https://github.com/epflgraph/graphes-client) |
[SDK](https://github.com/epflgraph/graph-sdk) |
[Agents](https://github.com/epflgraph/graphagents)


<br />

Project Overview
================
The **Graph Platform**, developed by the AI Engineering team at the [Center for Digital Education](https://www.epfl.ch/education/educational-initiatives/cede/) at EPFL (Swiss Federal Institute of Technology Lausanne), is an open-source **data intelligence platform** for education and research.

The platform uses semantic analysis and graph-based algorithms to federate, enrich, and interconnect academic content and entities, such as courses, lectures, exercises, publications, and other educational and research resources, into a unified **knowledge graph**.

On top of the platform, the [GraphSearch](https://graphsearch.epfl.ch/en) app provides a fast and intuitive interface for searching and discovering the knowledge graph. It also enables conversational access to indexed resources through an LLM-powered [chatbot](https://graphsearch.epfl.ch/en/chatbot).

Core Services
=============

The Graph Platform is composed of five core services that communicate or interact with one another. Each service is fairly self-contained, and can be deployed on separate machines with different hardware capabilities.

📚 [Graph Registry](https://github.com/epflgraph/graphregistry): The first layer in the Graph Platform. It ingests data in JSON format through an ETL pipeline, and generates a knowledge graph that feeds the GraphSearch and GraphChat applications. Data can be added to the registry through direct JSON file imports, or through a REST API.

🤖 [Graph AI](https://github.com/epflgraph/graphai): The semantic analysis engine that provides functionalities such as video segmentation, OCR, audio transcription, translation, embeddings, RAG construction, and ontological concepts detection.

🌲 [Graph Ontology](https://github.com/epflgraph/graphontology): A semantic graph of academically relevant concepts built from Wikipedia data. The network of concepts - over 1 million in size - is algorithmically clustered into naturally occuring categories with minimal human intervention.

🔎 [Graph Search](https://github.com/epflgraph/graphsearch_ui): A lightning fast search and recommendation engine sitting on top of the Graph Registry service. It is a web interface that enables users to navigate, explore, and discover the knowledge graph and the academic resources it indexes.

💬 [Graph Chat](https://github.com/epflgraph/graphchatbot): An LLM-based chatbot that leverages the knowledge graph to support and enrich answers to user prompts. It uses retrieval-augmented generation (RAG) techniques to provide relevant resources idexed by the knowledge graph, essentially providing natural language based navigation and discovery of the institution's academic content.

### Data infrastructure

In addition to these core services, the Graph Platform requires at least one relational database server like MySQL or MariaDB, and an indexing engine like ElasticSearch or OpenSearch.

It is recommended to have two active deployments of each. One for a core services / test environment, and one for a production environment serving GraphSearch.

To facilitate management and transfer of data across these services, we provide the following utilities:

🐳 [DB client](https://github.com/epflgraph/graphdb-client): A self-contained MySQL/MariaDB client with its own CLI. <br />
⚡️ [ES client](https://github.com/epflgraph/graphes-client): A self-contained ElasticSearch client with its own CLI.

Both clients are deployable by local Python-based installation or through Docker.

<img src="assets/Graph_ecosystem.png" alt="Graph Platform service interaction" style="border: 1px solid #8b8b8b;">

> **Figure:** Core services of the Graph Platform and their respective interactions.

<br />

Platform Deployment
===================

The core services should ideally be deployed on different machines with varying harware capabilities, in order to optimize for each use case. The recomended minimal specifications are shown in the table bellow.

| Service | CPU Cores | RAM      | Hard Drive |
|---------|-----------|----------|------------|
| ElasticSearch  | 4  | 8 GB  | 200 GB |
| MySQL/MariaDB  | 4  | 8 GB  | 2 TB   |
| Graph Registry | 4  | 4 GB  | 100 GB |
| Graph AI       | 16 | 32 GB | 100 GB |
| Graph Search   | 4  | 8 GB  | 50 GB  |
| Graph Chat     | 4  | 4 GB  | 50 GB  |

> **Table:** Minimal recommended hardware specifications for the Graph Platform core services.

The Graph AI service in particular will further benefit from the use of GPUs such as the Nvidia A100. This is because endpoints that perform voice transcription, text translation, and embeddings make use of models that are optimised for, and execute much faster in GPUs.

The Graph Ontology does not require its own machine. It is composed of two static datasets; one SQL-based, hosted on MySQL/MariaDB (80 GB), and the other index-based, hosted on ElasticSearch (35 GB).

Deployment Instructions
=======================
For detailed instructions on how to deploy the Graph Platform core services, you may consult the dedicated repository pages linked above.
