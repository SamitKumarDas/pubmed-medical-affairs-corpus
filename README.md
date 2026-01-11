# PubMed Medical Affairs 3-Layer Corpus (Topic 2 – MS Thesis)

## Overview
This repository contains a reproducible pipeline to construct a biomedical literature corpus from PubMed and a derived dataset used for MS thesis topic submission.

The corpus is designed to represent three Medical Affairs-relevant engagement layers:
- L1: Scientific engagement (mechanism, efficacy, biomarkers, RWE)
- L2: Safety and risk framing (AEs, tolerability, toxicity)
- L3: Comparative/critical discourse (head-to-head, limitations, unmet need)

## Data Source
Primary data source: PubMed (NCBI Entrez)
- PubMed: https://pubmed.ncbi.nlm.nih.gov/
- NCBI E-utilities documentation: https://www.ncbi.nlm.nih.gov/books/NBK25501/

## How the dataset was generated
The dataset was generated programmatically using the NCBI E-utilities API:
1. ESearch used to retrieve PubMed IDs for each layer query (with `usehistory=y`)
2. EFetch used to download titles + abstracts in batches
3. Records were tagged with a layer label (L1/L2/L3)
4. PMIDs were deduplicated across layers and saved to CSV

## Dataset
- The full derived dataset exceeds GitHub file size limits and is therefore hosted externally.
- Google drive link(full dataset) -> https://drive.google.com/file/d/1s4w0PXJPPkyd-RRtgHQWa9gjGJFRAugo/view?usp=drive_link
  Contains: PMID, title, abstract, year, journal, layer
- The dataset is derived from publicly available PubMed abstracts accessed via NCBI E-utilities.

## Reproducibility
To recreate the dataset:

```bash
pip install -r requirements.txt
python src/build_pubmed_corpus.py
