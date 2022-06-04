<img src="https://zenodo.org/api/files/00000000-0000-0000-0000-000000000000/incentive/logo.jpg" alt="incentive logo" width="300"/>

[![CI](https://github.com/fair-data-collective/M4M18-vocabulary/workflows/Sheet2RDF/badge.svg)](https://github.com/fair-data-collective/M4M18-vocabulary/actions?query=workflow%3ASheet2RDF)

# [INCENTIVE Variables Controlled Vocabulary](http://purl.org/incentive/variables/)
Controlled vocabularies allow an accurate and controlled approach in describing physical and digital assets (e.g., data). One of such controlled vocabulary is **INCENTIVE Variables**. This controlled vocabulary is a result of Metadata 4 Machine (M4M) Workshop 18 and 22 (M4M.18 and M4M.22) provided to [the INCENTIVE community](https://zenodo.org/communities/incentive/about/). 

`sheet2rdf` and `OntoStack`, developed by Nikola Vasiljevic, are used to build and serve **INCENTIVE Variable**, while [PURL](https://archive.org/services/purl/), which once configured, will be used to persist identifiers for the vocabulary terms and properties:

   http://purl.org/incentive/variables/


# Tooling
## [sheet2rdf](https://github.com/fair-data-collective/sheet2rdf)

This repository hosts automatic workflow, executed by means of Github actions, and underlying shell and python scripts which:

- [Fetches Google Sheet](https://docs.google.com/spreadsheets/d/1g6pfXRYA-4LjRj2ZS74jcs9R5vs5dOCoBdwAQW8opcY/edit#gid=1316280843), containing the taxonomy terms and their defitions, from Google Drive and stores is as `xlsx` and `csv` files
- Converts fetched sheet to machine-actionable and FAIR RDF vocabulary using [xls2rdf](https://github.com/sparna-git/xls2rdf)
- Tests the resulting RDF vocabulary using [qSKOS](https://github.com/cmader/qSKOS/)
- Commits conversion results and tests logs to this repository
- and deploy RDF vocabulary to OntoStack to be served to humans and machines

## [OntoStack](http://vocab.fairdatacollective.org)

OntoStack is a set of orchestrated micro-services configured and interfaced such that they can intake vocabularies and resolve their terms and RDF properties upon requests either by humans or machines.

Some of OntoStack micro-services are:

- [Jena Fuseki](https://jena.apache.org/documentation/fuseki2/) a graph database
- [SKOSMOS](http://www.skosmos.org/) a web-based SKOS browser acting as a front-end for the vocabularies persisted by the graph database
- [Træfik](https://doc.traefik.io/traefik/) an edge router responsible for proper serving of URL requests

**INCENTIVE Variables** is temporarly served by FAIR Data Collective instance of `OntoStack`:
http://vocab.fairdatacollective.org/
