---
layout: review_post
title: "[Paper Review] KitchenScale: Learning to Predict Ingredient Quantities from Recipe Contexts"
author: Sohyun
date: 2024-07-27
---

## 여는 글

해당 논문은 레시피 문맥을 기반으로 목표 재료의 양과 단위를 예측하는 것을 목표로 하는 사전 학습된 모델(PLM)인 Kitchen Scale 이라는 언어 모델을 소개한다. 여기서 주목한 것은 양에 대한 예측이다. 실제로 이전의 여러 실험에서는 주로 비율로 성분 조성을 제안하거나 숫자와 단위를 텍스트로 취급하는 방식으로 재료의 양을 다루어서 양을 정확하게 예측하는 데 한계가 있다.

실제로 LLM은 숫자를 다룰 때, 뭔가 나사가 빠진 모습을 보일 때가 많다. 이는 이들을 숫자 보단 텍스트로 취급하고 모델이 학습하기 때문이다.

![스크린샷 2024-07-27 225922](https://github.com/user-attachments/assets/7d0ecb9a-df9b-4560-a551-9183479c0fe2){: .responsive-img .align-center}


위 사진은 ChatGPT 4o 한테 숫자 비교를 시킨 것인데, 이러한 단순 비교에서도 제대로 못하는 모습을 보여준다.

이러한 문제는 레시피를 다룰 때도 나타난다. 이전에 동일하게 ChatGPT 4o 로 브라우니 레시피 생성 후, 이를 저당 레시피로 바꿔달라고 요청을 해보았는데, 설탕을 스테비아로 변환하는 것 까지는 잘하지만 설탕 200g을 스테비아 200g 으로 대체해버리는 등, Quantity에 대한 처리는 잘 하지 못하는 모습을 보여주었다.

이 논문에서는 이를 해결하기 위해 DExp(Discrete Latent Exponent) 이라는 방법을 사용했다고 하는데, 이에 관심이 생겨 해당 논문을 읽어보았다.


## Introduction

기존의 SHARE[^1] 연구나 레시피와 관련된 연구들은 레시피 재료의 대체, 또는 레시피 생성에 집중을 하고 양과 관련된 문제의 경우 Limitation으로 기술되어 있는 경우가 대부분이었다. 기존에는 재료의 양의 경우 비율로 제안하거나 숫자와 단위를 단순히 텍스트로 취급하는 방법을 사용하는 방식을 취하였다. 따라서 본 연구는 이러한 부분에 초점을 맞추었다.

해당 연구의 중요성과 목표를 간단하게 설명하면,

-   **중요성**: 요리에서 적절한 재료의 양을 결정하는 것은 맛을 풍부하게 하고 건강을 증진시키는 데 중요한 요소이다.
-   **목표**: 이를 해결하기 위해 레시피 문맥을 기반으로 특정 재료의 양과 측정 단위를 예측하는 모델, KitchenScale을 소개한다.

위와 같다.

[^1]:SHARE: a System for Hierarchical Assistive Recipe Editing


해당 논문에서 제시한 KitchenScale 모델을 효과적으로 학습시키기 위해 연구진은 다음과 같은 세 가지의 하위 작업으로 재료 양 측정 문제를 구성했다.

1. **재료 측정 유형 분류**(Measurement Type Classification): 재료가 부피로 측정되는지, 중량으로 측정되는지를 분류
2. **단위 분류**(Unit Classification): 재료의 측정 단위를 예측(Oz, Cup, Spoon, etc.)
3. **양 회귀 작업**(Quantity Regression): 재료의 정확한 양 예측

이 모델은 레시피 텍스트에서 요리 지식을 학습하는 전이 학습 방법을 사용하여 개발되었고, 레시피 데이터의 수치적 변동성을 효과적으로 처리하기 위해 이산 잠재 지수(**DExp**) 방법을 채택했다고 한다.

간단하게 실험 설정과 결과에 대해 언급하였는데 새로 구축한 데이터셋과 추천 예제를 통해 KitchenScale의 다양한 레시피 문맥에 대한 이해와 재료 양 예측의 일반화 가능성을 실험했고, KitchenScale의 기능을 시연하기 위해 웹 애플리케이션을 구현했다고 한다. 이 애플리케이션은 숫자(예: 2)와 단위(예: 온스)로 표현된 재료 양을 추천하는 기능을 제공한다.

해당 연구의 기여는
-   **재료 양 예측 작업 정의**: 재료 측정 유형 분류, 단위 분류, 양 회귀의 세 가지 하위 작업으로 구성된 재료 양 예측 작업을 정의했다.
-   **KitchenScale 개발**: PLM을 활용하여 재료 양 예측 작업을 수행하는 KitchenScale 모델을 개발했다.
-   **데이터셋 구축**: 레시피 텍스트를 기반으로 대규모 데이터셋을 구축하여 모델을 학습시켰다.
-   **실험 결과**: KitchenScale의 다양한 레시피 문맥에 대한 이해와 재료 양 예측 능력을 실험을 통해 검증했다.
-   **웹 애플리케이션 구현**: KitchenScale의 기능을 시연하기 위한 웹 기반 애플리케이션을 구현했다.

5 가지의 기여점이 있다고 한다.


## Related Works


### 수치 추론과 언어 모델링


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk5MDU3MzQ3MiwtMzkyODM3MTQ2LDEzMj
M2OTQwMzIsNzMxNzAzMywxMDk1NDc4NTMzLC05Mzc2MTA5NzAs
LTE0NjYxMTM0MTAsLTE1MDQ5Mzk0NjMsLTMxMDIxNjU4Myw2OT
UzMTU3NTksMTU3NTE5Mjk0NCwtMjAzNTEwMTM2LDY2MDcxMjg1
NiwtMTA2MDEwNTcyNCwtMTk0NTkyOTA3NCw3MTU2MDkyOTQsOD
EyMzIwNDUyLC0xNTI1NDYyOTEwLDM1MTIyNTgyMCwtMTc3Mzgz
NTc0N119
-->