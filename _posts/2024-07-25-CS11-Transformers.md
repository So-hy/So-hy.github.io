<h1>Transformers</h1>

**<h2>Review Attention</h2>**

어텐션(Attention) 메커니즘이란?
어텐션 메커니즘은 입력 시퀀스의 각 요소가 출력 시퀀스의 각 요소에 얼마나 영향을 미치는지를 계산하는 방법이다. 이 메커니즘은 특히 번역, 텍스트 생성 등의 작업에서 중요한 역할을 한다.

<h3>**Cross Attention**</h3>
Cross Attention은 다른 문장 또는 시퀀스를 어텐션하는 메커니즘이다. 하나의 시퀀스가 키(key) 역할을 하고, 다른 시퀀스가 쿼리(query) 역할을 한다.
쿼리 벡터의 각 요소가 키 벡터의 각 요소에 대해 어텐션을 계산한다.

![enter image description here](https://lh3.googleusercontent.com/fife/ALs6j_GGySAiqrd1bwODvv3AF_MUPZglq6_lXeVOFm1Tv-_6DdZ9Vudud7EJ5XuqEqcEGZxWjg3chzzmiYGuhsAuyshMHL7okDwfac36Ug-WAuXi6ygX9uI_KTQZ7vfpZynaX7_yDOGfi7OjOVfEZ5a_GE3hzMXcJh4GWPXYeBCNRQk3jVh7RAyHp14S46tKLn5aZ4YCXNqv1oKlcT2xqOJP8Ba7Pwm1NhRlkan5TP3rDp5REVkEOlEo3kXcVL8-bD-YlOv3Qv7wImQ_2uBngyxhLo5Ny0E4Lk87dscM1a6S4StbBDvn5nBAIL_qKBnE1SMYwU-yiRI3qsZUBcVyO6PkoEoE4z6ipfn6IGGVNfWwz1y2B-U5QOsbfCwxaLoRSqQx2k_MFjpc6BVwbUHOTTqdRYJbxYeL-w_QZz3FqIEf58MhcQChS6m6eX-yUj-Bbt1lFchARPHbU4IM3i8uxjFoIl0Ck7puFwNjwFA50cB7BfBkBesTKfReB1l9vEmHJ-z-pyAd7N7cWv5uF4ayFBtKPyDT6hkYlT3NRkVjMrXTcUmZVB-2aHuZvcl6zXEqI8OscZF-nYpug3p_xxCeZcMvftiNWy5sJ53W0FHnpurA3Gn0bM3GaSZ6tAYHj6qdMQayi1WJ4RXPE5GInWmWzxQAbEMdmaja0H8vb5o0_eaDQyI_1W93CA5vXmp164SOFn31TNGoCrrlkC1BierKw9emV4I85fCL_Sj5wUDF6tWPNl_GTkHBZfzxpRjcLEyQMhvMWKmMNAcgbSNpvlcObKfhB36vyEbxj9lTd5VXcap5SWWtmjrKuOYWXtoZPUJpWWXGza2sLQ70SK5VV35sxMjw_WgQDDzfhdUffOyft8e1O0zUSvFlOI7uyUIibSzXThu9jmS2dBCncvUmN7Xkc_0R4HG8z_QK1X-oThTssVkbzMpGL-g0npHa_Aim3dj8WHoiiqOedNLQnFCxiBlMOY0PwY5o4VV0C6eaCDfSnFHbqktzrsPm-IliJcO13Wb0Wm1JIv_yXBBqyOv867WswrB_pmdDsWtEqc4TiKRTidUqoN5Z0q9vlcUivJEN44MBRNtwuvz59WSKUKULTDq1oe-rdu7QgOuiFi9UmWzrM2Z-oYDv479VWBS6Zg1DQ_Saz_Obloz2GT1vmsje34iuZkwsXCce64h2jiR5noBX4fQQJbGFeNspzLqNnJcvTHFaw6cmvzIDuMp2Bt0oegSFGAEtw2_gwfrl2CDm-2nl8Xc6gv2k7S007ihSNzIyUAAmcW5Ib6dXDBbuw7Od8kaBmNbNALiN9EeTX1K_1HcoTZpz02dCNZ07ajAgeJthaWCZDeAgN-HIR-Qfwa5XzRGRWRxYh1i87Tk_RfcVdrjPlVe2B_TmO2hWpp8DrxvQb5GuKBFa8yjIds-5IcQ9OaJb9SoTgJyXCQIuHQXDSc3HQ7XnOXDv6knZnjuRovWDCKKBjYFfeL1qc00oGxrjCb13iELwyqPaKyDIFfZFEYEH5QntJccsc-O18svSFp4RXq-1rYjPOBucF01NJnhr8AeRF4Wlq-R5Dk1-Pc2XFHnLhOn0tPmGTk7YZbwNYziqsAd-5C4gmA-a4KEb4QdT1PEjRmPER2YftjGZy2c_JHMUJpRIhayHCPR7VTZQ6JeXiXBmhmLDgfE78NnlFDSW7eeYJC-QXEQ_u_VzD0c9ch2FYIQPx8vsKRhZ7PY9Xl98wpx901wRb-q0fh4aX_9fkZPq4U5PRvL-UPfzubsQvA=w959-h928)

위 그림에서 입력 문장은 (this, is, an, example) 이고
대상 문장은 (kore, wa, rei, desu) 이다.
각 셀의 색상은 어텐션 스코어를 나타낸다.

> 어텐션 스코어란?
> ⇒ 특정 쿼리와 모든 키 간의 유사도를 나타내는 값이다.

각 셀의 색상은 어텐션 스코어를 나타낸다. 어두운 색상일수록 높은 어텐션 스코어를 의미하며, 밝은 색상일수록 낮은 어텐션 스코어를 의미한다. 예를 들어, "this"와 "kore(これ)" 사이의 셀은 어두운 색상으로 되어 있어, 이 두 단어 사이의 어텐션 스코어가 높음을 나타낸다.

각 열의 하단에 있는 보라색 벡터들은 어텐션 결과이다. 이는 입력 문장의 각 단어에 대해 대상 문장의 단어들로부터 어텐션을 적용한 결과다.

> 크로스 어텐션 과정을 간단하게 말하면 다음과 같다.
> -   **쿼리와 키 설정**:
>     -   쿼리는 입력 문장의 각 단어들 ("this", "is", "an", "example")이다.
>     -   키는 대상 문장의 각 단어들 ("kore", "wa", "rei", "desu")이다.
> -   **어텐션 스코어 계산**:
>     -   쿼리 벡터와 키 벡터 간의 내적(dot product)을 통해 어텐션 스코어를 계산한다.
>     -   각 쿼리 단어에 대해 모든 키 단어와의 유사도를 계산하여 어텐션 스코어 행렬을 만든다.
> -   **스코어 정규화**:
>     -   소프트맥스(Softmax) 함수를 사용하여 어텐션 스코어를 정규화한다. 이는 각 스코어를 확률로 변환하여 모든 스코어의 합이 1이 되도록 한다.
> -   **값 벡터 결합**:
>     -   각 키 단어에 해당하는 값 벡터에 어텐션 스코어를 곱한 후, 이를 합산하여 최종 어텐션 결과 벡터를 만든다.
>     -   이 과정은 입력 문장의 각 단어에 대해 반복된다.

<h3>**Self Attention**</h3>
셀프 어텐션은 크로스 어텐션과는 달리 동일한 시퀀스 내에서 어텐션을 계산한다. 즉, 쿼리와 키가 동일한 시퀀스에 대응되므로, 시퀀스 내의 요소 간의 관계를 모델링할 수 있다.


위 이미지를 보면 입력 문장과 대상 문장이 동일한 시퀀스를 나타냄을 볼 수 있다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NDA5ODI3NjAsLTE5Nzc2MzY2NiwxMD
I4NTgyNTE2LDE1MDY0MDkwMDAsLTIwODg3NDY2MTJdfQ==
-->