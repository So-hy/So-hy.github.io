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

해당 연구의 중요성과 목표는 아래와 같다.

-   **중요성**: 요리에서 적절한 재료의 양을 결정하는 것은 맛을 풍부하게 하고 건강을 증진시키는 데 중요한 요소이다.
-   **목표**: 이를 해결하기 위해 레시피 문맥을 기반으로 특정 재료의 양과 측정 단위를 예측하는 모델, KitchenScale을 소개한다.


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


### Numerical Reasoning & Language Modeling

PLM(Pre-trained Language Model)은 이미 많은 자연어 처리 작업에서 사용되고 있다. BERT나 GPT가 그 예이다.

최근 들어, 자연어 처리(NLP) 분야에서 숫자를 다루는 작업이 중요하게 다루어지기 시작했다고 한다. 아래의 예들은 수치 지식과 수치 임베딩과 관련된 탐구들이다.

Lin et al. (2020), Yamane et al. (2020), Elazar et al. (2019)[^2]


또다른 연구는 PLM이 일반적으로 숫자의 크기를 학습할 수 있다고 말한다.

Zhang et al., 2020[^3]



그러나 특정 도메인의 데이터 셋에서는 숫자의 분포 특성 때문에 회귀(숫자 예측) 작업에서 어려움을 겪을 수 있다. 전통적인 선형 회귀 방법으로 간단한 숫자 값을 예측하려는 연구가 있었으나, 고차원 수치에 대한 예측은 가능도 기반 회귀(Likelihood-Based Regression)이 더 효과적이다는 것을 밝혔다고 한다.(Spithourakis and Riedel, 2018)[^4] 그러한 방법 중 하나가 바로 해당 연구에서 사용하는 DExp 방법이다.(Spokoyny and Berg-Kirkpatrick, 2020)[^5]



### Application with Food Recipes

레시피와 관련된 연구도 다양한 접근법이 제안되었다.

레시피 임베딩부터 재료 추천, 레시피 추천, 레시피 검색 등의 접근법이 있었고, GPT와 같은 생성 모델이 시피 생성에 사용되기 시작했다. 그러나 이러한 생성 모델들은 숫자를 단어처럼 처리하여, 숫자 값의 차이를 제대로 처리하지 못한다.

이런 제안 뿐만 아니라 레시피 모델의 학습에 쓰일 데이터셋을 구축하는 연구도 있었다. Recipe1M은 100만개 이상의 요리 레시피와 1,300만 개의 음식 이미지를 포함하는 다중 모달 데이터셋이다. 여러 연구들이 이 데이터셋을 활용해 레시피 마이닝을 수행했고 RecipeDB와 Reciptor는 더 구조화된 데이터 요소를 도입했다. 본 연구에서는 위의 두 데이터셋을 통합하여 보다 포괄적이고 구조화된 데이터셋을 구축했다.

##  Ingredient Quantity  Prediction  Task


이 섹션에서는 요리 레시피에서 사용되는 다양한 의미 요소들에 대해 정의하고, 제안된 재료 양 예측 과제를 설명한다.

- **레시피 $R$** : 요리를 위해 사용자가 필요한 다양한 음식 관련 의미(sementics)를 설명하는 레시피다. 레시피는 레시피 제목 $e$, 재료 $I$, 설명 태그? $B$, 그리고 몇 인분에 대한 값 $s$로 구성된다.
    
- **재료 $I$** : 레시피의 $n$ 가지 기본 요소로, 최종 요리의 맛과 질감을 결정한다. 각 재료는 $I =\{i_0, i_1,...,i_{n-1}\}$ 로 표현되며, \| $I$ \| $=n$ 이다.
    
- **타겟 재료 $i_t$** : 수치 탐구 과제를 위해 $I$ 에서 지정된 하나의 재료이다 ( $i_t \in I$ ).
    
- **기타 재료 $I_o$​** : 타겟 재료를 제외한 재료들의 집합이다. \| $I_o\cap\{i_t\}$ \| $=0$ 이고, $I_o\cup\{i_t\} = I$ 이다.
    
- **제목 $e$** : 요리를 간략히 설명하는 레시피의 제목이다.
    
- **태그 $B$** : 요리의 지역?(어느 나라 요리인가를 의미하는 것 같다.), 요리 시간, 카테고리 등의 특정 정보를 제공하는 m개의 태그이다. $B = \{b_0, b_1, ... , b_{m-1}\}$ 로 표현되며, \|$B$\|$ = m$ 이다.
    
- **몇 인분에 대한 값(제공량) $s$** : 동일한 요리를 만들 때 사용되는 재료의 양을 조정하기 위한 스칼라 값이다. Number of Servings 라고 표기되어 있다.
    
- **레시피 문맥 질의 구성 $C$** : Source 레시피 $R$ 에서 추출한 텍스트 요소들로 구성된 레시피 문맥 질의다. 각 수치 탐구 과제에서 $C = \{i_t, I_o, B, e, s\}$ 를 입력으로 사용한다.

수치 탐구 과제..?(Numeracy probing task) 라는 말이 나오는데 처음 보는 말이라 따로 찾아보았다.

> 수치 탐구 과제는 NLP에서 모델이 수치를 얼마나 잘 이해하고 예측할 수 있는지를 평가하기 위한 특정 과제를 의미한다. 쉽게 말해, 모델이 숫자 데이터를 다루는 능력을 시험하고 강화하는 과제이다.
> 
> 수치 탐구 과제는 모델이 수치적 데이터를 처리하고 예측하는 능력을 평가하는 여러 작업을 포함한다. 
> 이런 과제는 다음과 같은 요소들을 포함할 수 있습니다:
> 
> 1.  **수치 데이터의 이해**:
>     
>     -   모델이 숫자와 그 의미를 이해하는 능력을 평가한다.
>     -   예: 텍스트에서 "3 apples"라는 구문을 이해하고, 숫자 3과 사과를 연결하는 능력.
>     
> 2.  **수치 데이터의 예측**:
>     
>     -   주어진 문맥에서 올바른 숫자를 예측하는 능력을 평가한다.
>     -   예: 레시피 문맥에서 "얼마나 많은 설탕이 필요한가?"라는 질문에 대해 정확한 양을 예측하는 능력.
>     
> 3.  **수치 데이터의 분류**:
>     
>     -   수치 데이터가 주어졌을 때, 이를 적절한 범주로 분류하는 능력을 평가다.
>     -   예: 재료의 양이 주어졌을 때, 이를 부피 또는 무게 단위로 분류하는 능력.

KitchenScale 모델에서의 수치 탐구 과제는 다음의 세 가지 주요 작업으로 나뉘어 진행된다.

 1. **재료 측정 유형 분류 (Ingredient Measurement Type Classification)**:

    
    -   주어진 레시피 문맥과 타겟 재료를 기반으로, 해당 재료의 측정 유형(부피 또는 무게)을 예측하는 단계이다.
    -   모델링: $P(d$ \| $C)$ , 여기서 $d$ 는 측정 유형, $C$ 는 레시피 문맥을 의미한다.
   
  
 2. **재료 측정 단위 분류 (Ingredient Measurement Unit Classification)**:

    
    -   주어진 레시피 문맥, 측정 유형, 타겟 재료를 기반으로, 해당 재료의 측정 단위(cup, Tablespoon 등)를 예측한다.
    -   모델링: $P(u$ \| $C, i_{t\_d})$, 여기서 $u$ 는 측정 단위, $C$ 는 레시피 문맥, $i_{t\_d}$ 는 측정 유형을 의미한다.
   

 3. **재료 양 회귀 (Ingredient Quantity Regression)**:

    
    -   주어진 레시피 문맥, 측정 유형, 타겟 재료를 기반으로, 해당 재료의 정확한 양을 예측하는 단계다.
    -   모델링: $P(q$ \| $C, i_{t\_d})$ , 여기서 $q$ 는 재료의 양, $C$ 는 레시피 문맥, $i_{t\_d}$​ 는 측정 유형을 의미한다.


위의 과정을 통해 레시피 문맥에서 재료의 측정 유형, 단위, 양을 정확하게 예측하는 능력을 개발하고 평가한다. 추가로 타겟 재료 $i_t$ 의 텍스트 요소에 대한 정의도 설명하고 있다.

#### 타겟 재료의 텍스트 요소 정의

1.  **설명 이름(Descriptive Name) ${t\_DescName}$​** : '다진', '슬라이스'와 같은 설명 단어를 포함한 타겟 재료의 이름이다. 설명 단어가 제거된 타겟 재료 이름은 ${t\_Name}$​ 으로 표시된다.
    
2.  **측정 유형(Measurement Type) $i_{t\_d}$** : 측정 방법을 결정하는 재료 속성이다. 이 작업에서는 '부피'와 '무게' 두 가지 레이블을 사용한다.
    
3.  **측정 단위(Measurement Unit) $i_{t\_u}$** : 타겟 재료의 물리적 성분을 표현하는 표준 단위다. 이 작업에서는 '컵', '테이블스푼', '티스푼', '파운드', '온스', '그램', '밀리리터', '핀치', '대시', '킬로그램', '파인트', '쿼트', '드롭', '갤런'의 14가지 단위를 사용한다.
    
4.  **양(Quantity) $i_{t\_q}$​** : 레시피에서 사용되는 타겟 재료의 양을 나타내는 연속 값이다.


이번엔 본 연구에서 사용된 데이터셋을 확인해보자.


##  Dataset

KitchenScale의 재료 양 예측 작업을 위한 데이터셋은 RecipeDB(Batra et al., 2020)와 Reciptor(Li and Zaki, 2020)에서 레시피와 그 속성을 병합하여 생성되었다. 결합된 데이터셋은 총 101,573개의 레시피 정보를 포함하고 있습니다.

**타겟 재료 선택 및 마스킹:**
데이터셋의 각 레시피에서 무작위로 타겟 재료를 선택했다. 그런 다음 이 타겟 재료와 관련된 수치 정보를 예측 작업을 위해 마스킹했다. 이는 RecipeDB의 숫자 값과 단위를 원본 재료 텍스트와 일치시키는 과정을 포함한다.


원본 레시피와 RecipeDB의 차이는 아래의 예시로 확인할 수 있다.

1. **원본 레시피**:

•  사용자가 작성한 레시피로, 자연어 형식으로 되어 있다.

•  예: “2 cups of sugar”, “1/2 teaspoon of salt”, “500g of chicken breast” 등의 형태로 재료와 양, 단위가 적혀 있습니다.

2. **RecipeDB**:

•  원본 레시피의 구조화된 버전입니다.

•  각 레시피의 재료, 양, 단위 등의 정보를 데이터베이스 형식으로 정리하여 저장합니다.

•  예: {“ingredient”: “sugar”, “quantity”: 2, “unit”: “cups”}, {“ingredient”: “salt”, “quantity”: 0.5, “unit”: “teaspoon”}, {“ingredient”: “chicken breast”, “quantity”: 500, “unit”: “g”} 등의 형태로 저장됩니다.


**측정 단위 및 전처리:**
데이터셋에는 다양한 재료의 측정 단위가 포함되어 있었습니다. 이 중 100번 이상 등장하는 74개의 단위를 선택했습니다. 단위는 약어를 표준화하고(예: “pounds”를 “lb”로 변환) 복수형 표현을 단수형으로 표준화하는(예: “tablespoons”를 “tablespoon”으로 변환) 방식으로 정리했습니다. 국제 단위계(SI)에 따라 14개의 측정 단위가 사용되었으며, 두 가지 측정 유형(부피와 무게)으로 분류되었습니다. 부피는 밀리리터(ml), 무게는 그램(g)을 기본 단위로 사용했습니다. 알 수 없거나 비표준 단위가 있는 데이터 인스턴스는 삭제되었습니다.

수치 변환 및 정규화:
타겟 재료의 수치량을 정규화된 부동 소수점 값으로 변환했습니다. 분수로 된 숫자는 소수 값으로 변환했습니다(예: ‘1 1/2’을 1.5로 변환). 이러한 정규화된 값은 재료 양 예측 문제를 회귀 문제로 구성하는 데 사용되었습니다.

최종 데이터셋 구성:
최종 처리된 데이터셋은 98,725개의 데이터 인스턴스를 포함하고 있습니다. 데이터셋의 각 인스턴스는  K = \{d, u, q, c\} 로 정의됩니다. 여기서:

	•	 d 는 측정 유형을 나타냅니다.
	•	 u 는 측정 단위를 나타냅니다.
	•	 q 는 정규화된 수량을 나타냅니다.
	•	 c 는 레시피 맥락을 나타내며, 여기에는 타겟 재료의 설명 이름 ( iDescNamet ), 다른 재료 ( Io ), 태그 ( B ), 제목 ( e ), 서빙 수 ( s )가 포함됩니다.

데이터는 훈련, 검증, 테스트 세트로 각각 8:1:1 비율로 분할되었습니다. 문서의 표 1은 데이터셋에 있는 타겟 재료의 수량에 대한 통계 세부 정보를 제공합니다.

데이터셋 통계 요약:

	•	훈련 인스턴스: 78,984개
	•	검증 인스턴스: 9,873개
	•	테스트 인스턴스: 9,868개
	•	타겟 재료 수량에 대한 통계:
	•	평균: 185.93 (훈련), 187.29 (검증), 182.36 (테스트)
	•	표준 편차: 384.88 (훈련), 383.83 (검증), 385.41 (테스트)
	•	최소: 0.05
	•	최대: 30,283.28 (훈련), 15,141.64 (검증), 11,356.32 (테스트) 

[^2]: Lin, B.Y., Lee, S., Khanna, R., Ren, X., 2020. Birds have four legs?! NumerSense: Probing Numerical Commonsense Knowledge of Pre-Trained Language Models, in: Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP), Association for Computational Linguistics, Online. pp. 6862–6868. URL: https://aclanthology.org/2020. emnlp- main.557, doi:10.18653/v1/2020.emnlp- main.557. Yamane, H., Lin, C.Y., Harada, T., 2020. Measuring numerical common sense: Is a word embedding approach effective? URL: https://openreview.net/ 
forum?id=B1xbTlBKwB Elazar, Y., Mahabal, A., Ramachandran, D., Bedrax-Weiss, T., Roth, D., 2019. 
How large are lions? inducing distributions over quantitative attributes, in: Proceedings of the 57th Annual Meeting of the Association for Computational 
Linguistics, Association for Computational Linguistics, Florence, Italy. pp. 3973–3983. URL: https://aclanthology.org/P19- 1388, doi:10. 18653/v1/P19- 1388.

[^3]: Elazar, Y., Mahabal, A., Ramachandran, D., Bedrax-Weiss, T., Roth, D., 2019. How large are lions? inducing distributions over quantitative attributes, in: 
Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics, Association for Computational Linguistics, Florence, Italy. pp. 3973–3983. URL: https://aclanthology.org/P19- 1388, doi:10.18653/v1/P19- 1388.


[^4]: Spithourakis, G., Riedel, S., 2018. Numeracy for language models: Evaluating and improving their ability to predict numbers, in: Proceedings of the 56th Annual 
Meeting of the Association for Computational Linguistics (Volume 1: Long Papers), pp. 2104–2115
[^5]: Spokoyny, D., Berg-Kirkpatrick, T., 2020. An empirical investigation of contextualized number prediction, in: Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP), Association for Computational Linguistics, Online. URL: https://aclanthology.org/2020.emnlp-main.385, doi:10.18653/v1/2020.emnlp- main.385.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDgxMjczMzk4LC0xNDA3MDIzMTkwLDI2NT
gwMDExNSwxMDgyNjk4ODk2LC0yMDc3NDEwOTk2LDEzMjQwODY0
NDQsLTExNDEzNTY5MjIsLTMzNDQ3NDYxOCwxODUwMTI1NjkyLC
0xNjI1MzMwOTU2LDExNjU5NjM3NTAsLTE0OTE2MjM4OTgsOTU1
NjcyMDcwLDIxMzE1MjAzOCwtMTQzNzExNjQxMCwxNTA4MzEyMT
A2LDUxNTI0OTg1NywxNTA4MzEyMTA2LDE1ODUxMjU1NjAsMjU1
MzIyNDMwXX0=
-->