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
예시 세포주 하나
근데 clustering의 요인을 결정하는건 주요 목적이 아니므로 다음 결과로 넘어갔음 하지만, 세포주마다 어떤 유전자나 pathway에 의해 그 반응이 구분지어지는지 추가 분석하는것도 흥미로울 것.
2. Cell cycle

3. MOA-specific pathway leading-edge genes
<img width="1797" height="600" alt="image" src="https://github.com/user-attachments/assets/57a8a088-037f-400b-bc45-264e67a2d524" />
<img width="678" height="826" alt="image" src="https://github.com/user-attachments/assets/097a5154-7f66-43ac-b062-3c9c2aeb55c9" />

umap한거?  
5. Concordance
<img width="624" height="906" alt="image" src="https://github.com/user-attachments/assets/0e217db1-fcad-45d4-8224-b17a09447707" />

<img width="675" height="1350" alt="image" src="https://github.com/user-attachments/assets/f1f73ba9-1e37-4740-9c43-b8c345c26ede" />

4. 조직에서 target의 발현정도 - 표로 정리

5. 
같은 조직에서도 특정 세포주만 활용하였음 - 같은 조직이어도 여러 세포유형을 대상으로 해서 반응성을 보는 것도 필요.


<br><br>
### References

OpenAI. 2026. GPT-5, ChatGPT model. OpenAI, San Francisco, CA. Available at: https://chat.openai.com/ (accessed in August-September 2026).

Zhang J, Ubas AA, Svensson V, et al. 2026. Tahoe-100M: Mapping drug-induced molecular phenotypes at single-cell resolution. Cell 189(19):5945–5961.e8. DOI:10.1016/j.cell.2026.08.035.
