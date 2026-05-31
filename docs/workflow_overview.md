\# Workflow Overview



This document summarizes the main bioinformatic workflow used in the project:



\*\*Pangenomic and machine learning analysis of \*Levilactobacillus brevis\* strains associated with the beer niche.\*\*



The workflow was designed to move from public genome metadata to candidate genomic modules, strain prioritization, protein-level interpretation, expanded validation, and regulatory hypothesis generation.



\---



\## 1. Metadata retrieval and curation



Genome metadata for \*Levilactobacillus brevis\* were retrieved from public databases, mainly BV-BRC and NCBI.



The initial dataset contained 270 entries. These entries were curated to remove or exclude records that were not suitable for comparative genomic analysis, including:



\* plasmid-only entries,

\* duplicated or redundant records,

\* deprecated records,

\* low-quality genomes,

\* records without usable assembly accessions,

\* records with incomplete or inconsistent metadata.



The main fields considered during curation included:



\* `Assembly Accession`,

\* genome status,

\* genome quality,

\* number of contigs,

\* CheckM completeness,

\* CheckM contamination,

\* genome size,

\* isolation source.



After curation, 162 genomes were retained. From these, 148 genomes had usable and downloadable assembly accessions for downstream analysis.



\---



\## 2. Label assignment



The study focused on identifying genomic signatures associated with the beer niche.



Genomes were labeled according to their isolation source:



\* \*\*Positive group:\*\* strains associated with beer or brewery-related environments.

\* \*\*Negative group:\*\* strains from other sources or non-beer-associated environments.



The expanded dataset included:



\* 18 positive genomes,

\* 130 negative genomes,

\* 148 genomes in total.



A subset of 58 genomes was used for the initial PanX discovery phase:



\* 18 positive genomes,

\* 40 negative genomes.



\---



\## 3. Genome preparation



Genome assemblies were retrieved using their assembly accessions.



GenBank files were used because they include:



\* nucleotide sequences,

\* annotated coding sequences,

\* locus tags,

\* gene products,

\* genomic coordinates.



PanX requires properly annotated coding sequences to compare homologous proteins across genomes.



Some genomes required reannotation using Prokka to generate compatible GenBank files and recover genomes that initially failed during PanX processing.



\---



\## 4. Pangenome construction with PanX



PanX was used to construct the pangenome from the selected genome subset.



The analysis grouped homologous proteins into gene clusters. These clusters represented the basis for downstream comparative analyses.



The PanX workflow generated the file:



```text

allclusters\_final.tsv

```



This file links genomes, locus tags, and gene clusters.



The pangenome analysis of the 58-genome subset identified more than 10,000 gene clusters.



\---



\## 5. Presence/absence matrix construction



The PanX cluster output was transformed into a binary presence/absence matrix.



In this matrix:



\* rows represent genomes,

\* columns represent gene clusters,

\* `1` means the cluster is present,

\* `0` means the cluster is absent.



The main matrix generated was:



```text

matriz\_presencia\_ausencia\_subset58.csv

```



This matrix was used to compare cluster distribution between positive and negative genomes.



\---



\## 6. Differential cluster analysis



Each cluster was evaluated according to its prevalence in the positive and negative groups.



For each cluster, the following values were calculated:



\* prevalence in positive genomes,

\* prevalence in negative genomes,

\* delta prevalence,

\* Fisher exact test,

\* Benjamini-Hochberg FDR correction.



The goal was to identify clusters enriched in beer-associated strains.



Clusters with high prevalence in positives and low prevalence in negatives were prioritized as candidates.



\---



\## 7. Functional annotation of top clusters



Top enriched clusters were functionally inspected using GenBank annotations.



For representative genomes, locus tags were parsed from GenBank files to extract:



\* gene names,

\* annotated protein products,

\* genomic coordinates,

\* coding sequence information.



This step allowed the transition from statistical cluster enrichment to biological interpretation.



Several top clusters were associated with:



\* redox metabolism,

\* transcriptional regulation,

\* transport,

\* detoxification,

\* hypothetical proteins.



\---



\## 8. Gene neighborhood and candidate genomic blocks



The genomic neighborhoods of top clusters were inspected to determine whether candidate genes appeared as isolated elements or as conserved modules.



This analysis identified conserved gene neighborhoods with syntenic organization.



Two main candidate blocks were defined:



\* \*\*Block 1:\*\* associated mainly with redox metabolism, regulation, transport, detoxification, and hypothetical proteins.

\* \*\*Block 2:\*\* associated with regulation and oxidoreductive functions.



These candidate blocks were later transformed into modular scores.



\---



\## 9. Technological trait map



A technological trait map was constructed to summarize the presence of candidate modules in each genome.



Each strain received modular scores based on the presence of selected markers:



\* `score\_bloque1`,

\* `score\_bloque2`,

\* `score\_total\_modulos`,

\* redox/detoxification module,

\* regulation module.



This step converted pangenomic information into interpretable numerical features for strain comparison and machine learning.



\---



\## 10. Machine learning and strain ranking



Machine learning models were trained using modular features derived from the candidate blocks.



The main models used were:



\* logistic regression,

\* random forest.



The models were used to evaluate whether modular features could discriminate beer-associated from non-beer-associated strains.



A ranking system was then created using:



```text

priority score = 0.5 × normalized modular score + 0.5 × logistic regression probability

```



This ranking prioritized strains with strong modular signatures and high predicted probability of belonging to the positive group.



\---



\## 11. Candidate protein selection



From the modular signature, four initially hypothetical protein clusters were prioritized:



| Cluster    | Length |

| ---------- | -----: |

| `CL\_02406` | 245 aa |

| `CL\_02402` | 189 aa |

| `CL\_02424` |  51 aa |

| `CL\_02363` |  54 aa |



Protein sequences were extracted from GenBank files using their corresponding locus tags.



These sequences were then used for functional refinement.



\---



\## 12. Functional refinement with BLASTP and InterPro



Candidate protein sequences were analyzed using BLASTP and InterPro.



The main interpretations were:



\* `CL\_02406`: putative TauE/SafE transporter.

\* `CL\_02402`: putative TetR/AcrR transcriptional regulator.

\* `CL\_02424`: small conserved hypothetical protein.

\* `CL\_02363`: unresolved small hypothetical protein.



At this stage, `CL\_02402` and `CL\_02406` became the main functional candidates.



\---



\## 13. Expanded validation in 148 genomes



The four candidate proteins were validated in the expanded dataset of 148 genomes.



The validation showed that:



\* `CL\_02402` remained enriched in positive genomes.

\* `CL\_02406`, `CL\_02424`, and `CL\_02363` lost specificity in the expanded dataset.



Main expanded validation result:



```text

CL\_02402: 16/18 positives and 29/130 negatives

Delta prevalence ≈ 0.67

```



This supported `CL\_02402` as the strongest expanded biomarker candidate.



\---



\## 14. Structural interpretation



Because `CL\_02402` was initially annotated as hypothetical but showed evidence compatible with TetR/AcrR-like regulators, structural analysis was performed.



The structure was predicted using AlphaFold and searched against structural databases using Foldseek.



The structural results supported the interpretation of `CL\_02402` as a putative TetR/AcrR-like transcriptional regulator.



This step helped move from sequence-based annotation to structure-supported functional inference.



\---



\## 15. Operator and motif analysis



The genomic neighborhood of `CL\_02402` was inspected to identify possible regulatory regions.



A divergent intergenic region between `CL\_02402` and `HKAJCJDL\_01698` was identified.



This region was 77 bp long in the reference genome and contained AT-rich motifs compatible with candidate operator sequences.



The main motif proposed was:



```text

TTTACATATTGTAAA

```



This motif was enriched in positive genomes and was proposed as a candidate operator associated with `CL\_02402`.



\---



\## 16. Final regulatory hypothesis



The final proposed model was:



```text

CL\_02402 ← TTTACATATTGTAAA → HKAJCJDL\_01698 → CL\_02406

```



In this model:



\* `CL\_02402` is a putative TetR/AcrR transcriptional regulator.

\* `TTTACATATTGTAAA` is a candidate operator motif.

\* `HKAJCJDL\_01698` is a possible immediate target gene.

\* `CL\_02406` is a putative TauE/SafE transporter associated with the candidate module.



This model remains bioinformatic and hypothesis-generating. Experimental validation is required to confirm protein-DNA binding, regulatory activity, ligand identity, and phenotypic relevance.



\---



\## 17. Main outputs



The main output files are organized in:



```text

data/

results/tables/

docs/

```



Important result categories include:



\* curated metadata,

\* genome accession lists,

\* PanX cluster outputs,

\* presence/absence matrices,

\* machine learning and ranking outputs,

\* candidate protein annotation files,

\* expanded validation results,

\* CL\_02402 operator/motif analysis,

\* final summary tables.



\---



\## 18. Limitations



The main limitations of the workflow include:



\* the initial discovery phase was performed on a 58-genome subset due to computational constraints,

\* functional assignments for some candidates remain putative,

\* the operator motif was predicted bioinformatically but not experimentally validated,

\* the ligand of `CL\_02402` was not identified,

\* phenotypic validation under beer-like conditions remains necessary.



\---



\## 19. Future work



Recommended next steps include:



\* experimental validation of `CL\_02402` binding to the candidate operator,

\* gene expression analysis under beer-like stress conditions,

\* phenotypic assays for hop tolerance, ethanol tolerance, low pH tolerance, and oxidative stress,

\* comparative analysis with additional beer-spoilage lactic acid bacteria,

\* expansion of the dataset with newly available genomes.



