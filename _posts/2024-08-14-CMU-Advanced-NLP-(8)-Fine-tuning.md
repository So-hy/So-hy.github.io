---
title: CMU Advanced NLP 2024 (8) Fine-tuning and Instruction Tuning
author: Sohyun
layout: post
---


파인 튜닝, 그리고 인스트럭션 튜닝이 필요한 이유, 그것은 NLP로 다양한 작업을 해결할 수 있기 때문이다. 이게 무슨 말이냐면, 이런 다양한 작업은 서로 다른 다양한 종류의 데이터를 필요로 한다. 

언어 모델링 작업의 경우 주로 텍스트 데이터만을 사용한다. (언어 모델링은 문장에서 다음 단어를 예측하거나 문장을 생성하는 작업을 의미한다.)
이런 작업에서는 단순히 텍스트 데이터만 있으면 된다. 

일부 NLP작업에선 특별히 사람이 데이터를 만들 필요가 없는 경우도 있다. 예를 들어, 기계 번역 작업에서는 사람들이 이미 다른 언어로 번역해놓은 텍스트 데이터를 사용할 수 있다. 이런 데이터를 Naturally occuring data(자연적으로 발생한 데이터) 라고 부를 수 있다.
(기계 번역 데이터가 풍부한 이유는 당연히 사람들이 번역 작업을 계속하기 때문이다.)

또다른 형태의 데이터는 수작업으로 라벨링된 데이터다. 이는 질문-답변(Question Answering)이나 이름 엔디디 인식(Named Entity Recognition)과 같은 작업에 사용되는 데이터다. 이러한 데이터는 자연적으로 발생하지 않기 때문에, 훈련을 위해 수작업으로 데이터를 생성해야 한다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MzEyNjEwNDMsLTEyMTYwOTY5MDcsLT
E1NDg1Mzk0NzgsLTY5OTE0NjUyMSw5NDgzMTI3MzcsNDM2ODM5
MTk5LDQ3MjkzMDk3NCwtMjA1MDcyOTA5MCwtODI3MzQ1NjIxXX
0=
-->