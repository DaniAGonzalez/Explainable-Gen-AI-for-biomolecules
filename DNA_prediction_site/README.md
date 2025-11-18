# Transcription Factor Binding Prediction

Deep learning models to predict transcription factor-DNA binding with interpretability validation.

## Project Summary

Developed and validated CNN and CNN-Transformer architectures to predict where transcription factors bind to DNA sequences (200bp). Trained models on 10 different transcription factors, achieving AUC scores ranging from 0.76 to 0.98.

Key components:
- ConvModelV2: CNN with batch normalization and dropout
- ConvTransformerModel: Hybrid architecture with self-attention
- In silico saturation mutagenesis for motif validation
- Architecture ablation studies

## Results

Performance varies by transcription factor based on motif specificity:
- ATF2: 0.981 AUC (strong consensus motif)
- CTCF: 0.963 AUC (well-defined CCGC signature)
- ZNF24: 0.762 AUC (context-dependent binding)

Interpretability analysis confirmed models learn genuine biological motifs rather than dataset artifacts. Adding Transformers improved challenging factors by ~2.5%, suggesting long-range dependency modeling.

## Implementation

All code, analysis, and visualizations are contained in the Jupyter notebook. The notebook follows a structured workflow:

1. Data loading and exploration
2. Baseline model development
3. Interpretability analysis (mutagenesis, gradients)
4. Multi-factor training comparison
5. Architecture search with Transformers

**Dependencies**: PyTorch, NumPy, Pandas, Matplotlib, Scikit-learn

**Dataset**: ChIP-seq derived binding sites for 10 transcription factors (~2k-61k training sequences per factor, 200bp each)
