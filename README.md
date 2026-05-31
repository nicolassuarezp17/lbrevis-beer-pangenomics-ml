\# Pangenomic and Machine Learning Analysis of \*Levilactobacillus brevis\* Strains Associated with the Beer Niche



This repository contains the bioinformatic workflow and main results from a pangenomic and machine learning project focused on \*Levilactobacillus brevis\* strains associated with the beer niche.



The project aimed to identify genomic modules, candidate proteins, and potential biomarkers that could help distinguish or prioritize strains associated with beer-related environments. The workflow integrated curated public genome metadata, PanX-based pangenome analysis, presence/absence matrices, differential cluster analysis, machine learning models, candidate protein annotation, 148-genome validation, and exploratory regulatory motif analysis.



\## Project overview



\*Levilactobacillus brevis\* is one of the lactic acid bacteria frequently associated with beer spoilage and fermentation-related environments. Some strains may persist under restrictive conditions such as low pH, ethanol, hop-derived antimicrobial compounds, and nutrient limitation.



This project explored whether genomic signatures could explain differences between beer-associated and non-beer-associated strains. The final analysis identified a modular signal enriched in beer-associated strains and prioritized `CL\_02402` as the strongest expanded biomarker candidate.



\## Main workflow



The analysis followed these main steps:



1\. Public genome metadata curation from BV-BRC and NCBI.

2\. Selection of \*L. brevis\* genomes with usable assembly accessions.

3\. Preparation of GenBank files for pangenomic analysis.

4\. PanX-based pangenome construction.

5\. Presence/absence matrix generation from gene clusters.

6\. Differential cluster analysis between beer-associated and non-beer-associated strains.

7\. Construction of a technological trait map based on candidate genomic modules.

8\. Machine learning classification and strain prioritization.

9\. Candidate protein extraction and functional annotation using BLASTP and InterPro.

10\. Expanded validation in 148 genomes.

11\. Structural interpretation using AlphaFold and Foldseek.

12\. Exploratory operator/motif analysis for `CL\_02402`.



\## Dataset summary



The initial dataset included 270 entries associated with \*Levilactobacillus brevis\*. After metadata curation, removal of unsuitable entries, and verification of downloadable assemblies, 148 genomes were retained for expanded validation.



A subset of 58 genomes was used for the initial PanX-based discovery phase:



\* 18 beer-associated positive genomes.

\* 40 non-beer-associated negative genomes.



\## Key results



The pangenomic analysis identified modular genomic signatures enriched in beer-associated strains. These modules were mainly related to:



\* regulation,

\* redox metabolism,

\* transport,

\* detoxification,

\* and hypothetical proteins requiring further functional interpretation.



Machine learning models based on modular features supported the discriminatory value of these genomic signatures. The ranking strategy combined modular score and logistic regression probability to prioritize candidate strains.



Expanded validation in 148 genomes showed that `CL\_02402` was the most robust candidate biomarker:



\* `CL\_02402`: 16/18 positives and 29/130 negatives.

\* Delta prevalence: approximately 0.67.



Other initial candidates, such as `CL\_02406`, `CL\_02424`, and `CL\_02363`, were relevant in the discovery subset but lost specificity in the expanded dataset.



\## Candidate proteins



Four initially hypothetical proteins were prioritized for functional refinement:



| Cluster    | Length | Final interpretation                         |

| ---------- | -----: | -------------------------------------------- |

| `CL\_02406` | 245 aa | Putative TauE/SafE transporter               |

| `CL\_02402` | 189 aa | Putative TetR/AcrR transcriptional regulator |

| `CL\_02424` |  51 aa | Small conserved hypothetical protein         |

| `CL\_02363` |  54 aa | Small unresolved hypothetical protein        |



`CL\_02402` was further supported by InterPro, AlphaFold, and Foldseek results as a putative TetR/AcrR-like transcriptional regulator.



\## Regulatory model hypothesis



An exploratory analysis of the genomic neighborhood of `CL\_02402` identified a divergent intergenic region between `CL\_02402` and `HKAJCJDL\_01698`.



The motif:



```text

TTTACATATTGTAAA

```



was enriched in positive genomes and was proposed as a candidate operator motif.



The final proposed model was:



```text

CL\_02402 ← TTTACATATTGTAAA → HKAJCJDL\_01698 → CL\_02406

```



This regulatory model is bioinformatic and hypothesis-generating. Experimental validation would be required to confirm DNA binding, regulatory activity, ligand identity, and phenotypic relevance.



\## Repository structure



```text

data/

├── accessions/              Genome accession lists

└── metadata/                Curated metadata and labels



results/

└── tables/

&#x20;   ├── candidate\_proteins/  Candidate protein annotation tables

&#x20;   ├── final\_summary/       Final summary and consistency audit

&#x20;   ├── ml\_ranking/          Machine learning and strain ranking outputs

&#x20;   ├── operator\_motif\_analysis/  CL\_02402 neighborhood and motif analysis

&#x20;   ├── pangenome\_matrices/  PanX cluster outputs and presence/absence matrix

&#x20;   └── validation\_148/      Expanded validation in 148 genomes



scripts/                     Analysis scripts

notebooks/                   Jupyter notebooks

docs/                        Additional documentation

```



\## Tools and software



Main tools and libraries used in the project included:



\* Python

\* pandas

\* scikit-learn

\* PanX

\* Prokka

\* BLASTP

\* InterPro

\* AlphaFold

\* Foldseek

\* Git and GitHub



\## Notes



This repository contains curated metadata, result tables, candidate protein files, and summary outputs. Raw genome files are not included due to file size and reproducibility considerations. Genome accessions are provided so the dataset can be reconstructed from public databases.



\## Author



Nicolás Suárez Peña

Microbiology and Bioanalysis student

Industrial microbiology, fermentation, and bioinformatics



