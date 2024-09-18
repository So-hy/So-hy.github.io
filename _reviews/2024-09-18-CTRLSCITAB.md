---
layout: review_post
title: "[Paper Review] TOWARDS CONTROLLED TABLE-TO-TEXT GENERATION WITH SCIENTIFIC REASONING
author: Zhixin Guo , Jianping Zhou , Jiexing Qi , Mingxuan Yan , Ziwei He , Xinbing Wang , Chenghu Zhou
date: 2024-09-18
---


과학 논문의 표 데이터에서 유용한 정보를 추출하고 이를 논리적으로 표현하는 작업은 과학적 추론이 요구되며, 이는 현재 언어 모델들이 해결하기 어려운 문제로 남아 있다. 논문에서는 이러한 문제를 해결하기 위해 CTRLSciTab이라는 새로운 데이터셋을 구축했으며, 여러 사전 학습된 언어 모델을 평가하고, 추가로 새로운 아키텍처를 제안하여 더 나은 성능을 입증했다.


## **1. Introduction**


-   **테이블-텍스트 생성 문제**: 최근 **사전 학습된 언어 모델(PLM)** 기반 방법들이 텍스트 생성에서 발전을 이루었지만, 과학적 도메인에서는 여전히 어려움이 있음.
    
-   **과학적 추론의 필요성**: 과학적 추론은 체계적이고 증거 기반의 사고 과정으로, 기존 PLM 시스템은 이런 고급 지식을 필요로 하는 설명을 생성하는 데 한계가 있음.
    
-   **기존 과제의 한계**: 기존 테이블-텍스트 생성 과제는 숫자 추론에 집중되어 있으며, 사용자 선호에 맞춘 설명을 생성하지 못하는 경우가 많음.
    
-   **새로운 과제 제안**: **과학적 추론**과 **사용자 선호**를 반영한 **제어된 테이블-텍스트 생성** 과제를 제안하며, 이를 위해 **CTRLSciTab** 데이터셋을 구축함.
    
-   **모델 평가**: PLM 기반 모델들이 과학적 도메인에서 낮은 성능을 보였고, 이를 해결하기 위한 **새로운 벤치마크**를 제안함.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk2MzE2MzI3NiwtNTE5ODY0NTk4LC0zMj
IxMzE4OTMsNDg4OTA3ODg4LC0yMTI5MTQxODI4XX0=
-->