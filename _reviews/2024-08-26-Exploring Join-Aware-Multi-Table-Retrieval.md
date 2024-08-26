---
layout: review_post
title: "[Paper Review] Is Table Retrieval a Solved Problem? Exploring Join-Aware Multi-Table Retrieval
author: Sohyun
date: 2024-08-25
---


## Overview

이 논문은 여러 테이블에서 정보를 추출해 질문에 대한 정확한 답을 제공하는 오픈 도메인 질문-응답(QA) 시스템에서 테이블 검색의 문제를 다루고 있다. 기존의 접근법들은 질문에 대한 답이 단일 테이블 또는 질문을 분해하거나 재구성하여 식별된 여러 테이블에 있다고 가정했으나, 이는 충분하지 않다고 주장한다. 여러 테이블을 검색하고, 그 테이블들을 결합하는 계획이 사용자 쿼리로부터 직접적으로 도출되지 않는 경우가 많기 때문에, 검색 단계에서 이 결합 계획을 고려하지 않으면 이후의 추론 및 응답 과정에서 오류가 발생할 수 있다.

따라서 이러한 문제를 해결하기 위해 쿼리와 데이터베이스에 대해 유용한 결합 관계를 검색 단계에서 발견하는 방법을 제안한다. 이 방법은 테이블-쿼리의 관련성뿐만 아니라 테이블-테이블의 관련성을 고려한 새로운 재랭킹(re-ranking) 방법을 사용한다. 논문에서 제안된 방법은 최신 테이블 검색 접근법보다 최대 9.3% 높은 F1 점수와 5.4% 높은 QA 정확도를 달성했다고 보고한다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjk4NzUxODQyLDcwNjE0NzI4MywtMTMwOD
Y0MjYxM119
-->