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

•  **입력과 예측**: 입력 X와 지금까지 예측한 모든 것을 기반으로 다음 토큰 YJ의 확률을 제공합니다.

•  **확률 계산**: 시퀀스 내 모든 확률을 곱하면, 입력 X에 대한 출력 Y의 확률을 계산할 수 있습니다.

•  **본질**: 즉, 이 고급 모델은 단순히 조건부 확률 분포에 불과합니다.


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA3OTE0NTEyMCwtMTMwNjE3MDAwNiw1OD
gyMjEwMCwtMTIwNjQ5MjY3MywtNDc0Mjg5MTk4LC0xMDIxMzE5
NjQ1LDUxNTM2MzMyMiwxMDg5OTU0NzcyXX0=
-->