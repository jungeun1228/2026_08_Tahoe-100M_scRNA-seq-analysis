# 2026_08_Tahoe-100M_scRNA-seq-analysis

### Purpose

1. Compare 
2. Quantify concordance 
<br><br>
### Motivation
Environmental chemicals can act through multiple modes of action (MOAs). Although some chemicals are well characterized as acting on specific molecular targets, secondary or off-target effects may also occur. These effects can alter the dominant MOA and the magnitude of toxicity depending on species- and cell-type-specific sensitivity. Here I aimed to investigate whether responses associated with known MOAs are conserved across cell types or exhibit cell-type-specific differences in sensitivity.

Tahoe-100M (Zhang et al., 2026) is a large-scale perturbation atlas comprising approximately 100 million single-cell transcriptomes from 50 cancer cell lines exposed to approximately 1,100 drug–dose conditions. For this project, seventeen chemicals representing eight MOA classes commonly encountered in environmental toxicology were selected from the Tahoe-100M dataset and evaluated across five cell lines: HT-29, PANC-1, HepG2/C3A, A-172, and BT-474.

* 17 chemicals from 8 MOA classes: A total of 17 substances were selected, including those likely to act through specific MOAs commonly addressed in environmental toxicology, as well as those likely to exhibit non-specific MOA through baseline toxicity.
<img width="797" height="400" alt="image" src="https://github.com/user-attachments/assets/8562276f-0230-4c91-adc7-e17920bffae1" />

<br><br>
### Main results

#### 1. Single-cell clustering, cell cycle analysis
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

#### 3. Gene set enrichment analysis (GSEA) for MOA-specific/common pathways and leading-edge analysis
  - MOA-specific pathways: one to four pathways from the Hallmark and Reactome gene set collections were selected for each MOA class.
  - Common pathways for stress response: four pathways (E2F_TARGETS, G2M_CHECKPOINT, APOPTOSIS, REACTIVE_OXYGEN_SPECIES_PATHWAY)<br>
* Overall, compound-induced responses showed both cell line-specific and consistent patterns across the five cell lines.
* For example, carbidopa, an AhR agonist, showed a largely consistent direction of change in MOA-specific pathways, although the magnitude of gene expression responses varied across cell lines. In contrast, the two pathways related to cell-cycle regulation showed differences not only in response magnitude but also in the direction of change among cell lines. The cell line-specific differences observed in AhR-related MOA-specific pathways (xenobiotic metabolism, phase I functionalization) may be explained by differences in the expression of AhR and its cofactors, as well as in metabolic regulation, which could result in differential sensitivity to the compound across cell types.
* In contrast, thymol, which acts through a non-specific MOA, showed relatively consistent response directions across cell lines, both at the pathway level and in the subsequent leading-edge gene analysis (results below). This may reflect its non-specific mode of action through hydrophobic partitioning into cell membranes, making the magnitude of its effects less dependent on cell type. This interpretation is consistent with previous research reporting relatively constant critical membrane concentrations across different cell types (Escher et al., 2019).

<br>
* GSEA for MOA-specific/common pathways
<img width="1382" height="581" alt="image" src="https://github.com/user-attachments/assets/86f8e52c-7095-4da7-8cba-e4fe4178560d" />
<img width="1380" height="581" alt="image" src="https://github.com/user-attachments/assets/9188eae9-b9fb-4f9f-84b5-1d50dde903bb" />

[Leading edge analysis based on MOA-specific pathway]
같은 MOA class라도 thymol과 chlorhexidine은 세부 MOA가 다른것으로 추정됨. Thymol은 phenol ring을 가진 small molecule로서, hydrophobic partition으로 membrane을 교란시킬 것으로 예상하지만,  chlorhexidine은 cationic amphiphile로서 phospholipid와 직접 결합하는 식으로 membrane에 영향을 주기 때문에 반응의 방향이 다른 것으로 예상된다. 또한 non-specific MOA를 가진 thymol은 세포주가 달라도 유전자 발현 농도나 그 방향이 전반적으로 conservative한 것을 볼 수 있다.
<img width="1368" height="600" alt="image" src="https://github.com/user-attachments/assets/53feab2b-1e33-433d-bbf8-01bc09f68969" />
<img width="1367" height="600" alt="image" src="https://github.com/user-attachments/assets/04d67412-7081-46fa-8006-1abb565eac3f" />

umap한거?

<br><br>
4. Concordance<br>

<img width="675" height="1350" alt="image" src="https://github.com/user-attachments/assets/f1f73ba9-1e37-4740-9c43-b8c345c26ede" />
<img width="624" height="906" alt="image" src="https://github.com/user-attachments/assets/0e217db1-fcad-45d4-8224-b17a09447707" />

5. 조직에서 target의 발현정도 - 표로 정리

### 
같은 조직에서도 특정 세포주만 활용하였음 - 같은 조직이어도 여러 세포유형을 대상으로 해서 반응성을 보는 것도 필요.


### Limitations & further direction
암세포주 활용하였음. 특정 세포주와 조직에서의 방향성은 다를 수 있음. 같은 조직내에서도 다양한 세포 유형이 존재하므로.
세포마다 같은 target을 건드렸어도, 다른 pathway가 활성화될 수 있음 (예. AhR -> liver metabolism/ detox 기전 vs. gut이나 brain 은 inflammation/ immunity 관련 기전, breast는 ER signalling과 강한 crosstalk이 있음 - hormone signling,  development등)


<br>
다만 같은 cluster 내에서도 저 물질의 반응을 구분짓는 주요 유전자가 무엇이었는지 알아보는것도 흥미로울 듯. 또한 세포주마다 Dot plot을 통해 어떤 유전자가 해당 cluster에서 우세한가를 파악하긴 했지만, MOA와 직접적인 연결을 짓기에는 downstream toxic response(?)와 같은 general한 독성반응이었기에 어려웠음. pathway에 의해 그 반응이 구분지어지는지 추가 분석하는것도 흥미로울 것.그렇지만 clustering의 요인을 결정하는건 주요 목적이 아니므로 다음 결과로 넘어가자. 

<br><br>
### References

Beate I. Escher, Lisa Glauch, Maria König, Philipp Mayer, Rita Schlichting; Baseline Toxicity and Volatility Cutoff in Reporter Gene Assays Used for High-Throughput Screening. Chem. Res. Toxicol. 19 August 2019; 32 (8): 1646–1655. https://doi.org/10.1021/acs.chemrestox.9b00182

OpenAI. 2026. GPT-5, ChatGPT model. OpenAI, San Francisco, CA. Available at: https://chat.openai.com/ (accessed in August-September 2026).

Zhang J, Ubas AA, Svensson V, et al. 2026. Tahoe-100M: Mapping drug-induced molecular phenotypes at single-cell resolution. Cell 189(19):5945–5961.e8. DOI:10.1016/j.cell.2026.08.035.
