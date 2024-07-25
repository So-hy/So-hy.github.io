<h1>Transformers</h1>

**<h2>Review Attention</h2>**

어텐션(Attention) 메커니즘이란?
어텐션 메커니즘은 입력 시퀀스의 각 요소가 출력 시퀀스의 각 요소에 얼마나 영향을 미치는지를 계산하는 방법이다. 이 메커니즘은 특히 번역, 텍스트 생성 등의 작업에서 중요한 역할을 한다.

<h3>**Cross Attention**</h3>
Cross Attention은 다른 문장 또는 시퀀스를 어텐션하는 메커니즘이다. 하나의 시퀀스가 키(key) 역할을 하고, 다른 시퀀스가 쿼리(query) 역할을 한다.
쿼리 벡터의 각 요소가 키 벡터의 각 요소에 대해 어텐션을 계산한다.

![enter image description here](https://github.com/So-hy/So-hy.github.io/blob/gh-pages/assets/images/blog/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202024-07-25%20204512.png?raw=true)
위 그림에서 입력 문장은 (this, is, an, example) 이고
대상 문장은 (kore, wa, rei, desu) 이다.
각 셀의 색상은 어텐션 스코어를 나타낸다.

> 어텐션 스코어란?
> ⇒ 특정 쿼리와 모든 키 간의 유사도를 나타내는 값이다.

각 셀의 색상은 어텐션 스코어를 나타낸다. 어두운 색상일수록 높은 어텐션 스코어를 의미하며, 밝은 색상일수록 낮은 어텐션 스코어를 의미한다. 예를 들어, "this"와 "kore(これ)" 사이의 셀은 어두운 색상으로 되어 있어, 이 두 단어 사이의 어텐션 스코어가 높음을 나타낸다.

각 열의 하단에 있는 보라색 벡터들은 어텐션 결과이다. 이는 입력 문장의 각 단어에 대해 대상 문장의 단어들로부터 어텐션을 적용한 결과다.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMjM5MzM1MiwxMDI4NTgyNTE2LDE1MD
Y0MDkwMDAsLTIwODg3NDY2MTJdfQ==
-->