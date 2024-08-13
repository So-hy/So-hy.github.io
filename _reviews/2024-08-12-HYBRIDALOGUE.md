---
layout: review_post
title: "[Paper Review] HYBRIDIALOGUE: An Information-Seeking Dialogue Dataset Grounded on Tabular and Textual Data"
author: Sohyun
date: 2024-08-12
---


해당 논문은 구조화된 테이블 데이터와 비구조화된 텍스트 데이터를 모두 처리할 수 있는 대화 시스템을 개발하기 위해 새로운 데이터셋을 소개한다. 즉, 해당 논문은 대화 시스템의 성능을 향상시키기 위한 효율적인 데이터셋, HYBRIDIALOGUE를 만드는 데 중점을 두고 있다.

## Introduction

반구조화된 테이블 추론을 위한 자연어 추론(NLI) 작업의 훈련 데이터를 구축할 때, 현재 두 가지 주요 접근 방식이 있다. 하나는 **크라우드소싱(Crowdsourcing)** 방식이고, 다른 하나는 **자동화 방법(Automatic Methods)**이다.

크라우드 소싱은 사람이 데이터셋을 생성하는 방식이다. 따라서 비용이 많이 들고 시간이 많이 소요되어 확장성에 한계가 있다. TABFACT 와 INFOTABS와 같은 데이터셋이 있다. 이들은 훨씬 학습하기 좋은 형태의 데이터셋을 제공하기 때문에 유용하지만, 규모에 제한이 있으며 종종 주석 편향과 허위 상관의 문제를 겪는다.

자동화 방법은 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg3MDExNDgxLC0xNzk0OTg5NjY5LDE2Nz
Q3MDM0NzNdfQ==
-->