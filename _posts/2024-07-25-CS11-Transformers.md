## **Review Attention**

어텐션(Attention) 메커니즘이란?
어텐션 메커니즘은 입력 시퀀스의 각 요소가 출력 시퀀스의 각 요소에 얼마나 영향을 미치는지를 계산하는 방법이다. 이 메커니즘은 특히 번역, 텍스트 생성 등의 작업에서 중요한 역할을 한다.

### **Cross Attention**

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

### **Self Attention**

셀프 어텐션은 크로스 어텐션과는 달리 동일한 시퀀스 내에서 어텐션을 계산한다. 즉, 쿼리와 키가 동일한 시퀀스에 대응되므로, 시퀀스 내의 요소 간의 관계를 모델링할 수 있다.


![enter image description here](https://lh3.googleusercontent.com/fife/ALs6j_HfxeKBNlZCVE9erlgsTM0I0l8l0v0McBJl-Rb20vKqVX_pN39_M1GZsVi_9UWQBScuOXOnKVRZZccD_IsZd8Ikb-n5-S0RslDhh9KqjfJQKrUxUxOtW2JWBEUxplo2BTCHPz3TyNRdmF8hY_LanIwTWIoCnsxOX9uz_8f_z-8PzFfgRvA5HfUTwYvynp347KnG5B1qx1BaanJq-lf5vtuSix8SbrotAe7k3vEaiZicp67AalKlHIa4x8E9ikTHis191ox7F8KTxiQ-ViOBdZ4gQ4bmCndy-X6-NbfPar-KuX17EW6dgKk2ofOoR3dkbZS7k10gmFPhtXGB-7z8S4KD5VKX9g7jrE93QzYX3k8YeAFPlk60klD7yz5tCbzTm5B2Kc91nINipKrU3Xsre1Vr_IF5JYAUvfucUxMHWXty8h6IPPTV32jtn1nA2mE6uN_3WIqkuJZAW1yg3YjPhXBdqFBYlb_QeSAPQFAqIown7BysmeLChsKE8XUC06D7I3XCLn139Y1NjJysi2oiQneIX895XKWNS9SJGbIRHRigaLRbg_fNwUuRw24dNFec7_ZTXlsazfX5vjwZwMLM1GePpTXs1HQPuUAYYUYdOXWe_ukGZ40IlH-XYvXljDAz7y-NKkOf0MXQljS-e8sEgnTwMVeMPgNfdcwyv7e-nzMwlCz0KU4hXNzRNks2pzPVltpgElc5XS3zOdNl2vV-fFcFAw41Q2N6LcGFUolNbqQqg6P7kwiEP2DcBCHzb9qFKfkm5ndp5T0YdX6p-G8MOAki3X7-WQMcwpfuLBOPBdmDD2pJLZ5sPt4mXtAj3y5e3sfHzOoLexUH-MgEuhXeK8PITeV_ILvXVUd3tyuFdnKC013xDS7WMzSLWKej-iYhLBwkGxHc1GLiaTB3J2ZEkgEgdw5eanjDpJTKvXwVP-NKa9pYE5G0P8fhbatdQB32UiWa-jwaD0kzc0_1IKoQu0asetBZ9F9Hv1KvB2iHgy4uFbn-3SgvVm7P_x2QyvD1nT8amOxvc-NsofGpTUWTchJfTxLgovOtU1ObY05zFQufKlmCNX1Y7N5ZvH_6x60YIoSTFvYHlAvRRbe6ubE8BWQ21KQqbkXvrONdpCDCK7dpbufP2TEhRkYSp30YQA9H4xX8hagwpeW_NEiDjZHrgdvWgYpGntQEVEsH1zkQ0MBfaxFBhQiKkbIvcz4HPWx8aiAQBE3jh04zGWcJBitivSyfk9MO2_clu1Uqe4ZODu7GxNGfg5EF2gPckhvywO4ylWHhKjQtn4r7QSsSrCae42KWvNJGJdMCH7ggiysSRDqBJG6Dijyl_tXGp3tV-3OfqrHLVpxaLmOMbJ0ZethgH6eZ26Kt6diKFnSpdtamh2syl_RDsCRkkqAFA4MGAcY7UCsqJCAQtWJ5TZRrzmNNEriJaqys0eCiuOSoO93xZ9doLbAkxmYW_NEN1yVWzPaSlWCejax1x5JpzRqwrD4Qt_wFh8Axxk6yxA1veJA5wNVGhaVYPdyeACrSyJZFLNML_bE6YksO5WDBxpyLIs7OslAYSSA9MwhJ-q-4PoOj30FoRx7FtRBIR2tbtMa0Tqp7cNQ67UuqYYeF5WifUAydPcgUludFTbETiDIKplWVYtcS7rKm4mN16mVJJEockjqWzyMGYbRKkdCv__M6fmI2bT5muEVyqJ6ew4a6LO-iiCvFOmqb9qFCpfU_-0ShHeKiPF3kISVSthvaC7zVzpn2nfXWBNB6bttu=w959-h928)

위 그림을 보면 입력 문장과 대상 문장이 동일한 시퀀스를 나타냄을 볼 수 있다.
트랜스포머 기반 모델은 이 두 가지 어텐션 메커니즘을 모두 사용하거나 셀프 어텐션만 사용한다.
(후술할 내용이지만 Decoder-Only Model들은 셀프 어텐션만 사용하고, Encoder-Decoder Model들은 두 가지 어텐션을 모두 사용한다.)


### **Calculating Attention**

![스크린샷 2024-07-25 211412](https://github.com/user-attachments/assets/d4d57ae2-b943-42e8-86e5-d766b139a12c)

위  그림은 크로스 어텐션을 계산하는 과정을 보여준다. 입력 벡터는 쿼리(Query) 벡터를 담당하고, 대상 벡터는 키(Key) 벡터를 담당한다.
쿼리 벡터의 단어 "hate" 에 대해 모든 키 벡터의 단어와 어텐션 가중치 계산을 취하는 모습을 볼 수 있다.(⇒ 이는 쿼리 벡터와 키 벡터 간의 유사도를 계산하는 과정이라고 볼 수 있다.) 그리고 softmax를 취해 normalize 한 값으로 바꾼다.

입력 벡터와 대상 벡터, 그리고 쿼리 벡터와 키 벡터 라는 말이 계속 나오는데, 입력 벡터(**쿼리 벡터**)는 디코더의 입력을 나타내고, 대상 벡터(**키 벡터**)는 인코더의 출력을 나타낸다. 즉, 해당 예시의 모델은 일본어(この映画が嫌い)를 영어(I hate this movie) 로 번역하는 모델임을 의미한다.

![스크린샷 2024-07-25 211425](https://github.com/user-attachments/assets/e4745e50-770d-4daa-bb32-f129592fb326)

그럼 위 그림에서 말하는 값 벡터(Value Vector)는 뭘까? 값 벡터는 키 벡터와 같은 토큰으로부터 생성되는 벡터이다. 하지만 다른 가중치를 통해 생성된다.
만약 단어 별로 토큰화 되었다고 가정했을 때, "kono", "eiga", "ga", "kirai"는 각각 임베딩 벡터 $\mathbf{e}_1, \mathbf{e}_2, \mathbf{e}_3, \mathbf{e}_4$로 변환된다. 키 벡터의 경우 -   각 임베딩 벡터에 키 가중치 행렬 $\mathbf{W}_K$​를 곱하여 생성되고, ( $\mathbf{K}_i = \mathbf{W}_K \cdot \mathbf{e}_i$)이 벡터는 쿼리 벡터와의 유사도를 계산하는데 사용된다. 값 벡터의 경우 각 임베딩 벡터에 값 가중치 행렬 $\mathbf{W}_V$를 곱하여 생성되고, ( $\mathbf{V}_i = \mathbf{W}_V \cdot \mathbf{e}_i$) 이 벡터는 최종 어텐션 결과를 생성하는데 사용된다.
어쨌든, 이전에 normalize 한 값(어텐션 가중치)을 각 값 벡터에 곱한 후, 이를 합산하여 최종 어텐션을 출력한다.  예를 들어, 값 벡터 $V_1, V_2, V_3$​와 어텐션 가중치 $\alpha_1, \alpha_2, \alpha_3$가 있을 때, 최종 출력은 $\alpha_1 V_1 + \alpha_2 V_2 + \alpha_3 V_3​$가 된다.

## **Transformers**
트랜스포머 모델은 "Attention is All You Need" 라는 논문에서 처음 소개 되었다. 트랜스포머는 기본적으로 시퀀스 투 시퀀스(Sequence-to-Sequence) 모델로, 이 모델은 오직 어텐션 메커니즘만을 사용하여 시퀀스를 생성할 수 있음을 보여주었다. 기존의 RNN 기반의 모델도 어텐션을 사용하였으나 단지 Cross-Attention 만 사용하였다고 교수는 설명하고 있다. 트랜스포머는 이러한 Cross-attention 에 더해 RNN이 하는 역할을 Self-Attention 으로 대체한다.
처음에 트랜스포머 모델은 기계 번역에 강한 모습을 보였지만, 지금은 대부분의 task에 있어 강한 모습을 보인다. 또한 트랜스포머 모델은 Matrix multiplications 만으로 구성되어 있기 때문에 빠르다는 강점도 있다. (RNN은 다음 계산을 위해 이전의 계산이 끝나기 까지 기다려야 한다는 병목 현상이 발생하기 때문이다.)


<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAzMzk3OTc1LC0xODE1Njc1MDA2LDQzMD
Y5NDczNywxNTAxNTQ1MzYwLC0yOTMxNDc3NzMsLTk5MTU1NzU5
NSwxMTAxNzc5NTYyLC0xNzMwNTMzMTQ3LDE5ODE4ODUwNTIsLT
Q5MTA4NDA3NCw3ODQ3MTQ1MjksLTU3MzQwMzA2NywxNjY2ODQw
MTMyLC0xNzQwOTgyNzYwLC0xOTc3NjM2NjYsMTAyODU4MjUxNi
wxNTA2NDA5MDAwLC0yMDg4NzQ2NjEyXX0=
-->