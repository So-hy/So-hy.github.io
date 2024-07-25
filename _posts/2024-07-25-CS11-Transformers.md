<h1>Transformers</h1>

**<h2>Review Attention</h2>**

어텐션(Attention) 메커니즘이란?
어텐션 메커니즘은 입력 시퀀스의 각 요소가 출력 시퀀스의 각 요소에 얼마나 영향을 미치는지를 계산하는 방법이다. 이 메커니즘은 특히 번역, 텍스트 생성 등의 작업에서 중요한 역할을 한다.

<h3>**Cross Attention**</h3>
Cross Attention은 다른 문장 또는 시퀀스를 어텐션하는 메커니즘이다. 하나의 시퀀스가 키(key) 역할을 하고, 다른 시퀀스가 쿼리(query) 역할을 한다.
쿼리 벡터의 각 요소가 키 벡터의 각 요소에 대해 어텐션을 계산한다.

위 그림에서 입력 문장은 (this, is, an, example) 이고
대상 문장은 (kore, wa, rei, desu) 이다.
각 셀의 색상은 어텐션 스코어를 나타낸다.

> 어텐션 스코어란?
> ⇒ 특정 쿼리와 모든 키 간의 유사도를 나타내는 값이다.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyODU4MjUxNiwxNTA2NDA5MDAwLC0yMD
g4NzQ2NjEyXX0=
-->