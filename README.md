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

1. Clustering + cell cycle<br>
특정 MOA를 가진 물질의 target이 많이 발현된 세포주에서 싱글셀들의 반응이 같은 MOA class끼리 clustering되는지 확인하고자 하였음.<br>
When we clustered single cells for all 5 cell lines individually, cell-cycle composition was major determinant for cell clustering rather than MOA family.<br>
다른물질들은 여러 cluster에 걸쳐서 나타나는 반면에 Niclosamide랑 dexamethasone이 clustering되는 경향.<br>
PANC-1 Niclosamide 5 uM - cluster 5의 일부 (ANLN, TPX2 많이 발현)<br>
A-172 Dexamethasone all doses - cluster 0의 일부 (LOX, IGFBP3 많이 발현)<br>
A-172 Niclosamide 5 uM - cluster 5의 일부 (INSIG1, PPKAG2 많이 발현)<br>
E.g., A-172<br>
<img width="956" height="270" alt="image" src="https://github.com/user-attachments/assets/bb957be8-60ed-406d-92da-e60e1d6b436b" />

<img width="437" height="400" alt="image" src="https://github.com/user-attachments/assets/a71f9fb5-9bff-4aaf-9ec9-0d3a5b86cf27" />
<img width="495" height="400" alt="image" src="https://github.com/user-attachments/assets/c13f5fd0-747f-4f1a-9642-853c92feeaad" />
<br>
다만 같은 cluster 내에서도 저 물질의 반응을 구분짓는 주요 유전자가 무엇이었는지 알아보는것도 흥미로울 듯. 또한 세포주마다 Dot plot을 통해 어떤 유전자가 해당 cluster에서 우세한가를 파악하긴 했지만, MOA와 직접적인 연결을 짓기에는 downstream toxic response(?)와 같은 general한 독성반응이었기에 어려웠음. pathway에 의해 그 반응이 구분지어지는지 추가 분석하는것도 흥미로울 것.그렇지만 clustering의 요인을 결정하는건 주요 목적이 아니므로 다음 결과로 넘어가자. 
<br>
여기부터는 지우기?
<img width="535" height="431" alt="image" src="https://github.com/user-attachments/assets/d2896cac-a04d-4f16-85c9-10b405a9a41c" />
<img width="1212" height="466" alt="image" src="https://github.com/user-attachments/assets/d551f4da-3aae-4918-87a0-afce06c773e6" />

<img width="514" height="314" alt="image" src="https://github.com/user-attachments/assets/934fa2fc-2439-4ab7-b52a-818385c69ef5" />

<img width="1056" height="431" alt="image" src="https://github.com/user-attachments/assets/f4e93453-08ed-48e6-ae11-202656f4e458" />
- 그냥 클러스터별로 유전자만? 아니면 물질별 umap MOA plot?
<br><br>
2. Cell cycle
cell cycle관련 유전자가 main determinant이기에, cell cycle이 물질 처리후에 변한 물질이 있나 살펴보았음  <br>
Niclosamide induced a pronounced, dose-dependent redistribution of the cell-cycle profile toward the G2/M compartment, particularly at 5 µM, with concomitant depletion of the G1 population in HT29, PANC1, HepG2_C3A, and A172 cells. In contrast, triclosan produced comparatively modest cell-cycle alterations. These findings suggest that strong niclosamide-induced mitochondrial stress may interfere with G2/M progression, although additional markers are required to distinguish G2 arrest from mitotic arrest and to exclude effects of differential cell loss.
<br>
Niclosamide commonly 뚜렷하게 increased G2/M phase at 5uM in 4 cell lines // PPAR moderate//  다른 세포주에서는 영향이 약하거나 dose-dependent 한 경향이 보이지 않앗음<br>
<img width="1102" height="266" alt="image" src="https://github.com/user-attachments/assets/c4c822ba-a57d-480a-a505-47fe3a6109e0" />
<br><br>
3. Gene set enrichment analysis (GSEA) for MOA-specific/common pathways and leading-edge analysis<br>
  - MOA-specific pathways for each MOA class (1-4 pathways were selected for each)<br>
  - common pathways for stress response (4 pathways: E2F_TARGETS, G2M_CHECKPOINT, APOPTOSIS, REACTIVE_OXYGEN_SPECIES_PATHWAY)<br>
뭐가 눈에 띄는결과??? 공부해보기
Carbidopa는 MOA-specific pathway의 경우 방향성은 같으나 독성의 발현 농도가 cell line 마다 다름 반면 세포주기를 조절하는 pathway들은 방향성도 세포주마다 달랐음 <br>
반면에 non-specific MOA인 thymol은 비교적 반응의 방향성이 pathway측면에서도, 그 이후의 leading-edge gene 측면에서도 conservative했다.
[GSEA for MOA-specific/common pathways]
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


### Limitations and further direction
암세포주 활용하였음. 특정 세포주와 조직에서의 방향성은 다를 수 있음. 같은 조직내에서도 다양한 세포 유형이 존재하므로.


<br><br>
### References

OpenAI. 2026. GPT-5, ChatGPT model. OpenAI, San Francisco, CA. Available at: https://chat.openai.com/ (accessed in August-September 2026).

Zhang J, Ubas AA, Svensson V, et al. 2026. Tahoe-100M: Mapping drug-induced molecular phenotypes at single-cell resolution. Cell 189(19):5945–5961.e8. DOI:10.1016/j.cell.2026.08.035.
