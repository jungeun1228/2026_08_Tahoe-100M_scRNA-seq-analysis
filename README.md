# 2026_08_Tahoe-100M_scRNA-seq-analysis

### Purpose

1. Compare 
2. Quantify concordance 
<br><br>
### Motivation
Environmental chemicals can act through multiple modes of action (MOAs). Although some chemicals are well characterized as acting on specific molecular targets, secondary or off-target effects may also occur. These effects can alter the dominant MOA and the magnitude of toxicity depending on species- and cell-type-specific sensitivity. Here I aimed to investigate whether responses associated with known MOAs are conserved across cell types or exhibit cell-type-specific differences in sensitivity.

Tahoe-100M (Zhang et al., 2026) is a large-scale perturbation atlas comprising approximately 100 million single-cell transcriptomes from 50 cancer cell lines exposed to approximately 1,100 drug–dose conditions. For this project, seventeen chemicals representing eight MOA classes commonly encountered in environmental toxicology were selected from the Tahoe-100M dataset and evaluated across five cell lines: HT-29, PANC-1, HepG2/C3A, A-172, and BT-474.

* 8 MOA classes
Baseline toxicity (represent non-specific MOA)

<br><br>
### Main results

1. Clustering + cell cycle
특정 MOA를 가진 물질의 target이 많이 발현된 세포주에서 싱글셀들의 반응이 clustering되는지 확인하고자.
다른물질들은 여러 cluster에 걸쳐서 나타나는 반면에 Niclosamide랑 dexamethasone이 clustering되는 경향.
PANC-1 Niclosamide 5 uM - cluster 5의 일부 (ANLN, TPX2 많이 발현)
A-172 Dexamethasone all doses - cluster 0의 일부 (LOX, IGFBP3 많이 발현)
A-172 Niclosamide 5 uM - cluster 5의 일부 (INSIG1, PPKAG2 많이 발현)
When we clustered single cells for all 5 cell lines individually, cell-cycle composition was major determinant for cell clustering (e.g., HT-29).
E.g., A-172
<img width="956" height="270" alt="image" src="https://github.com/user-attachments/assets/bb957be8-60ed-406d-92da-e60e1d6b436b" />
<img width="1601" height="878" alt="image" src="https://github.com/user-attachments/assets/ed08290e-4109-498a-a1d0-b3995e5d5759" />

<img width="932" height="853" alt="image" src="https://github.com/user-attachments/assets/a71f9fb5-9bff-4aaf-9ec9-0d3a5b86cf27" />
<img width="2016" height="1630" alt="image" src="https://github.com/user-attachments/assets/c13f5fd0-747f-4f1a-9642-853c92feeaad" />

예시 세포주 하나
근데 clustering의 요인을 결정하는건 주요 목적이 아니므로 다음 결과로 넘어갔음 하지만, 세포주마다 어떤 유전자나 pathway에 의해 그 반응이 구분지어지는지 추가 분석하는것도 흥미로울 것.

<img width="535" height="431" alt="image" src="https://github.com/user-attachments/assets/d2896cac-a04d-4f16-85c9-10b405a9a41c" />
<img width="1212" height="466" alt="image" src="https://github.com/user-attachments/assets/d551f4da-3aae-4918-87a0-afce06c773e6" />

<img width="514" height="314" alt="image" src="https://github.com/user-attachments/assets/934fa2fc-2439-4ab7-b52a-818385c69ef5" />

<img width="1056" height="431" alt="image" src="https://github.com/user-attachments/assets/f4e93453-08ed-48e6-ae11-202656f4e458" />
- 그냥 클러스터별로 유전자만? 아니면 물질별 umap MOA plot?
  
2. Cell cycle
같은 MOA 여도 다른 경향성
Niclosamide induced a pronounced, dose-dependent redistribution of the cell-cycle profile toward the G2/M compartment, particularly at 5 µM, with concomitant depletion of the G1 population in HT29, PANC1, HepG2_C3A, and A172 cells. In contrast, triclosan produced comparatively modest cell-cycle alterations. These findings suggest that strong niclosamide-induced mitochondrial stress may interfere with G2/M progression, although additional markers are required to distinguish G2 arrest from mitotic arrest and to exclude effects of differential cell loss.

Niclosamide commonly 뚜렷하게 increased G2/M phase at 5uM in 4 cell lines // PPAR moderate//  다른 세포주에서는 영향이 약하거나 dose-dependent 한 경향이 보이지 않앗
<img width="1102" height="266" alt="image" src="https://github.com/user-attachments/assets/c4c822ba-a57d-480a-a505-47fe3a6109e0" />

4. MOA-specific pathway and leading-edge genes
<img width="1797" height="600" alt="image" src="https://github.com/user-attachments/assets/57a8a088-037f-400b-bc45-264e67a2d524" />
<img width="678" height="826" alt="image" src="https://github.com/user-attachments/assets/097a5154-7f66-43ac-b062-3c9c2aeb55c9" />

umap한거?  
4. Concordance
<img width="624" height="906" alt="image" src="https://github.com/user-attachments/assets/0e217db1-fcad-45d4-8224-b17a09447707" />

<img width="675" height="1350" alt="image" src="https://github.com/user-attachments/assets/f1f73ba9-1e37-4740-9c43-b8c345c26ede" />

5. 조직에서 target의 발현정도 - 표로 정리

6. 
같은 조직에서도 특정 세포주만 활용하였음 - 같은 조직이어도 여러 세포유형을 대상으로 해서 반응성을 보는 것도 필요.


<br><br>
### References

OpenAI. 2026. GPT-5, ChatGPT model. OpenAI, San Francisco, CA. Available at: https://chat.openai.com/ (accessed in August-September 2026).

Zhang J, Ubas AA, Svensson V, et al. 2026. Tahoe-100M: Mapping drug-induced molecular phenotypes at single-cell resolution. Cell 189(19):5945–5961.e8. DOI:10.1016/j.cell.2026.08.035.
