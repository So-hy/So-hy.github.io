---
layout: review_post
title: "[Paper Review] KitchenScale: Learning to Predict Ingredient Quantities from Recipe Contexts"
author: Sohyun
date: 2024-07-27
---

해당 논문은 레시피 문맥을 기반으로 목표 재료의 양과 단위를 예측하는 것을 목표로 하는 Kitchen Scale 이라는 언어 모델을 소개한다. 여기서 주목한 것은 양에 대한 예측이다. 실제로 이전의 여러 실험에서는 주로 비율로 성분 조성을 제안하거나 숫자와 단위를 텍스트로 취급하는 방식으로 재료의 양을 다루어서 양을 정확하게 예측하는 데 한계가 있다.

실제로 LLM은 숫자를 다룰 때, 뭔가 나사가 빠진 모습을 보일 때가 많다. 이는 이들을 숫자 보단 텍스트로 취급하고 모델이 학습하기 때문이다.

![스크린샷 2024-07-27 225922](https://github.com/user-attachments/assets/7d0ecb9a-df9b-4560-a551-9183479c0fe2){: .responsive-img .align-center}


위 사진은 ChatGPT 4o 한테 숫자 비교를 시킨 것인데, 이러한 단순 비교에서도 제대로 못하는 모습을 보여준다.

이러한 문제는 레시피를 다룰 때도 나타난다. 이전에 동일하게 ChatGPT 4o 로 브라우니 레시피 생성 후, 이를 저당 레시피로 바꿔달라고 요청을 해보았는데, 설탕을 스테비아로 변환하는 것 까지는 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NzM4MzU3NDddfQ==
-->