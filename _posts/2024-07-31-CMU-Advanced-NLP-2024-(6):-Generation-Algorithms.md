---
title: CMU Advanced NLP 2024 (6) Generation Algorithms
author: Sohyun
layout: post
---

위 강의에서는 여러 생성 알고리즘(Generation Algorithms)과, 이와 관련된 여러 이론을 설명하고 있다.

교수는 먼저 하나의 모델 $M$을 가정하고 강의를 시작한다.

해당 모델은 70억 개의 매개변수로 이루어져있고, 가장 최신의 아키텍쳐로 사전 학습된 모델이며, 수 조개의 텍스트 토큰으로 사전 학습되었다. 또한, 여러 리더보드에서 최고의 성능을 자랑하는 매우 유명한 모델이라고 말한다.

하지만 모델 $M$을 자세히 살펴보면, 사실 이 모델은 조건부 확률 분포를 정의한다. 모델이 조건부 확률 분포를 정의한다는 것은, 모델이 특정 조건 $X$가 주어졌을 때 다른 변수 $Y$의 분포를 예측하거나 설명할 수 있다는 의미이다. 모델에 입력 $X$를 넣으면, 관심 있는 시퀀스에 대한 확률을 출력한다. 특히, $M$은 어휘의 모든 토큰에 대한 확률 분포를 제공하여 다음에 어떤 토큰을 출력할지 예측한다. 이러한 의미를 아래의 식이 내포한다.

$$P(Y | X) = \prod_{j=1}^{J} P(y_j | X, y_1, \ldots, y_{j-1})$$

•  **입력과 예측**: 입력 $X$와 지금까지 예측한 모든 것을 기반으로 다음 토큰 $y_j$의 확률을 제공한다.

•  **확률 계산**: 시퀀스 내 모든 확률을 곱하면, 입력 $X$에 대한 출력 $Y$의 확률을 계산할 수 있다.

즉, 이 고급 모델은 단순히 조건부 확률 분포에 불과하다. 그럼에도 불구하고, 이를 활용하여 번역, 요약, 추론 등 다양한 NLP 작업을 수행할 수 있다. 입력 X와 출력 Y의 정의를 바꾸는 것만으로도 다양한 작업에 적용할 수 있다. 아래는 그 예시이다.


![제목 없음](https://github.com/user-attachments/assets/f49d05b4-2125-4730-916c-e4b2280b2ea6){: .responsive-img .align-center}



모델이 단순한 확률 분포로 작동할 때의 좋은 점은 모델이 예측의 확신도(confidence)를 제공할 수 있다는 것이다. 예를 들어 "2 + 2 = ?"라는 입력에 대해 모델이 '4'에 높은 확률을 부여하면, 모델이 매우 확신하고 있음을 알 수 있다. 반면, "교수가 좋아하는 색깔은?" 같은 질문에 대해서는 분포가 평평하게 나타나 확신도가 낮음을 알 수 있다.


![2](https://github.com/user-attachments/assets/2b8033f2-0f0e-4a86-af23-65dfb49dea94){: .responsive-img .align-center}


그러나 이러한 확률 분포 모델은 잘못된 출력을 생성할 수도 있다. 모델은 잘못된 단어에도 0이 아닌 적은 확률을 할당하기 때문에 예측 시, 잘못되거나 이상한 출력을 생성할 가능성이 있다. 이러한 문제는 모델이 훈련된 데이터가 완벽하더라도 발생할 수 있다. 이러한 문제를 할루시네이션(Hallucination)이라고 한다.

이러한 문제를 해결할 방법으로 해당 강의에서는 **샘플링**을 소개한다.


## 샘플링(Sampling for LMs)

모델에서 좋은 출력을 얻기 위한 방법 중 하나가 바로 샘플링이다. 다양한 샘플링 기법들이 있으며, 각 방법은 모델의 확률 분포에서 토큰을 선택하는 방법에 따라 다르다.

첫 번째로 소개하는 것은 단순 샘플링(Ancestral Sampling)이다.

### 단순 샘플링(Ancestral Sampling)

단순 샘플링은 단순히 확률 분포에 따라 토큰을 무작위로 선택하는 방법이다. 확률이 높은 ㅌ
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcyNzI2NDUwMywxNzk0MDU4MjE0LC0xMD
k2NzkyNjA4LC0xOTU4MDY1MjUsMzQ1MDI2ODU5LC0xNzQyOTMx
NTc2LDUzMzk4NTQ1OCwxMDc5MTQ1MTIwLC0xMzA2MTcwMDA2LD
U4ODIyMTAwLC0xMjA2NDkyNjczLC00NzQyODkxOTgsLTEwMjEz
MTk2NDUsNTE1MzYzMzIyLDEwODk5NTQ3NzJdfQ==
-->