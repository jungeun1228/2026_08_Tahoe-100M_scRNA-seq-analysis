# 2026_08_Tahoe-100M_scRNA-seq-analysis

| Notebook | Description |
|---|---|
| **00** | Tahoe-100M data download, condition filtering, and Parquet subset generation |
| **01** | Parquet → sparse AnnData (`.h5ad`) conversion by cell line |
| **02** | scRNA-seq preprocessing, clustering, marker-gene, and cell-cycle analyses |
| **03** | Pseudobulk aggregation, normalization, and matched-DMSO log2FC calculation |
| **04** | Gene-level, pathway-level, MOA-specific, and concordance analyses |

<br><br>
### Motivation
Environmental chemicals can act through multiple modes of action (MOAs). Although some chemicals are well characterized as acting on specific molecular targets, secondary or off-target effects may also occur. These effects can alter the dominant MOA and the magnitude of toxicity depending on species- and cell-type-specific sensitivity. Here I aimed to investigate whether responses associated with known MOAs are conserved across cell types or exhibit cell-type-specific differences in sensitivity.

Tahoe-100M (Zhang et al., 2026) is a large-scale perturbation atlas comprising approximately 100 million single-cell transcriptomes from 50 cancer cell lines exposed to approximately 1,100 drug–dose conditions. For this project, seventeen chemicals representing eight MOA classes commonly encountered in environmental toxicology were selected from the Tahoe-100M dataset and evaluated across five cell lines: HT-29, PANC-1, HepG2/C3A, A-172, and BT-474.

* 17 chemicals from 8 MOA classes: A total of 17 substances were selected, including those likely to act through specific MOAs commonly addressed in environmental toxicology, as well as those likely to exhibit non-specific MOA through baseline toxicity.
<img width="797" height="400" alt="image" src="https://github.com/user-attachments/assets/8562276f-0230-4c91-adc7-e17920bffae1" />

<br><br>
### Main results

#### 1. Single-cell clustering and cluster-specific marker expression
* To investigate whether single cells exposed to compounds belonging to the same MOA class exhibited similar transcriptomic responses and clustered together
* When single cells were clustered for each of the five cell lines individually, cell-cycle composition consistently emerged as a major determinant of cell clustering, rather than MOA family.<br>
* While cells exposed to most other compounds were distributed across multiple clusters, cells treated with niclosamide and dexamethasone were predominantly concentrated in specific clusters, as shown below. These clusters were characterized by increased expression of genes mainly associated with cell growth, metabolic regulation, and extracellular matrix (ECM) remodeling.<br>
  - PANC-1, Niclosamide 5 µM – a subset of cluster 5, with high expression of ANLN and TPX2<br>
  - A-172, Niclosamide 5 µM – a subset of cluster 5, with high expression of INSIG1 and PPKAG2<br>
  - A-172, Dexamethasone at all doses – a subset of cluster 0, with high expression of LOX and IGFBP3<br>
* Representative figures for A-172
<img width="956" height="270" alt="image" src="https://github.com/user-attachments/assets/bb957be8-60ed-406d-92da-e60e1d6b436b" />
<img width="382" height="350" alt="image" src="https://github.com/user-attachments/assets/a71f9fb5-9bff-4aaf-9ec9-0d3a5b86cf27" />
<img width="433" height="350" alt="image" src="https://github.com/user-attachments/assets/c13f5fd0-747f-4f1a-9642-853c92feeaad" />
<br><br><br>

#### 2. Cell cycle phase assignment
* To examine whether compound treatment altered cell-cycle distribution since cell cycle-related genes emerged as a major determinant of cell clustering
* Among the 17 compounds, niclosamide showed the most pronounced increase in the G2/M population, consistently across four cell lines. Compounds belonging to the redox-cycling or PPARγ MOA classes also induced moderate cell-cycle alterations in some cell lines.
* Niclosamide induced a pronounced redistribution of the cell-cycle profile toward the G2/M compartment, particularly at 5 µM, with concomitant depletion of the G1 population in HT29, PANC1, HepG2/C3A, and A172 cells. In contrast, triclosan, despite belonging to the same MOA class, produced comparatively modest cell-cycle alterations. These findings suggest that strong niclosamide-induced mitochondrial stress was associated with altered G2/M progression, although additional markers are required to distinguish G2 arrest from mitotic arrest and to exclude effects of differential cell loss.
<br>
<img width="812" height="400" alt="image" src="https://github.com/user-attachments/assets/ede3bfef-8548-49d1-8dbb-74128e524172" />
<br><br><br>

#### 3. Gene set enrichment analysis (GSEA) and leading-edge analysis for MOA-specific/common pathways
  - MOA-specific pathways: one to four pathways from the Hallmark and Reactome gene set collections were selected for each MOA class.
  - Common pathways for stress response: four pathways (E2F_TARGETS, G2M_CHECKPOINT, APOPTOSIS, REACTIVE_OXYGEN_SPECIES_PATHWAY)<br>
* Overall, compound-induced responses showed both cell line-specific and consistent patterns across the five cell lines.
* For example, carbidopa, an AhR agonist, showed a largely consistent direction of change in MOA-specific pathways, although the magnitude of gene expression responses varied across cell lines. In contrast, the two pathways related to cell-cycle regulation showed differences not only in response magnitude but also in the direction of change among cell lines. The cell line-specific differences observed in AhR-related MOA-specific pathways (xenobiotic metabolism, phase I functionalization) may be explained by differences in the expression of AhR and its cofactors, as well as in metabolic regulation, which could result in differential sensitivity to the compound across cell types.
* In contrast, thymol, which acts through a non-specific MOA, showed relatively consistent response directions across cell lines, both at the pathway level and in the subsequent leading-edge gene analysis (results below). This may reflect its non-specific mode of action through hydrophobic partitioning into cell membranes, making the magnitude of its effects less dependent on cell type. This interpretation is consistent with previous research reporting relatively constant critical membrane concentrations across different cell types (Escher et al., 2019).
* Figure: GSEA for MOA-specific/common pathways for carbidopa and thymol
<img width="714" height="300" alt="image" src="https://github.com/user-attachments/assets/86f8e52c-7095-4da7-8cba-e4fe4178560d" />
<img width="713" height="300" alt="image" src="https://github.com/user-attachments/assets/9188eae9-b9fb-4f9f-84b5-1d50dde903bb" />

* Although thymol and chlorhexidine belong to the same broad MOA class, they have been reported to act through distinct underlying mechanisms. Thymol is a small molecule containing a phenolic ring and is expected to disrupt membrane integrity primarily through hydrophobic partitioning into the lipid bilayer. In contrast, chlorhexidine is a cationic amphiphile that affects membranes through direct interactions with phospholipids. In addition, its structural properties may allow it to engage multiple secondary targets, which could contribute to the different directions of cellular responses observed between the two compounds.
* Moreover, as noted above, thymol, which non-specifically targets the cell membrane, showed a relatively conserved response pattern across cell lines, with both the magnitude and direction of gene expression changes remaining broadly consistent across different cell types.

* Figure: Leading edge analysis based on MOA-specific pathways for AhR activators and membrane disruptors
<img width="684" height="300" alt="image" src="https://github.com/user-attachments/assets/53feab2b-1e33-433d-bbf8-01bc09f68969" />
<img width="684" height="300" alt="image" src="https://github.com/user-attachments/assets/04d67412-7081-46fa-8006-1abb565eac3f" />
<br><br>

#### 4. Concordance analysis across cell lines
* To quantify the consistency of transcriptional responses in MOA-specific pathways across cell lines
* MOA groups whose primary targets are relatively consistently present across cell types, such as membrane disruptors and uncouplers, showed higher concordance in transcriptional responses across cell lines than other MOA groups. In particular, thymol, a putative baseline toxicant, exhibited the highest cross-cell-line concordance. In contrast, receptor-mediated pathways, such as those involving AhR or PPARγ, showed more pronounced cell line-dependent response patterns, likely reflecting differences in target expression levels as well as in other cellular factors involved in the respective mechanisms.

<img width="450" height="900" alt="image" src="https://github.com/user-attachments/assets/f1f73ba9-1e37-4740-9c43-b8c345c26ede" />
<img width="413" height="600" alt="image" src="https://github.com/user-attachments/assets/0e217db1-fcad-45d4-8224-b17a09447707" />

### Limitations & Future Directions
- The Tahoe-100M dataset lacked biological replicates, precluding robust statistical analysis. Future studies should therefore use datasets with sufficient biological replication and focus on a smaller number of MOA classes to enable more in-depth analyses.
- Only one specific cell line was analyzed for each tissue type. Given the cellular heterogeneity within individual tissues, future work should examine multiple cell types from the same tissue to better characterize cell type-specific responses.
- Because cancer cell lines were used in this study, the observed responses may differ from those in normal tissues or non-transformed cells.
<br><br>

### References

Escher BI, Glauch L, König M, Mayer P, Schlichting R. 2019. Baseline toxicity and volatility cutoff in reporter gene assays used for high-throughput screening. Chem Res Toxicol 32(8):1646–1655. DOI:10.1021/acs.chemrestox.9b00182.

OpenAI. 2026. ChatGPT (GPT-5.6 Sol) [Large language model]. OpenAI. Available at: https://chatgpt.com/ (accessed September 27, 2026).

Zhang J, Ubas AA, Svensson V, et al. 2026. Tahoe-100M: Mapping drug-induced molecular phenotypes at single-cell resolution. Cell 189(19):5945–5961.e8. DOI:10.1016/j.cell.2026.08.035.
