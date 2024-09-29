---
layout: review_post
title: "[Paper Review] Effective Distillation of Table-based Reasoning Ability from LLMs"
author: Bohao Yang, Chen Tang, Kun Zhao, Chenghao Xiao, Chenghua Lin
date: 2024-09-29
---



### *Abstract*

1. **배경:** LLM은 테이블 기반 추론을 수행할 수 있지만, 큰 파라미터 수와 높은 연산 요구 사항이 실제 적용에 어려움을 준다. 기존 연구에서 LLM의 수치 추론 능력을 소규모 모델로 증류하는 방법이 연구되어 왔으나, 과학 분야의 테이블 기반 추론에 특화된 소규모 모델에 대한 연구는 부족했다.

2. **제안 방법:** 논문은 LLM을 활용한 두 단계의 증류 방법을 제안한다. 첫 번째 단계는 LLM을 사용해 테이블 기반 추론과 설명을 생성하고, 두 번째 단계에서는 이 생성된 데이터를 사용해 소규모 모델을 미세 조정하여 테이블 추론 능력을 이전하는 것이다.

3. **실험:** 과학 분야의 테이블 기반 텍스트 생성 작업에서 2억 2천만 파라미터 규모의 모델(Flan-T5-base)이 증류 데이터를 통해 미세 조정되었을 때, 전통적인 방법으로 미세 조정한 소규모 모델이나 특정 LLM을 능가하는 성능을 보였다.

4. **결과:** 증류된 CoT(Chain-of-Thought) 데이터를 사용해 소규모 모델을 미세 조정하는 것이 테이블 기반 추론 능력 향상에 효과적이며, 작은 모델로도 큰 모델에 준하는 성능을 달성할 수 있음을 입증했다.

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzcxMjQ5MTAyLDExODc0OTI5OTZdfQ==
-->