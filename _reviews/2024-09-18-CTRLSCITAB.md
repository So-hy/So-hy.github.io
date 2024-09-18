---
layout: review_post
title: "[Paper Review] TOWARDS CONTROLLED TABLE-TO-TEXT GENERATION WITH SCIENTIFIC REASONING
author: Zhixin Guo , Jianping Zhou , Jiexing Qi , Mingxuan Yan , Ziwei He , Xinbing Wang , Chenghu Zhou
date: 2024-09-18
---


과학 논문의 표 데이터에서 유용한 정보를 추출하고 이를 논리적으로 표현하는 작업은 과학적 추론이 요구되며, 이는 현재 언어 모델들이 해결하기 어려운 문제로 남아 있다. 논문에서는 이러한 문제를 해결하기 위해 CTRLSciTab이라는 새로운 데이터셋을 구축했으며, 여러 사전 학습된 언어 모델을 평가하고, 추가로 새로운 아키텍처를 제안하여 더 나은 성능을 입증했다.


## **1. Introduction**


-   최근 **사전 학습된 언어 모델(PLM)** 기반 방법들이 텍스트 생성에서 발전을 이루었지만, 과학적 도메인에서는 여전히 어려움이 있음.
    
-   과학적 추론은 체계적이고 증거 기반의 사고 과정으로, 기존 PLM 시스템은 이런 고급 지식을 필요로 하는 설명을 생성하는 데 한계가 있음.
    
-   **기존 방법의 한계**: 기존 테이블-텍스트 생성 과제는 숫자 추론에 집중되어 있으며, 사용자 선호에 맞춘 설명을 생성하지 못하는 경우가 많음.
    
-   **새로운 방법 제안**: **과학적 추론**과 **사용자 선호**를 반영한 **제어된 테이블-텍스트 생성** 과제를 제안하며, 이를 위해 **CTRLSciTab** 데이터셋을 구축함.
    
-   **모델 평가**: PLM 기반 모델들이 과학적 도메인에서 낮은 성능을 보였고, 이를 해결하기 위한 **새로운 벤치마크**를 제안함.


## **2. THE CTRLSCITAB DATASET**


-   **CTRLSciTab 데이터 준비**: 과학 문헌에서 수집된 테이블-설명 쌍을 기반으로 한 데이터셋으로, 원본 논문에서 표와 연결된 문장을 추출하고 이를 과학적 추론에 필요한 도메인 특화 지식으로 구성함. 이 데이터셋에는 하이라이트된 셀이 포함되어 있어 사용자 선호를 반영하는 프롬프트 역할을 함.
-   **데이터셋 구조**: 각 테이블은 평균 52개의 셀과 34개의 단어로 구성된 설명을 포함하며, 전체 셀 중 약 20%는 하이라이트된 셀로, 사용자 선호를 반영함. 또한, 각 테이블에는 평균 20개의 도메인 특화 지식 문장이 제공됨.
-   **주요 목적**: CTRLSciTab은 기존의 테이블-텍스트 생성 작업에서 도메인 특화 지식과 과학적 추론을 추가해 보다 복잡한 설명 생성을 가능하게 함.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NDU0MzE0NzgsLTQ4ODMxNzQzMSwxMT
MwMTcyODcsLTUxOTg2NDU5OCwtMzIyMTMxODkzLDQ4ODkwNzg4
OCwtMjEyOTE0MTgyOF19
-->