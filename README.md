# 🧬 Single-Cell RNA-seq Analysis of Diabetic Kidney Disease
### A Complete End-to-End Python/Scanpy Portfolio | GSE279086

<div align="center">

![Python](https://img.shields.io/badge/Python-3.12.1-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Scanpy](https://img.shields.io/badge/Scanpy-1.12.1-00ADD8?style=for-the-badge)
![CellTypist](https://img.shields.io/badge/CellTypist-1.7.1-FF6B6B?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)
![Dataset](https://img.shields.io/badge/GEO-GSE279086-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

**40 kidney biopsies · 29,287 cells · 18 cell types · 9,545 DEGs · 5,400+ pathways**

*From raw FASTQ metadata to biological insight — entirely in Python*

</div>

---

## 👤 About This Project

This repository demonstrates my ability to independently design, implement, and interpret a **production-grade single-cell RNA-seq analysis pipeline** from scratch using Python. Every decision — from QC thresholds to pathway databases — is scientifically justified and reproducible.

> **This is not a tutorial follow-along. This is original analysis of a real clinical dataset answering a real biological question.**

**Scientific Question:**
> *How do individual kidney cell types transcriptionally respond to early Type 1 Diabetes — and which signaling pathways drive these changes?*

---

## 🎯 What This Portfolio Demonstrates

| Skill | Evidence |
|---|---|
| **End-to-end scRNA-seq** | 6-script pipeline from raw GEO data to pathway biology |
| **Python/Scanpy proficiency** | Complete workflow without R — industry standard tooling |
| **Batch correction** | Harmony integration across 40 samples |
| **Automated cell annotation** | CellTypist with kidney-specific reference model |
| **Multi-method pathway analysis** | ORA + GSEA + PROGENy decoupler — three complementary approaches |
| **Biological interpretation** | Clinical-grade insights report with therapeutic implications |
| **Reproducibility** | Documented environment, version-controlled code, cached outputs |
| **Data visualization** | 17 publication-quality figures across all analysis steps |

---

## 📊 Key Results at a Glance

<table>
<tr>
<td align="center"><b>29,287</b><br>High-quality cells</td>
<td align="center"><b>18</b><br>Cell types identified</td>
<td align="center"><b>9,545</b><br>Significant DEGs</td>
<td align="center"><b>5,400+</b><br>Enriched pathways</td>
</tr>
<tr>
<td align="center"><b>40</b><br>Kidney biopsies</td>
<td align="center"><b>21</b><br>Leiden clusters</td>
<td align="center"><b>3</b><br>Pathway databases</td>
<td align="center"><b>0.904</b><br>Mean annotation confidence</td>
</tr>
</table>

### 🔬 Top Biological Findings
- **JAK-STAT pathway** strongly activated in endothelial and immune cells → chronic vascular inflammation
- **Global translational stress** across all major tubular cell types → integrated stress response
- **Mitochondrial dysfunction** in descending thin limb → PI3K survival signaling loss
- **Podocyte depletion** in T1D samples → early glomerulosclerosis
- **Innate immune dominance** over adaptive immunity in early DKD

> 📄 Full biological insights report: **[RESULTS.md](./RESULTS.md)**

---

## 🗂️ Dataset

| Field | Details |
|---|---|
| **GEO Accession** | [GSE279086](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE279086) |
| **Technology** | 10x Genomics 3' scRNA-seq |
| **Tissue** | Human kidney cortex biopsies |
| **Samples** | 40 total — 28 Type 1 Diabetes, 12 Lean Control |
| **Organism** | *Homo sapiens* |
| **Focus** | Early transcriptional changes in diabetic kidney disease |

---

## 🔄 Analysis Pipeline

```
Raw GEO Data (GSE279086)
        │
        ▼
┌─────────────────────┐
│  01_GEO_download    │  ← Automated download of 40 samples from NCBI GEO
│                     │    GEOparse · FTP retrieval · manifest generation
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  02_load_qc         │  ← Per-sample QC · 406,365 → 29,287 cells (92.8% filtered)
│                     │    MT% · gene count · UMI · ribosomal filtering
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  03_normalize       │  ← Normalization · HVG selection · PCA · Harmony
│  _pca_umap          │    Batch correction across 40 samples · UMAP · Leiden
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  04_celltypist      │  ← Automated annotation · Adult Human Kidney model
│                     │    18 cell types · confidence score 0.904
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  05_DEG             │  ← Wilcoxon DEG · per cell type · T1D vs Control
│                     │    9,545 significant DEGs across 16 cell types
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  06_pathway         │  ← ORA · GSEA · PROGENy decoupler
│  _enrichment        │    GO · KEGG · Reactome · MSigDB · 5,400+ pathways
└─────────────────────┘
```

---

## 📁 Repository Structure

```
scRNAseq-kidney-diabetes-GSE279086-scanpy/
│
├── 📓 notebooks/
│   ├── 01_GEO_download.ipynb          # GEO data retrieval & sample manifest
│   ├── 02_load_qc.ipynb               # QC filtering & visualization
│   ├── 03_normalize_pca_umap.ipynb    # Normalization, HVGs, PCA, Harmony, UMAP
│   ├── 04_celltypist.ipynb            # CellTypist cell type annotation
│   ├── 05_DEG.ipynb                   # Wilcoxon differential expression
│   └── 06_pathway_enrichment.ipynb   # ORA, GSEA, PROGENy pathway analysis
│
├── 📊 figures/
│   ├── 02_qc/                         # Pre & post QC violin plots (8 figures)
│   ├── 03_processing/                 # HVG, PCA elbow, UMAP plots (4 figures)
│   ├── 04_annotation/                 # Cell type UMAP with confidence scores
│   ├── 05_DEG/                        # Volcano plots for top 6 cell types
│   └── 06_pathways/                   # ORA, GSEA, PROGENy, combined insights
│
├── 📂 output/
│   ├── sample_manifest.csv            # 40 sample metadata
│   ├── DEG_summary_table.csv          # DEG counts per cell type
│   ├── DEG_master_table.csv           # All 658,818 tested gene-cell combinations
│   └── pathways/
│       ├── ORA/                       # Per cell type ORA results (13 CSVs)
│       ├── GSEA/                      # Per cell type GSEA results (18 CSVs)
│       ├── PROGENy_scores.csv         # Pathway activity scores per pseudobulk
│       └── PROGENy_pvals.csv          # Pathway activity p-values
│
├── 📄 RESULTS.md                      # Integrated biological insights report
├── 📄 README.md                       # This file
├── 📄 requirements.txt                # Python environment specification
└── 🧬 Adult_Human_Kidney.pkl          # CellTypist kidney reference model
```

---

## 🔬 Detailed Workflow

### 01 — GEO Download
Automated retrieval of all 40 samples from NCBI GEO using GEOparse. Each sample's three 10X Genomics files (barcodes, features, matrix) are downloaded and renamed to standard format. A complete sample manifest mapping GSM IDs to disease conditions is generated.

**Output:** 40 sample folders · `output/sample_manifest.csv`

---

### 02 — Quality Control
Per-sample QC metrics calculated and filtered using fixed thresholds consistent with published kidney scRNA-seq workflows.

| Metric | Threshold | Biological Rationale |
|---|---|---|
| Genes detected | 200 – 7,000 | Remove empty droplets & doublets |
| UMI counts | 500 – 50,000 | Remove poor capture & doublets |
| Mitochondrial % | < 20% | Remove dying/stressed cells |
| Ribosomal % | < 50% | Remove low-information cells |

**Result:** 406,365 → **29,287 cells** retained (7.2%)

> The aggressive filtering reflects the dataset's biology — kidney tissue dissociation releases high ambient RNA and metabolically active tubular cells have naturally elevated mitochondrial content.

---

### 03 — Normalization, Dimensionality Reduction & Batch Correction

| Step | Method | Parameters |
|---|---|---|
| Normalization | Log1p (CP10K) | target_sum = 10,000 |
| HVG selection | Seurat flavor | n_top_genes = 2,000 |
| Scaling | StandardScaler | max_value = 10, HVGs only |
| PCA | Truncated SVD | 50 components |
| Batch correction | **Harmony** | 40 samples, converged in **9 iterations** |
| Neighbor graph | kNN | n_neighbors = 30, 30 Harmony PCs |
| UMAP | McInnes et al. | min_dist = 0.3 |
| Clustering | **Leiden** | resolution = 0.5 → **21 clusters** |

**Key result:** Harmony successfully mixed all 40 samples — cells cluster by biology, not by batch.

---

### 04 — Cell Type Annotation
Automated annotation using **CellTypist** with the Adult Human Kidney reference model (v1, 41 cell types). Majority voting assigns cell type labels at the Leiden cluster level for robust, consistent annotation.

- **9,728 genes** matched between dataset and model
- **18 of 41 possible cell types** identified
- **Mean confidence score: 0.904** ✅

---

### 05 — Differential Expression
Wilcoxon rank-sum test applied per cell type comparing T1D vs Lean Control cells. This non-parametric approach handles the zero-inflated, sparse nature of scRNA-seq data without normality assumptions.

- **16 cell types** with at least one significant DEG
- **9,545 total significant DEGs** (FDR < 0.05, |log2FC| > 0.25)
- **C-TAL most affected:** 3,704 DEGs (92% upregulated)
- **PC most downregulated:** 83% of 1,157 DEGs downregulated

---

### 06 — Pathway Enrichment
Three complementary pathway analysis approaches applied:

**ORA (Over-Representation Analysis)**
- Databases: GO Biological Process 2023, KEGG 2021, Reactome 2022
- Method: Hypergeometric test on upregulated DEGs per cell type
- Result: **3,524 significant pathways** across 13 cell types

**Pre-Ranked GSEA**
- Databases: MSigDB Hallmarks 2020, Reactome 2022
- Ranking: Signed -log10(p-value) × direction
- Result: **1,891 significant pathways** (FDR < 0.25) across 17 cell types

**PROGENy via decoupler**
- Method: Multivariate Linear Model (MLM) on pseudobulk data
- Pathways: 14 core cancer/disease-relevant pathways
- Result: JAK-STAT most consistently activated across vascular and immune cells

---

## ⚙️ Installation & Reproduction

### Prerequisites
- Python 3.12+
- GitHub Codespaces or Linux environment
- ~20GB disk space
- 16GB RAM minimum (32GB recommended)

### 1. Clone the Repository
```bash
git clone https://github.com/mimakbio-cpu/scRNAseq-kidney-diabetes-GSE279086-scanpy.git
cd scRNAseq-kidney-diabetes-GSE279086-scanpy
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Pipeline
```bash
jupyter nbconvert --to notebook --execute notebooks/01_GEO_download.ipynb
jupyter nbconvert --to notebook --execute notebooks/02_load_qc.ipynb
jupyter nbconvert --to notebook --execute notebooks/03_normalize_pca_umap.ipynb
jupyter nbconvert --to notebook --execute notebooks/04_celltypist.ipynb
jupyter nbconvert --to notebook --execute notebooks/05_DEG.ipynb
jupyter nbconvert --to notebook --execute notebooks/06_pathway_enrichment.ipynb
```

### Expected Runtime
| Step | Runtime |
|---|---|
| Data download | 20–40 minutes |
| QC & merging | 5–10 minutes |
| Normalization, PCA, UMAP | 10–15 minutes |
| CellTypist annotation | 5 minutes |
| DEG analysis | 15–20 minutes |
| Pathway enrichment | 30–45 minutes |
| **Total** | **~2 hours** |

---

## 🧰 Tools & Versions

| Tool | Version | Purpose |
|---|---|---|
| Python | 3.12.1 | Core language |
| scanpy | 1.12.1 | scRNA-seq analysis |
| anndata | 0.12.14 | Data structure |
| harmonypy | latest | Batch correction |
| celltypist | 1.7.1 | Cell type annotation |
| leidenalg | latest | Graph clustering |
| gseapy | 1.2.1 | ORA & GSEA |
| decoupler | 2.1.6 | Pathway activity scoring |
| GEOparse | latest | GEO data retrieval |
| matplotlib | latest | Visualization |
| seaborn | latest | Statistical visualization |

---

## 🔗 Related Portfolio

> This analysis is the **Python/Scanpy reproduction** of an R/Seurat pipeline on the same dataset.
> Both pipelines are available for direct methodological comparison:

| Pipeline | Language | Repository |
|---|---|---|
| **This repo** | Python · Scanpy · decoupler | [scRNAseq-kidney-diabetes-GSE279086-scanpy](https://github.com/mimakbio-cpu/scRNAseq-kidney-diabetes-GSE279086-scanpy) |
| **R pipeline** | R · Seurat · MAST · clusterProfiler | [scRNAseq-kidney-diabetes-GSE279086](https://github.com/mimakbio-cpu/scRNAseq-kidney-diabetes-GSE279086-) |

Running the same analysis in both ecosystems demonstrates:
- Deep understanding of scRNA-seq methodology independent of tooling
- Ability to work across both R and Python environments
- Awareness of methodological differences between platforms

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👨‍🔬 Author

<div align="center">

**Abdul Kader Ibrahim**
*NGS Lab Scientist | Bioinformatics Researcher*

[![Email](https://img.shields.io/badge/Email-mimak.bio%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mimak.bio@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-dnaseq-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/dnaseq)
[![GitHub](https://img.shields.io/badge/GitHub-mimakbio--cpu-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mimakbio-cpu)

*Passionate about single-cell genomics, spatial transcriptomics, and reproducible computational workflows.*
*Bringing both wet lab and bioinformatics expertise to every analysis.*

</div>

---

## 🙏 Acknowledgments

- Dataset from NCBI GEO accession [GSE279086](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE279086)
- CellTypist Adult Human Kidney model from the [Sanger Institute](https://www.celltypist.org)
- Built with the [Scanpy](https://scanpy.readthedocs.io) ecosystem and [decoupler](https://decoupler-py.readthedocs.io)
- Harmony batch correction: [Korsunsky et al., Nature Methods 2019](https://www.nature.com/articles/s41592-019-0619-0)
- PROGENy pathway scoring: [Schubert et al., Nature Communications 2018](https://www.nature.com/articles/s41467-017-02391-6)

---

<div align="center">

*Last Updated: May 2026*

⭐ If you find this analysis useful, please consider starring the repository

</div>
