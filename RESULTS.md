# Biological Insights Report
## Single-Cell RNA-seq Analysis of Diabetic Kidney Disease
### GSE279086 — Type 1 Diabetes vs Lean Control

**Author:** Abdul Kader Ibrahim  
**Pipeline:** Python/Scanpy  
**Date:** May 2026

---

## 1. Dataset Overview

40 human kidney cortex biopsies (28 T1D, 12 Lean Control) were analyzed using a complete scRNA-seq pipeline. After rigorous quality control, **29,287 high-quality cells** were retained from an initial 406,365 captured cells. The high removal rate (92.8%) reflects the known challenge of kidney tissue dissociation — high ambient RNA and mitochondrial content are characteristic of metabolically active kidney cells, particularly proximal tubule cells.

---

## 2. Cell Type Landscape of the Diabetic Kidney

CellTypist annotation with the Adult Human Kidney reference model identified **18 distinct kidney cell types** across 21 Leiden clusters, spanning all major kidney compartments.

### Cell Type Distribution

| Compartment | Cell Type | Cells | % of Total |
|---|---|---|---|
| **Tubular** | PC (Principal Cell) | 3,824 | 13.1% |
| **Tubular** | DTL (Descending Thin Limb) | 3,693 | 12.6% |
| **Tubular** | PT (Proximal Tubule) | 3,629 | 12.4% |
| **Tubular** | C-TAL (Cortical Thick Ascending Limb) | 2,513 | 8.6% |
| **Tubular** | CCD-IC-A (Collecting Duct Intercalated A) | 2,368 | 8.1% |
| **Vascular** | EC-PTC (Peritubular Capillary Endothelial) | 2,176 | 7.4% |
| **Tubular** | M-TAL (Medullary Thick Ascending Limb) | 1,707 | 5.8% |
| **Vascular** | VSMC/P (Vascular Smooth Muscle/Pericyte) | 1,681 | 5.7% |
| **Tubular** | aPT (Adaptive Proximal Tubule) | 1,563 | 5.3% |
| **Tubular** | CNT (Connecting Tubule) | 1,364 | 4.7% |
| **Vascular** | EC-DVR (Descending Vasa Recta Endothelial) | 1,299 | 4.4% |
| **Tubular** | IC-B (Intercalated Cell B) | 1,032 | 3.5% |
| **Immune** | T cells | 748 | 2.6% |
| **Vascular** | EC-GC (Glomerular Capillary Endothelial) | 607 | 2.1% |
| **Immune** | Non-classical monocytes | 605 | 2.1% |
| **Immune** | DC (Dendritic Cell) | 256 | 0.9% |
| **Vascular** | EC-LYM (Lymphatic Endothelial) | 124 | 0.4% |
| **Glomerular** | Podocytes | 98 | 0.3% |

### Key Observation — Adaptive Proximal Tubule (aPT)
The presence of **aPT as a distinct population (1,563 cells)** is biologically significant. Adaptive proximal tubule cells represent a dedifferentiated, stress-responding PT state increasingly recognized in diabetic kidney disease and acute kidney injury. Their abundance suggests active tubular remodeling in T1D.

### Key Observation — Podocyte Depletion
**Podocytes represent only 0.3% of captured cells** — with only 41 T1D vs 57 Control cells. This near-absence from T1D samples is consistent with podocyte loss in early diabetic glomerulosclerosis, a hallmark of progressive diabetic nephropathy.

---

## 3. Differential Expression Analysis

**9,545 significant DEGs** (FDR < 0.05, |log2FC| > 0.25) were identified across 16 cell types using Wilcoxon rank-sum testing, comparing Type 1 Diabetes vs Lean Control cells within each cell type.

### DEG Summary by Cell Type

| Cell Type | Total DEGs | Upregulated | Downregulated | Key Finding |
|---|---|---|---|---|
| C-TAL | 3,704 | 3,392 (92%) | 312 (8%) | Massive stress response |
| CCD-IC-A | 2,344 | 2,281 (97%) | 63 (3%) | Near-complete upregulation |
| PC | 1,157 | 201 (17%) | 956 (83%) | Predominantly downregulated |
| EC-PTC | 719 | 675 (94%) | 44 (6%) | Strong endothelial activation |
| DTL | 382 | 178 (47%) | 204 (53%) | Bidirectional dysregulation |
| VSMC/P | 286 | 137 (48%) | 149 (52%) | Balanced dysregulation |
| CNT | 236 | 215 (91%) | 21 (9%) | Predominantly upregulated |
| PT | 211 | 209 (99%) | 2 (1%) | Almost entirely upregulated |
| EC-DVR | 203 | 144 (71%) | 59 (29%) | Vascular activation |
| IC-B | 108 | 102 (94%) | 6 (6%) | Intercalated cell stress |
| aPT | 95 | 82 (86%) | 13 (14%) | Adaptive response activation |
| EC-GC | 54 | 52 (96%) | 2 (4%) | Glomerular endothelial activation |
| M-TAL | 34 | 12 (35%) | 22 (65%) | Predominantly downregulated |
| Non-classical monocytes | 7 | 7 (100%) | 0 | Immune activation |
| T cells | 4 | 3 (75%) | 1 (25%) | Minimal change |
| EC-LYM | 1 | 1 (100%) | 0 | Minimal change |
| DC | 0 | 0 | 0 | No significant change |
| Podocytes | 0 | 0 | 0 | Underpowered (41 cells) |

### Key Upregulated Genes

| Gene | Cell Type | Function | Implication |
|---|---|---|---|
| **AKR1C1** | PC, CCD-IC-A | Carbonyl reductase — oxidative stress | Oxidative stress response |
| **FABP5** | EC-PTC | Fatty acid binding protein | Metabolic reprogramming |
| **SERPINA6** | C-TAL | Cortisol-binding protein | Stress hormone response |
| **S100A4** | DTL | Calcium-binding inflammation marker | Inflammatory signaling |
| **SLC14A1** | VSMC/P | Urea transporter | Osmotic stress response |
| **KRT18** | VSMC/P | Keratin — structural protein | Vascular remodeling |

---

## 4. Pathway Analysis

### 4.1 Over-Representation Analysis (ORA)
**3,524 significant pathways** identified across GO Biological Process, KEGG and Reactome databases.

**Universal finding across all major cell types:**
Ribosomal and translation pathways are the most significantly enriched pathways in C-TAL, CCD-IC-A, EC-PTC, PT and CNT simultaneously. This convergence indicates **global translational stress** across the entire kidney in T1D — a coordinated cellular response to metabolic challenge.

**Cell-type specific ORA findings:**

| Cell Type | Top Pathways | Implication |
|---|---|---|
| C-TAL | Translation, Ribosome, Protein Metabolism | Protein synthesis stress response |
| CCD-IC-A | Translation, TCA Cycle, Cellular Respiration | Metabolic reprogramming |
| PC | Glycolysis, Apoptosis, Smooth Muscle Contraction | Energy failure + cell death |
| EC-PTC | Translation Elongation, Protein Targeting | Endothelial stress response |
| PT | Translation, Ribosome, Selenocysteine Synthesis | Proximal tubule stress |
| DTL | TCA Cycle, Oxidative Phosphorylation, Diabetic Cardiomyopathy | Mitochondrial dysfunction |

### 4.2 Pre-Ranked GSEA
**1,891 significant pathways** (FDR < 0.25) across 17 cell types using signed -log10(p-value) ranking.

**Key activated pathways (positive NES — upregulated in T1D):**

| Pathway | Cell Types | Implication |
|---|---|---|
| Eukaryotic Translation Elongation | CNT, aPT, EC-DVR | Translational stress |
| Mitochondrial Translation | IC-B | Mitochondrial compensation |
| Beta Defensins | IC-B, VSMC/P | Innate immune activation |
| Keratinization | VSMC/P | Vascular structural remodeling |
| rRNA Processing | EC-DVR | Ribosomal biogenesis |

**Key suppressed pathways (negative NES — downregulated in T1D):**

| Pathway | Cell Types | Implication |
|---|---|---|
| Nitric Oxide/Guanylate Cyclase | C-TAL | Impaired vasodilation |
| FGFR2 Signaling | C-TAL | Reduced tubular repair |
| ECM/Integrin Interactions | aPT | Matrix remodeling loss |
| Digestion | CNT | Tubular transport dysfunction |
| Olfactory Signaling | VSMC/P | G-protein signaling loss |

### 4.3 PROGENy Pathway Activity Scoring
14 core signaling pathways scored per cell type using pseudobulk MLM on 661 valid pseudobulk samples.

**Most dysregulated pathways (T1D vs Control):**

| Pathway | Cell Type | Direction | Score | Implication |
|---|---|---|---|---|
| **JAK-STAT** | Non-classical monocytes | ⬆️ +2.66 | Strongly activated | Cytokine-driven inflammation |
| **JAK-STAT** | EC-LYM | ⬆️ +2.57 | Strongly activated | Lymphatic inflammatory signaling |
| **JAK-STAT** | EC-PTC | ⬆️ +1.98 | Activated | Endothelial inflammation |
| **JAK-STAT** | EC-GC | ⬆️ +1.44 | Activated | Glomerular endothelial inflammation |
| **PI3K** | DTL | ⬇️ -2.18 | Strongly suppressed | Impaired cell survival |
| **NFkB** | DTL | ⬇️ -0.95 | Suppressed | Anti-inflammatory compensation |
| **TNFa** | DTL | ⬆️ +1.22 | Activated | Tubular inflammatory stress |
| **Hypoxia** | Podocytes | ⬇️ -1.11 | Suppressed | Glomerular hypoxia failure |
| **Androgen** | Podocytes | ⬇️ -1.30 | Suppressed | Podocyte survival loss |
| **MAPK** | C-TAL | ⬇️ -0.28 | Suppressed | Reduced stress response |

---

## 5. Integrated Biological Narrative

### Finding 1 — Global Translational Stress Response
The most consistent finding across all three pathway methods is the upregulation of **ribosomal and translation pathways** in the majority of kidney cell types. C-TAL (3,704 DEGs), CCD-IC-A (2,344 DEGs), EC-PTC (719 DEGs), PT (211 DEGs) and CNT (236 DEGs) all show translation/ribosome as their top ORA pathways, and GSEA confirms translation elongation activation in CNT, aPT and EC-DVR.

> **Interpretation:** The diabetic kidney undergoes a widespread translational stress response — cells compensate for metabolic damage by upregulating protein synthesis machinery. This is a hallmark of the unfolded protein response (UPR) and integrated stress response (ISR) in diabetic tissue.

### Finding 2 — Mitochondrial Dysfunction in the Thin Limb
DTL cells show bidirectional DEGs (47% up, 53% down) with ORA enrichment in TCA cycle, oxidative phosphorylation and mitochondrial ATP synthesis. PROGENy confirms strongly suppressed PI3K (-2.18) and TNFa activation (+1.22).

> **Interpretation:** The descending thin limb undergoes mitochondrial dysfunction in T1D. Energy production via oxidative phosphorylation is impaired while pro-inflammatory TNFa signaling is activated and cell survival PI3K signaling is lost — a combination consistent with early tubular cell death.

### Finding 3 — JAK-STAT Driven Vascular Inflammation
JAK-STAT pathway is the most consistently activated PROGENy pathway, with strong activation in EC-LYM (+2.57), Non-classical monocytes (+2.66), EC-PTC (+1.98) and EC-GC (+1.44). This convergence across immune and vascular cell types points to a coordinated inflammatory state.

> **Interpretation:** JAK-STAT signaling drives a chronic inflammatory response in the T1D kidney vasculature. Cytokine signaling through the JAK-STAT axis activates both immune cells and endothelial cells simultaneously — consistent with diabetic microangiopathy and the rationale for JAK inhibitor trials in DKD.

### Finding 4 — Collecting Duct Functional Failure
PC cells show 1,157 DEGs with 83% downregulated — the most predominantly downregulated cell type in the dataset. ORA confirms glycolysis and apoptosis enrichment. Key transport and energy genes are lost.

> **Interpretation:** Principal cells in the collecting duct are losing their functional identity in T1D. The near-complete downregulation pattern, combined with apoptosis pathway enrichment, suggests active collecting duct cell death rather than transcriptional reprogramming — an irreversible process if untreated.

### Finding 5 — Innate Immune Activation
Non-classical monocytes show the strongest JAK-STAT activation (+2.66) in the entire dataset. IC-B and VSMC/P show defensin pathway activation by GSEA. T cell DEGs are minimal (4 genes).

> **Interpretation:** The dominant immune response in early T1D kidney disease is **innate** rather than adaptive — monocyte JAK-STAT activation and defensin upregulation in structural cells (collecting duct, vascular) indicate pattern recognition-driven innate immunity rather than T cell-mediated adaptive immunity.

### Finding 6 — Glomerular Vulnerability and Podocyte Loss
Podocytes show near-absence in T1D samples (41 vs 57 Control cells). PROGENy reveals suppressed Hypoxia (-1.11) and Androgen (-1.30) signaling in remaining podocytes.

> **Interpretation:** Podocyte depletion is already evident in early T1D. The remaining podocytes show impaired hypoxia sensing and reduced survival signaling — consistent with progressive glomerulosclerosis. Androgen signaling suppression in podocytes is particularly notable as androgen receptors are known podocyte survival factors.

---

## 6. Summary of Key Biological Changes

```
T1D Kidney — Integrated Findings:

TUBULAR COMPARTMENT:
├── C-TAL/M-TAL  → Global translational stress + MAPK suppression
├── DTL          → Mitochondrial dysfunction + PI3K loss + TNFa activation
├── PC/CCD-IC-A  → Collecting duct failure + apoptosis activation
└── PT/aPT/CNT   → Compensatory translation + ECM remodeling loss

VASCULAR COMPARTMENT:
├── EC-PTC       → JAK-STAT inflammation + endothelial activation
├── EC-LYM       → Strongest JAK-STAT activation → lymphatic dysfunction
├── EC-GC        → Glomerular endothelial JAK-STAT activation
└── VSMC/P       → Defensin activation + vascular remodeling

GLOMERULAR COMPARTMENT:
└── Podocytes    → Cellular depletion + hypoxia/androgen signaling loss

IMMUNE COMPARTMENT:
├── Monocytes    → JAK-STAT dominant → innate immune activation
└── T cells      → Minimal transcriptional changes (4 DEGs)
```

---

## 7. Clinical and Therapeutic Implications

| Finding | Therapeutic Implication |
|---|---|
| JAK-STAT activation across vascular + immune cells | **JAK inhibitors** (Baricitinib, Tofacitinib) as DKD therapeutic targets |
| Global translational stress | **Integrated stress response modulators** (ISRIB) as potential intervention |
| Mitochondrial dysfunction in DTL | **Mitochondrial protective agents** (CoQ10, MitoQ) |
| Collecting duct apoptosis | **Anti-apoptotic strategies** targeting PC cell death |
| Podocyte depletion + survival signaling loss | **Podocyte protective agents** (SGLT2i, endothelin antagonists) |
| Innate immune dominance | **Innate immune targeting** over adaptive immune suppression |

---

## 8. Methodological Notes

| Step | Method | Key Parameter |
|---|---|---|
| QC filtering | Fixed thresholds | MT% < 20%, genes 200–7,000, UMI 500–50,000 |
| Normalization | Log1p (CP10K) | target_sum = 10,000 |
| HVG selection | Seurat flavor | n_top_genes = 2,000 |
| Dimensionality reduction | PCA | 30 components |
| Batch correction | Harmony | 40 samples, converged in 9 iterations |
| Clustering | Leiden | resolution = 0.5, 21 clusters |
| Cell annotation | CellTypist | Adult Human Kidney model, majority voting |
| DEG testing | Wilcoxon rank-sum | FDR < 0.05, \|log2FC\| > 0.25 |
| ORA | gseapy.enrichr | GO BP 2023, KEGG 2021, Reactome 2022 |
| GSEA | gseapy.prerank | MSigDB Hallmarks, Reactome, 1000 permutations |
| Pathway activity | decoupler PROGENy MLM | top 500 genes, pseudobulk |

---

*Analysis: Python/Scanpy pipeline | Dataset: GSE279086 | Cells: 29,287 | Cell types: 18 | DEGs: 9,545 | Pathways: 5,415+*  
*Author: Abdul Kader Ibrahim | mimak.bio@gmail.com | github.com/mimakbio-cpu*
