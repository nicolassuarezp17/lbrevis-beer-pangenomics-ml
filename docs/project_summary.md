\# Project Summary



\## Title



Pangenomic and machine learning analysis of \*Levilactobacillus brevis\* strains associated with the beer niche.



\## Objective



This project aimed to identify genomic modules, candidate proteins, and potential biomarkers associated with \*Levilactobacillus brevis\* strains from beer-related environments using public genome data, pangenomic analysis, machine learning, and functional annotation.



\## Background



\*Levilactobacillus brevis\* is a lactic acid bacterium frequently associated with fermented environments and beer spoilage. Some strains can persist under restrictive conditions such as low pH, ethanol, hop-derived antimicrobial compounds, nutrient limitation, and microbial competition. These adaptive traits may be linked to genomic plasticity, accessory genes, regulatory modules, transport systems, and detoxification mechanisms.



\## Workflow



The project followed a multi-step bioinformatic workflow:



1\. Public genome metadata were retrieved and curated from BV-BRC and NCBI.

2\. Genome entries were filtered using assembly accessions, genome quality metadata, source of isolation, and availability of downloadable assemblies.

3\. A subset of 58 genomes was used for the discovery phase, including 18 beer-associated positive genomes and 40 non-beer-associated negative genomes.

4\. PanX was used to construct the pangenome and generate gene clusters.

5\. A binary presence/absence matrix was generated from pangenomic clusters.

6\. Differential cluster analysis was performed to identify clusters enriched in beer-associated strains.

7\. Gene neighborhoods were inspected to identify candidate genomic blocks.

8\. A technological trait map was built using modular scores.

9\. Logistic regression and random forest models were used to classify and prioritize strains.

10\. Candidate proteins were extracted from GenBank files and functionally refined using BLASTP, InterPro, AlphaFold, and Foldseek.

11\. Candidate markers were validated in an expanded dataset of 148 genomes.

12\. An exploratory operator/motif analysis was performed for the main candidate, `CL\_02402`.



\## Main findings



The analysis identified a modular genomic signal enriched in beer-associated \*L. brevis\* strains. The strongest signal was linked to genes and candidate proteins associated with regulation, redox metabolism, transport, and detoxification.



The expanded validation in 148 genomes showed that `CL\_02402` was the most robust biomarker candidate:



\* `CL\_02402`: present in 16/18 positive genomes and 29/130 negative genomes.

\* Delta prevalence: approximately 0.67.

\* Interpreted as the strongest expanded biomarker candidate.



Other candidates such as `CL\_02406`, `CL\_02424`, and `CL\_02363` were relevant in the discovery subset but showed lower discriminatory value in the expanded dataset.



\## Candidate protein interpretation



Four initially hypothetical proteins were prioritized:



| Cluster    | Length | Interpretation                               |

| ---------- | -----: | -------------------------------------------- |

| `CL\_02406` | 245 aa | Putative TauE/SafE transporter               |

| `CL\_02402` | 189 aa | Putative TetR/AcrR transcriptional regulator |

| `CL\_02424` |  51 aa | Small conserved hypothetical protein         |

| `CL\_02363` |  54 aa | Small unresolved hypothetical protein        |



`CL\_02402` was supported by InterPro, AlphaFold, and Foldseek as a putative TetR/AcrR-like transcriptional regulator.



\## Regulatory hypothesis



The genomic neighborhood of `CL\_02402` showed a divergent architecture with `HKAJCJDL\_01698` and a nearby module including `CL\_02406`.



The motif:



```text

TTTACATATTGTAAA

```



was enriched in positive genomes and proposed as a candidate operator motif.



The final proposed model was:



```text

CL\_02402 ← TTTACATATTGTAAA → HKAJCJDL\_01698 → CL\_02406

```



This model remains bioinformatic and hypothesis-generating. Experimental validation would be required to confirm DNA binding, regulatory activity, ligand identity, and phenotypic relevance under beer-like conditions.



\## Tools used



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



\## Relevance



This project demonstrates the use of comparative genomics, pangenomics, and machine learning to prioritize microbial strains and genomic biomarkers with potential relevance in industrial fermentation, beer spoilage monitoring, and microbial adaptation studies.



