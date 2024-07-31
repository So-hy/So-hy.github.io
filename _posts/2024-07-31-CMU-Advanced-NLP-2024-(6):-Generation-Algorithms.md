---
title: CMU Advanced NLP 2024 (6) Generation Algorithms
author: Sohyun
layout: post
---

위 강의에서는 여러 생성 알고리즘(Generation Algorithms)과, 이와 관련된 여러 이론을 설명하고 있다.

교수는 먼저 하나의 모델 $M$을 가정하고 강의를 시작한다.

해당 모델은 70억 개의 매개변수로 이루어져있고, 가장 최신의 아키텍쳐로 사전 학습된 모델이며, 수 조개의 텍스트 토큰으로 사전 학습되었다. 또한, 여러 리더보드에서 최고의 성능을 자랑하는 매우 유명한 모델이라고 말한다.

하지만 모델 M을 자세히 살펴보면, 사실 이 모델은 단순한 조건부 확률 분포이다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTg4MjIxMDAsLTEyMDY0OTI2NzMsLTQ3ND
I4OTE5OCwtMTAyMTMxOTY0NSw1MTUzNjMzMjIsMTA4OTk1NDc3
Ml19
-->