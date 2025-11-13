# Protein Function Prediction using ESM-2 Embeddings

Predicting Gene Ontology molecular functions from protein sequences using transfer learning with ESM-2 protein language model.

## Overview

This project demonstrates accurate functional annotation of proteins directly from amino acid sequences, bypassing traditional homology-based methods. Using ESM-2 embeddings as features, we trained a multi-label classifier to predict 202 molecular function terms across 8,704 human proteins.

## Results

- **8x improvement** over random baselines (mean PR-AUC: 0.123 vs 0.016)
- **98.57% test accuracy** across 1,741 proteins
- **Exceptional performance** on conserved families:
  - Olfactory receptors: PR-AUC 0.996
  - GPCRs: PR-AUC 0.991  
  - Protein kinases: PR-AUC 0.892

##  Dataset

- **8,704 human proteins** (length ≤500 aa) from UniProt
- **202 GO molecular function terms** (≥50 examples each)
- **Split:** 60% train / 20% validation / 20% test
- **Sources:** Gene Ontology Consortium + UniProt Human Proteome

## Method

1. **Feature extraction:** ESM-2 (150M parameters) generates 640D embeddings per protein
2. **Classifier:** 2-layer feed-forward network with batch normalization
3. **Multi-label:** Sigmoid outputs for independent function predictions
4. **Training:** Binary cross-entropy loss with early stopping

## Quick Start
```bash
# Install dependencies
pip install torch transformers biopython scikit-learn pandas matplotlib seaborn

# Download data
wget http://current.geneontology.org/annotations/goa_human.gaf.gz
# Download UniProt human proteome FASTA from https://www.uniprot.org/proteomes/UP000005640

# Run notebook
jupyter notebook notebook.ipynb
```


## Key Findings

- Performance strongly correlates with training data availability (functions with >50 examples achieve PR-AUC >0.5)
- Proteins with conserved sequence motifs (receptors, kinases, DNA-binding domains) are most predictable
- ESM-2 learned biologically meaningful representations without explicit structural supervision
- Multi-label classification handles average 3-6 functions per protein

## Tech Stack

Python | PyTorch | Transformers | ESM-2 | Scikit-learn | BioPython

## Citation

Data sources:
- ESM-2: Meta AI (facebook/esm2_t30_150M_UR50D)
- GO Annotations: Gene Ontology Consortium
- Sequences: UniProt Human Proteome (UP000005640)

---

**Author:** Dr. Daniela Gonzalez  
**Year:** 2025
