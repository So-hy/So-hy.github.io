## **Review Attention**

어텐션(Attention) 메커니즘이란?
어텐션 메커니즘은 입력 시퀀스의 각 요소가 출력 시퀀스의 각 요소에 얼마나 영향을 미치는지를 계산하는 방법이다. 이 메커니즘은 특히 번역, 텍스트 생성 등의 작업에서 중요한 역할을 한다.

### **Cross Attention**

Cross Attention은 다른 문장 또는 시퀀스를 어텐션하는 메커니즘이다. 하나의 시퀀스가 키(key) 역할을 하고, 다른 시퀀스가 쿼리(query) 역할을 한다.
쿼리 벡터의 각 요소가 키 벡터의 각 요소에 대해 어텐션을 계산한다.

![enter image description here](https://lh3.googleusercontent.com/fife/ALs6j_GGySAiqrd1bwODvv3AF_MUPZglq6_lXeVOFm1Tv-_6DdZ9Vudud7EJ5XuqEqcEGZxWjg3chzzmiYGuhsAuyshMHL7okDwfac36Ug-WAuXi6ygX9uI_KTQZ7vfpZynaX7_yDOGfi7OjOVfEZ5a_GE3hzMXcJh4GWPXYeBCNRQk3jVh7RAyHp14S46tKLn5aZ4YCXNqv1oKlcT2xqOJP8Ba7Pwm1NhRlkan5TP3rDp5REVkEOlEo3kXcVL8-bD-YlOv3Qv7wImQ_2uBngyxhLo5Ny0E4Lk87dscM1a6S4StbBDvn5nBAIL_qKBnE1SMYwU-yiRI3qsZUBcVyO6PkoEoE4z6ipfn6IGGVNfWwz1y2B-U5QOsbfCwxaLoRSqQx2k_MFjpc6BVwbUHOTTqdRYJbxYeL-w_QZz3FqIEf58MhcQChS6m6eX-yUj-Bbt1lFchARPHbU4IM3i8uxjFoIl0Ck7puFwNjwFA50cB7BfBkBesTKfReB1l9vEmHJ-z-pyAd7N7cWv5uF4ayFBtKPyDT6hkYlT3NRkVjMrXTcUmZVB-2aHuZvcl6zXEqI8OscZF-nYpug3p_xxCeZcMvftiNWy5sJ53W0FHnpurA3Gn0bM3GaSZ6tAYHj6qdMQayi1WJ4RXPE5GInWmWzxQAbEMdmaja0H8vb5o0_eaDQyI_1W93CA5vXmp164SOFn31TNGoCrrlkC1BierKw9emV4I85fCL_Sj5wUDF6tWPNl_GTkHBZfzxpRjcLEyQMhvMWKmMNAcgbSNpvlcObKfhB36vyEbxj9lTd5VXcap5SWWtmjrKuOYWXtoZPUJpWWXGza2sLQ70SK5VV35sxMjw_WgQDDzfhdUffOyft8e1O0zUSvFlOI7uyUIibSzXThu9jmS2dBCncvUmN7Xkc_0R4HG8z_QK1X-oThTssVkbzMpGL-g0npHa_Aim3dj8WHoiiqOedNLQnFCxiBlMOY0PwY5o4VV0C6eaCDfSnFHbqktzrsPm-IliJcO13Wb0Wm1JIv_yXBBqyOv867WswrB_pmdDsWtEqc4TiKRTidUqoN5Z0q9vlcUivJEN44MBRNtwuvz59WSKUKULTDq1oe-rdu7QgOuiFi9UmWzrM2Z-oYDv479VWBS6Zg1DQ_Saz_Obloz2GT1vmsje34iuZkwsXCce64h2jiR5noBX4fQQJbGFeNspzLqNnJcvTHFaw6cmvzIDuMp2Bt0oegSFGAEtw2_gwfrl2CDm-2nl8Xc6gv2k7S007ihSNzIyUAAmcW5Ib6dXDBbuw7Od8kaBmNbNALiN9EeTX1K_1HcoTZpz02dCNZ07ajAgeJthaWCZDeAgN-HIR-Qfwa5XzRGRWRxYh1i87Tk_RfcVdrjPlVe2B_TmO2hWpp8DrxvQb5GuKBFa8yjIds-5IcQ9OaJb9SoTgJyXCQIuHQXDSc3HQ7XnOXDv6knZnjuRovWDCKKBjYFfeL1qc00oGxrjCb13iELwyqPaKyDIFfZFEYEH5QntJccsc-O18svSFp4RXq-1rYjPOBucF01NJnhr8AeRF4Wlq-R5Dk1-Pc2XFHnLhOn0tPmGTk7YZbwNYziqsAd-5C4gmA-a4KEb4QdT1PEjRmPER2YftjGZy2c_JHMUJpRIhayHCPR7VTZQ6JeXiXBmhmLDgfE78NnlFDSW7eeYJC-QXEQ_u_VzD0c9ch2FYIQPx8vsKRhZ7PY9Xl98wpx901wRb-q0fh4aX_9fkZPq4U5PRvL-UPfzubsQvA=w959-h928){: .responsive-img .align-center}

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


![enter image description here](https://lh3.googleusercontent.com/fife/ALs6j_HfxeKBNlZCVE9erlgsTM0I0l8l0v0McBJl-Rb20vKqVX_pN39_M1GZsVi_9UWQBScuOXOnKVRZZccD_IsZd8Ikb-n5-S0RslDhh9KqjfJQKrUxUxOtW2JWBEUxplo2BTCHPz3TyNRdmF8hY_LanIwTWIoCnsxOX9uz_8f_z-8PzFfgRvA5HfUTwYvynp347KnG5B1qx1BaanJq-lf5vtuSix8SbrotAe7k3vEaiZicp67AalKlHIa4x8E9ikTHis191ox7F8KTxiQ-ViOBdZ4gQ4bmCndy-X6-NbfPar-KuX17EW6dgKk2ofOoR3dkbZS7k10gmFPhtXGB-7z8S4KD5VKX9g7jrE93QzYX3k8YeAFPlk60klD7yz5tCbzTm5B2Kc91nINipKrU3Xsre1Vr_IF5JYAUvfucUxMHWXty8h6IPPTV32jtn1nA2mE6uN_3WIqkuJZAW1yg3YjPhXBdqFBYlb_QeSAPQFAqIown7BysmeLChsKE8XUC06D7I3XCLn139Y1NjJysi2oiQneIX895XKWNS9SJGbIRHRigaLRbg_fNwUuRw24dNFec7_ZTXlsazfX5vjwZwMLM1GePpTXs1HQPuUAYYUYdOXWe_ukGZ40IlH-XYvXljDAz7y-NKkOf0MXQljS-e8sEgnTwMVeMPgNfdcwyv7e-nzMwlCz0KU4hXNzRNks2pzPVltpgElc5XS3zOdNl2vV-fFcFAw41Q2N6LcGFUolNbqQqg6P7kwiEP2DcBCHzb9qFKfkm5ndp5T0YdX6p-G8MOAki3X7-WQMcwpfuLBOPBdmDD2pJLZ5sPt4mXtAj3y5e3sfHzOoLexUH-MgEuhXeK8PITeV_ILvXVUd3tyuFdnKC013xDS7WMzSLWKej-iYhLBwkGxHc1GLiaTB3J2ZEkgEgdw5eanjDpJTKvXwVP-NKa9pYE5G0P8fhbatdQB32UiWa-jwaD0kzc0_1IKoQu0asetBZ9F9Hv1KvB2iHgy4uFbn-3SgvVm7P_x2QyvD1nT8amOxvc-NsofGpTUWTchJfTxLgovOtU1ObY05zFQufKlmCNX1Y7N5ZvH_6x60YIoSTFvYHlAvRRbe6ubE8BWQ21KQqbkXvrONdpCDCK7dpbufP2TEhRkYSp30YQA9H4xX8hagwpeW_NEiDjZHrgdvWgYpGntQEVEsH1zkQ0MBfaxFBhQiKkbIvcz4HPWx8aiAQBE3jh04zGWcJBitivSyfk9MO2_clu1Uqe4ZODu7GxNGfg5EF2gPckhvywO4ylWHhKjQtn4r7QSsSrCae42KWvNJGJdMCH7ggiysSRDqBJG6Dijyl_tXGp3tV-3OfqrHLVpxaLmOMbJ0ZethgH6eZ26Kt6diKFnSpdtamh2syl_RDsCRkkqAFA4MGAcY7UCsqJCAQtWJ5TZRrzmNNEriJaqys0eCiuOSoO93xZ9doLbAkxmYW_NEN1yVWzPaSlWCejax1x5JpzRqwrD4Qt_wFh8Axxk6yxA1veJA5wNVGhaVYPdyeACrSyJZFLNML_bE6YksO5WDBxpyLIs7OslAYSSA9MwhJ-q-4PoOj30FoRx7FtRBIR2tbtMa0Tqp7cNQ67UuqYYeF5WifUAydPcgUludFTbETiDIKplWVYtcS7rKm4mN16mVJJEockjqWzyMGYbRKkdCv__M6fmI2bT5muEVyqJ6ew4a6LO-iiCvFOmqb9qFCpfU_-0ShHeKiPF3kISVSthvaC7zVzpn2nfXWBNB6bttu=w959-h928){: .responsive-img .align-center}

위 그림을 보면 입력 문장과 대상 문장이 동일한 시퀀스를 나타냄을 볼 수 있다.
트랜스포머 기반 모델은 이 두 가지 어텐션 메커니즘을 모두 사용하거나 셀프 어텐션만 사용한다.
(후술할 내용이지만 Decoder-Only Model들은 셀프 어텐션만 사용하고, Encoder-Decoder Model들은 두 가지 어텐션을 모두 사용한다.)


### **Calculating Attention**

![스크린샷 2024-07-25 211412](https://github.com/user-attachments/assets/d4d57ae2-b943-42e8-86e5-d766b139a12c){: .responsive-img .align-center}

위  그림은 크로스 어텐션을 계산하는 과정을 보여준다. 입력 벡터는 쿼리(Query) 벡터를 담당하고, 대상 벡터는 키(Key) 벡터를 담당한다.
쿼리 벡터의 단어 "hate" 에 대해 모든 키 벡터의 단어와 어텐션 가중치 계산을 취하는 모습을 볼 수 있다.(⇒ 이는 쿼리 벡터와 키 벡터 간의 유사도를 계산하는 과정이라고 볼 수 있다.) 그리고 softmax를 취해 normalize 한 값으로 바꾼다.

입력 벡터와 대상 벡터, 그리고 쿼리 벡터와 키 벡터 라는 말이 계속 나오는데, 입력 벡터(**쿼리 벡터**)는 디코더의 입력을 나타내고, 대상 벡터(**키 벡터**)는 인코더의 출력을 나타낸다. 즉, 해당 예시의 모델은 일본어(この映画が嫌い)를 영어(I hate this movie) 로 번역하는 모델임을 의미한다.

![스크린샷 2024-07-25 211425](https://github.com/user-attachments/assets/e4745e50-770d-4daa-bb32-f129592fb326){: .responsive-img .align-center}

그럼 위 그림에서 말하는 값 벡터(Value Vector)는 뭘까? 값 벡터는 키 벡터와 같은 토큰으로부터 생성되는 벡터이다. 하지만 다른 가중치를 통해 생성된다.

만약 단어 별로 토큰화 되었다고 가정했을 때, "kono", "eiga", "ga", "kirai"는 각각 임베딩 벡터 $\mathbf{e}_1, \mathbf{e}_2, \mathbf{e}_3, \mathbf{e}_4$로 변환된다. 키 벡터의 경우 -   각 임베딩 벡터에 키 가중치 행렬 $\mathbf{W}_K$​를 곱하여 생성되고, ( $\mathbf{K}_i = \mathbf{W}_K \cdot \mathbf{e}_i$)이 벡터는 쿼리 벡터와의 유사도를 계산하는데 사용된다. 값 벡터의 경우 각 임베딩 벡터에 값 가중치 행렬 $\mathbf{W}_V$를 곱하여 생성되고, ( $\mathbf{V}_i = \mathbf{W}_V \cdot \mathbf{e}_i$) 이 벡터는 최종 어텐션 결과를 생성하는데 사용된다.

어쨌든, 이전에 normalize 한 값(어텐션 가중치)을 각 값 벡터에 곱한 후, 이를 합산하여 최종 어텐션을 출력한다.  예를 들어, 값 벡터 $V_1, V_2, V_3$​와 어텐션 가중치 $\alpha_1, \alpha_2, \alpha_3$가 있을 때, 최종 출력은 $\alpha_1 V_1 + \alpha_2 V_2 + \alpha_3 V_3​$가 된다.

## **Transformers**
트랜스포머 모델은 "Attention is All You Need" 라는 논문에서 처음 소개 되었다. 트랜스포머는 기본적으로 시퀀스 투 시퀀스(Sequence-to-Sequence) 모델로, 이 모델은 오직 어텐션 메커니즘만을 사용하여 시퀀스를 생성할 수 있음을 보여주었다. 기존의 RNN 기반의 모델도 어텐션을 사용하였으나 단지 Cross-Attention 만 사용하였다고 교수는 설명하고 있다. 트랜스포머는 이러한 Cross-attention 에 더해 RNN이 하는 역할을 Self-Attention 으로 대체한다.

처음에 트랜스포머 모델은 기계 번역에 강한 모습을 보였지만, 지금은 대부분의 task에 있어 강한 모습을 보인다. 또한 트랜스포머 모델은 Matrix multiplications 만으로 구성되어 있기 때문에 빠르다는 강점도 있다. (RNN은 다음 계산을 위해 이전의 계산이 끝나기 까지 기다려야 한다는 병목 현상이 발생하기 때문이다.)

### **Two Types of Transformers**
트랜스포머는 크게 두 종류가 있다.

![스크린샷 2024-07-25 211449](https://github.com/user-attachments/assets/5649112f-9211-4b6b-8da1-c0e1a1808698){: .responsive-img .align-center}

하나는 인코더-디코더로 이루어진 모델이고(T5, MBART), 다른 하나는 디코더로만 이루어진 모델이다(GPT, LLaMa).

Feed Forward 의 경우 어텐션 메커니즘에 의해 계산된 다양한 특징들을 결합하여 새로운 특징을 추출하는 역할을 하고, Multi-head attention 블록의 경우 이전에 말한 어텐션에 대한 작업을 수행한다. (자세한 내용은 뒤에서 다룬다.) 디코더만 있는 모델은 크게 이 두 가지 부분만 있고 인코더-디코더 모델의 경우, Masked Multi-Attention 이라는 블록도 있다. (RNN의 어떤 점을 대체한다고 하는데, 아마 RNN이 이전의 결과를 토대로 현재의 결과를 계산하여야 하는 것과 같이 시퀀스 "A, B, C" 를 처리한다고 가정할 때, 만약 현재 시퀀스에서 'A' 부분을 처리하고 있다면 뒤에 있는 ", B, C" 를 보지 못하게 한다는 뜻인 것 같다.) 그리고 Multi-Head Attention 레이어가 하나 더 있는데 이는 Cross-Attention 을 담당한다.

**인코더-디코더 모델**은 입력과 출력이 명확하게 구분되는 작업에 적합하며, 반면 **디코더 전용 모델**은 단일 모듈(디코더)만 사용하며, 입력과 출력의 구분이 모호한 작업에 적합하다.(ChatGpt 와 같이 입력과 출력이 명확히 정해지지 않는 느낌이다.) 옆에 작게 적힌 Nx 는 해당 인코더, 디코더 레이어가 몇 겹 존재하는지에 대한 것이다.

### **Core Transformer Concepts**

 - Positional Encodings  
 - Multi-headed Attention 
 - Masked Attention 
 - Residual + layer normalization
 - Feed-forward layer

이러한 친구들이 트랜스포머 모델의 핵심이다.
우선 디코더를 보면서 차근차근 살펴보자.

![스크린샷 2024-07-25 211459](https://github.com/user-attachments/assets/b58a23c8-f900-4c6c-825b-304ca27c4bad){: .responsive-img .align-center}

Inputs, 즉 입력은 보통 subwords 단위로 쪼개진다. 그리고 이렇게 쪼개진 subwords를 Dense Vector Space로 Embedding 한다. 

그 다음으로 다룰 것은 Multi-head Attention이다.

## **Multi-head Attention**
![스크린샷 2024-07-25 211521](https://github.com/user-attachments/assets/3a75f06b-8f63-4b91-b523-384f748093bc){: .responsive-img .align-center}

Multi-Head Attention 의 기저에 깔린 기본 개념은 문장이나 시퀀스의 다른 부분의 정보는 서로 다르게 유용할 수 있다는 것이다. 이게 무슨 말일까..? 를 해석해보자면 문장이나 시퀀스 내의 각 단어 또는 요소가 서로 다른 역할과 의미를 가지고 있으며, 이 각각의 정보가 특정 문맥에서 다른 방식으로 유용할 수 있다는 것을 의미한다. 예를 들어..

-   **문법적 역할**: 어떤 단어는 문법적으로 중요한 정보를 제공할 수 있다. 예를 들어, 주어와 동사는 문장 구조를 이해하는 데 중요한 역할을 한다.
-   **의미적 정보**: 어떤 단어는 문장의 의미를 이해하는 데 중요한 정보를 제공할 수 있다. 예를 들어, "run"이라는 단어는 "달리다"라는 물리적 의미뿐만 아니라 "사업을 운영하다"라는 비유적 의미도 가질 수 있다. (Lexical Sementics)
-   **문맥적 중요성**: 어떤 단어는 특정 문맥에서 더 중요한 정보를 제공할 수 있다. 예를 들어, "bank"라는 단어는 문맥에 따라 "강둑" 또는 "은행"을 의미할 수 있다.

즉, 문장에서 단어의 의미를 명확히 하기 위해 사용하는 정보가 다를 수 있다는 것이다! (예를 들어 영어 문장을 보고 특정 단어가 무슨 뜻인지 맞추기 위해 그 문장에서 각 단어를 보는 것 보다 문장 전체를 볼 필요가 있다는 것.) 문법적인 관계를 보는 경우엔 영어에서는 근처의 context 를 참고하면 되긴 하지만, 의미적 정보를 파악하기 위해서는 좀 더 넓은 범위의 context를 참고해야 한다.

단순히 단일 헤드 어텐션(Single-Head Attention)는 시퀀스의 특정 한 단어에 대해 다른 요소들과의 중요도가 어떤지를 측정하는 식으로 진행되는데 이때문에 모든 부분에 동시에 주의를 기울일 수 없어 특정 부분에 집중하게 되는 문제가 생긴다. 따라서 단일 헤드 어텐션은 중요한 정보를 선택할 때 "하드 디시전"을 내려야 하는 경우, 즉, 어떤 정보를 선택하고 어떤 정보를 무시할지 명확하게 결정해야 하는 경우가 발생한다. 이러한 이유 때문에 Multi-head Attention을 쓰는 것이다.

그래서 Multi-Head Attention은 어떻게 작동하는 것일까? 아래의 그림을 보자.

![스크린샷 2024-07-25 211603](https://github.com/user-attachments/assets/6f14e61b-029c-4262-a490-ec863d3a78e5){: .responsive-img .align-center}

이 그림은 Attention is all you need 논문에 나온 것과 조금 다르긴 하지만 실제로 pytorch를 통해 구현할 때 어떤 식으로 되는 지에 가깝다. Q, K, V는 각각 Query Vector, Key Vector, Value Vector 을 의미한다.

Q벡터의 경우 열이 3개고, 나머지는 열이 4개인데, 이렇게 쿼리 벡터의 수와 키/값 벡터의 수는 충분히 다를 수 있다고 한다.(키/값 벡터의 개수는 무조건 같아야 한다.) 이런 경우는 Cross-Attention 시 발생할 수 있는데, Cross-Attention은 이전에 말한 것과 같이 디코더의 쿼리 벡터를 입력 시퀀스의 키와 값 벡터에 매핑하여 어텐션 스코어를 계산하는 과정이다. 이 때, 디코더가 현재 시점까지의 출력 시퀀스에 대한 정보를 기반으로, 전체 입력 시퀀스의 정보를 활용하여 다음 단어를 예측하기 때문에, 디코더가 현재 생성 중인 출력 시퀀스의 일부에 대해서만 쿼리 벡터를 생성할 수 있고, 이 때문에 개수가 달라질 수 있다는 것! (디코더의 출력 시퀀스의 길이와 관련이 있다는 뜻) 하지만 Self-Attention 의 경우, 동일한 시퀀스에 대해서 계산되는 것이기에, 당연 개수가 같아야 한다. (※ 행은 차원, 열은 시퀀스의 길이를 나타낸다고 보면 된다.)

어쨌든, 각각의 벡터를 각각의 가중치 행렬과 곱셈 연산을 한다. 이 곱하는 과정이 위의 그림에서 Attention 괄호 안에 있는 친구들을 의미한다. 이렇게 곱한 후, 얘들을 분할 및 재구성하는 과정을 거친다. 말 그대로 Multi-head attention 이니까 여러 헤드에 이 값을 쪼개서 넣는 것이다. 그림에서는 두 개로 쪼갰는데 이 말은 Attention Head 가 두 개 있다는 것! 위의 식은 분할 후, Matrix Multiply 를 진행했지만 그림은 반대의 순서다. 이는 실제로는 식처럼 하는게 아니라 큰 곱셈을 먼저 해버리고 쪼개는게 쪼개서 잔잔한 곱셈을 여러번 하는 것보다 효율적이기 때문이라고 한다. 그래서 실제로 구현할 때는 그림대로 하는게 일반적이라고 한다.

이렇게 분할된 각각의 헤드에 대해 어텐션 메커니즘을 실행한다. 이 어텐션 메커니즘은 한번에 병렬적으로 처리하게 된다. 그리고 결과를 출력하게 된다. 당연히 결과의 열은 Q의 열과 같게 된다. (쿼리에 대해 계산하기 때문..) 그리고 아까 쪼겠던 것들을 다시 연결함으로써 최종적으로 결과가 도출된다. 각 어텐션 헤드는 독립적으로 쿼리, 키, 값 벡터를 사용하여 어텐션 가중치를 계산하고, 이 과정에서 각 헤드는 입력 시퀀스의 다른 부분에 주의를 기울이게 되기 때문에 더 많은 문맥 정보를 이해할 수 있게 되는 것이다!

위의 과정을 코드로 나타내면 아래와 같다.

    def forward(self, query, key, value, mask=None): 
            nbatches = query.size(0)
    # 1) Do all the linear projections
            query = self.W_q(query) 
            key = self.W_k(key) 
            value = self.W_v(value)
    # 2) Reshape to get h heads
            query = query.view(nbatches, -1, self.heads, self.d_k).transpose(1, 2) 
            key = key.view(nbatches, -1, self.heads, self.d_k).transpose(1, 2) 
            value = value.view(nbatches, -1, self.heads, self.d_k).transpose(1, 2)
    # 3) Apply attention on all the projected vectors in batch.
            x, self.attn = attention(query, key, value)
    # 4) "Concat" using a view and apply a final linear.
            x = (
                x.transpose(1, 2) 
                .contiguous()
                .view(nbatches, -1, self.h * self.d_k) 
            )
    return self.W_o(x)


코드의 마지막을 보면 최종 결과에 W_o 를 적용하는 것을 볼 수 있다. 이는 식에도 표현되어 있는데 이 $\mathbf{W_O}$ 는 최종 선형 레이어로, 영상에서는 나오지 않았지만, 합산된 정보를 일관된 표현으로 결합/변환 하거나, 혹은 차원을 축소하는 등의 역할을 한다고 한다.

![스크린샷 2024-07-26 020605](https://github.com/user-attachments/assets/d98b1ef3-993d-4ebe-a3fe-6de75095e1d3){: .responsive-img .align-center}

이 그림은 Multi-Head Attention 을 했을 때, 어텐션이 어떻게 적용되는가를 보여주는 예시이다. making 이라는 단어에 대한 각 어텐션 헤드가 입력 시퀀스의 어느 부분에 주의를 기울이는지 확인할 수 있다. 

## **Positional Encoding**


트랜스포머 모델은 순수하게 Attention에 집중을 한다. 그러다보니 동일한 단어(또는 subword)가 문장 내에 다른 위치에 있을 때, 이를 구별할 수가 없고 문장 내 어느 위치에 있던 동일한 Attention 값을 가지게 된다. 왜냐하면 해당 단어에 대한 벡터는 Identical 하기 때문이다. 즉, 위치에 대한 정보가 없다는 것이다.

이러한 문제를 해결하기 위해 RNN 같이 위치 정보에 민감한 모델을 쓰면 되지만 Transformer 논문에서는 RNN을 쓰지 않았다. 대신 이를 해결하기 위해 Positional Encoding 이라는 기법을 도입했다.

Positional Encoding은 단어의 위치에 기반한 다른 임베딩을 입력 임베딩에 더하는 것이다.

![스크린샷 2024-07-26 035417](https://github.com/user-attachments/assets/50797d4a-cd4a-42a1-a171-2e36e5144d1d){: .responsive-img .align-center}

예를 들어 위 문장 두 개에서 서로 다른 위치의 big에 대해 앞쪽의 big의 임베딩에는 Wpos2를 더해주고, 뒤쪽의 big 임베딩에는 Wpos6를 더해줌으로써 위치 정보를 부여하는 것이다.

### **Sinusoidal Encoding**

 
 이러한 Positional Encoding을 구현하기 위한 방법에는 여러가지가 있다. 그 중, 트랜스포머 논문에서 사용한 기법은 Sinusoidal Encoding, 즉 $sin$을 활용한 인코딩이다.

방식은 아래와 같다.

![스크린샷 2024-07-26 040014](https://github.com/user-attachments/assets/0ab4598f-cdaf-4bdc-90f6-889c18dbbdee){: .responsive-img .align-center}

이 수식은 각 위치 $t$에 대해 $sin$ 및 $cos$ 값을 계산하여, 단어 위치를 고유한 벡터로 인코딩한다. $Pt(i)​$ 는 $t$ 위치에 있는 단어의 $i$번째 차원의 Positional Encoding 값을 의미하며, 짝수 차원에는 $sin$, 그리고 홀수 차원에는 $cos$을 통해 값을 계산한다. $\omega_k = \frac{1}{10000^{2k/d}}$ 에서 $\omega_k$는 주파수, $d$는 인코딩 벡터의 차원 수를 나타낸다. 이 임베딩은 아래의 그림과 같은 모양으로 보이는데 세로축은 sequence 내의 위치, 가로축은 임베딩 크기를 의미한다. 

대체 왜 이러한 방식을 왜 사용했을까? 이건 두 임베딩을 곱했을 때의 특징 때문이다.

일단 특정 단어 위치 $t$ 에 대해 Positional Encoding 벡터는 아래와 같이 만들어 질 것이다.

$Pt​=[sin(ω0​⋅t),cos(ω0​⋅t),sin(ω1​⋅t),cos(ω1​⋅t),...]$

그리고 이 인코딩 벡터를 다른 위치의 인코딩 벡터인 $P_{t'}$와 내적을 하여 유사성을 계산하고 그 값을 그림으로 나타내면 오른쪽 그림과 같이 나온다. 해당 히트맵의 각 셀은 두 위치 간의 유사성 값을 나타내고, 색상이 짙을 수록 높은 유사성을 나타내는데, 보이는 것과 같이 대각선은 항상 높은 유사성을 가지는 것을 볼 수 있다.(자기 자신과의 비교이기 때문)​ 그리고 두 위치가 가까울 수록 값이 커지는 것을 볼 수 있다. 이 값이 어텐션 메커니즘에 영향(Bias)를 주는데, 이 값이 커질수록 당연히 어텐션 메커니즘에서 가중치를 조정하는데 더 큰 영향을 주게 된다. 즉, 두 위치가 가까울수록 어텐션 값(가중치)이 커지게 되고, 이로 인해 어텐션 메커니즘이 문맥을 이해할 때, 가까운 단어들 간의 관계를 더 잘 반영하게 하는 것이다. 거기에 더해 대각선 상의 셀은 위치 인코딩 벡터가 자기 자신과의 상관 관계를 나타내며, 이는 각 위치 인코딩 벡터가 고유함을 시각적으로 보여준다. 이러한 이유로 이런 function을 쓰게 된 것이다.

### **Learned Encoding**


Learned Encoding은 위치 인코딩 값을 학습 가능한 파라미터로 설정하여, 모델이 학습 과정에서 최적의 위치 인코딩 값을 찾아내도록 하는 방법이다. 따라서 앞의 Sinusoidal Encoding 보다 쉽고, 모델이 학습 데이터에 맞춰 최적의 위치 인코딩 값을 찾을 수 있어, 데이터에 특화된 인코딩 값을 사용할 수 있는 유연성을 가지고 있다. 하지만 큰 단점이 있으니 학습 데이터의 범위를 넘어서는 값에 대해 일반화하는 것이 불가능하다. 즉, 모델이 학습한 시퀀스 길이보다 더 긴 시퀀스가 입력되면, 해당 위치에 대한 인코딩 값을 학습한 적이 없기 때문에 적절히 처리할 수 없다. 이는 모델이 더 긴 시퀀스를 잘 이해하지 못하게 만들 수 있다. 하지만 Sinusoidal Encoding의 경우 단순히 $k$ 값을 크게 해주면 된다. 그래서 모델이 학습하지 않은 더 긴 시퀀스에도 일반화할 수 있다. 이론적으로는 그렇지만 경험적으로 이것도 긴 시퀀스에 대해 그렇게 엄청 일반화를 잘 하지는 못하는 듯하다.


### **Absolute vs. Relative Encodings**


Absolute Positional Encoding은 입력에 인코딩 값을 추가하여 상대적 위치 정보도 캡처할 수 있기를 기대하는 방식이다. 각 단어의 위치를 절대적인 값으로 인코딩합니다. 즉, 문장 내에서 단어가 몇 번째 위치에 있는지를 나타내는 값을 사용하며, 가까운 친구들일수록 더 강한 어텐션을 적용하기 때문에 거리가 먼 단어의 경우 상대적으로 어텐션이 약해져 전체적으로 어텐션을 주지 못한다는 문제가 있다.
(예: 첫 번째 단어는 위치 1, 두 번째 단어는 위치 2 등.)
Relative Positional Encoding의 경우 각 단어의 위치를 절대적인 값으로 인코딩하는 대신, 각 단어 간의 상대적인 위치 정보를 인코딩한다. 즉, 특정 단어가 다른 단어와 얼마나 떨어져 있는지를 인코딩하는 방식이다.
(예: key embedding 은 query embedding 으로 부터 5칸 떨어져있다.) Relative Positional Encoding은 단어 간의 거리(상대적 위치)를 직접적으로 인코딩하여, 문장 내 단어들의 상대적 위치 정보를 명시적으로 포함한다. 이러한 이유 덕분에 문장의 길이가 달라져도(더 길거나 짧아져도) 상대적 위치 정보를 유지할 수 있어, 모델이 더 유연하게 문장을 이해할 수 있도록 돕는다. 또한 이런 거리 정보가 있기 때문에 시퀀스에서 멀리 떨어진 두 단어에 대해서도 충분히 어텐션을 취할 수 있다. 하지만 두 가지 문제점이 있는데 **Learnable Parameter**의 추가와 **Computational Cost**의 증가이다.

Relative Positional Encoding은 각 단어 쌍의 상대적 위치를 학습 가능한 파라미터로 인코딩한다. 이는 모델이 학습 과정에서 최적의 상대적 위치 인코딩 값을 찾아내도록 한다. 이 과정에서 각 단어 쌍마다 상대적 위치를 나타내는 파라미터가 추가된다. 특히 긴 시퀀스의 경우 단어 쌍의 수가 기하급수적으로 증가하므로, 필요한 파라미터의 수가 매우 많아질 수 있다. 이로 인해 모델의 복잡도를 증가시키고, 학습 과정에서 더 많은 메모리와 계산 자원이 필요하게 된다. 학습할 때마다 어텐션 매트릭스에 위치 파라미터 또한 계속 업데이트 해주어야 하며, 이 과정을 모든 레이어에 적용해야 한다.


### **Rotary Positional Encodings**


Rotary Positional Encoding(RoPE)의 경우 Absolute Positional Encoding과 Relative Positional Encoding의 결합하여 사용함으로써 두 인코딩의 장점을 모두 취하는 방식이다.

RoPE의 핵심 아이디어는 임베딩의 내적이 상대적인 위치의 함수가 되도록 하는 것이다. 이를 식으로 표현하면 아래와 같다. 

$$f_q(x_m, m) \cdot f_k(x_n, n) = g(x_m, x_n, m - n)$$

여기서 $f_q$와 $f_k$는 각각 쿼리와 키 임베딩 함수를 나타내고, $x_m$과 $x_n$은 입력 벡터, $m$과 $n$은 위치를 나타낸다. $g$는 상대 위치의 함수이다. 이렇게 함으로써 Absolute Position에 대한 정보는 잃게 되고, 이것으로부터 Relative Position에 대한 정보를 얻게 된다. 뭔가 단순해 보이는 느낌이지만 기본적으로 오직 상대 위치에만 의존하도록 해야 하기 때문에 절대 위치를 복구할 수 없는 방식이 필요하다고 한다. RoPE가 절대 위치를 복구할 수 없도록 설계된 이유는, 모델이 상대 위치 정보에만 의존하게 하여 새로운 입력 데이터에 대해 더 잘 일반화할 수 있도록 하기 위함이다.

어쨌든 이런 것을 구현하기 위해서 많은 수학적 기법이 사용되며, 구체적으로는 복소수와 삼각법이 활용된다. 이러한 수학적 접근 방식을 통해 절대 위치 정보를 복구할 수 없게 하고, 상대 위치 정보에만 의존하도록 한다.

![스크린샷 2024-07-26 114114](https://github.com/user-attachments/assets/0af90193-1650-4bc6-b79f-99403a910be8){: .responsive-img .align-center}


위의 그림이 RoPE의 인코딩 방법을 수학적으로 표현한 것이다. 각 요소에 대해 간단히 살펴보자면

$$\begin{pmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \\ \vdots \\ x_{d-1} \\ x_d \end{pmatrix}$$

-   여기서 $x$는 입력 벡터로, 각 요소$x_i$는 시퀀스 내의 각 위치에 해당하는 값이다. 벡터의 차원은 $d$다.


$$\begin{pmatrix} \cos m \theta_1 \\ \cos m \theta_1 \\ \cos m \theta_2 \\ \cos m \theta_2 \\ \vdots \\ \cos m \theta_{d/2} \\ \cos m \theta_{d/2} \end{pmatrix}​$$

-   $\cos m \theta_i$는 위치 $m$에서의 코사인 값을 나타내며, $\theta$는 특정 파라미터이다. 이 값들은 각 입력 벡터의 요소에 곱해져 위치 인코딩을 생성한다.

    
  $$\begin{pmatrix} \sin m \theta_1 \\ \sin m \theta_1 \\ \sin m \theta_2 \\ \sin m \theta_2 \\ \vdots \\ \sin m \theta_{d/2} \\ \sin m \theta_{d/2} \end{pmatrix}​$$
   

 - $\sin m \theta_i$는 위치 $m$에서의 사인 값을 나타내며, 역시 각 입력 벡터의 요소에 곱해진다.

    
$$\begin{pmatrix} -x_2 \\ x_1 \\ -x_4 \\ x_3 \\ \vdots \\ -x_d \\ x_{d-1} \end{pmatrix}​$$
   

 - 원래 벡터 $x$의 요소들이 교환되고 반전된 형태이다. 예를 들어, $x_1$​과 $x_2$가 위치를 바꾸고, $x_2$​는
   부호가 반전된다. 이는 사인 요소와 결합되어 새로운 인코딩을 생성한다.

$x$의 벡터가 입력 벡터이고 둘 중에 하나가 쿼리 벡터 또는 키 벡터가 된다.  강의에서는 코사인 쪽을 쿼리 벡터로 설명을 한다. 하나의 벡터는 순서대로 나열되어 있지만 다른 하나의 벡터는 순서가 바뀌어 있고, 반전되어 있다. 그리고 각각의 벡터에 $\cos m \theta$ 들과 $\sin m \theta$ 를 곱한다. 이걸 더함으로써 Positional Encoding에 대한 특징을 얻어낼 수 있다고 한다. 위의 곱셈 및, 벡터 변환을 통해 절대 위치 정보를 제거하고, 상대 위치 정보만을 얻어내 사용한다고 한다. 이로 인해 범위를 넘어선 새로운 데이터에 대해서도 잘 대응한다. 이러한 방식은 LLaMa에서 사용 중이라고 한다.


## **Layer Normalization and Residual Connections**


이전에 RNN에서 역전파 과정 중 그라디언트가 점점 작아지다 소실(또는 폭발)하는 문제가 발생한다고 하였다. 그리고 이러한 문제는 트랜스포머 모델에서도 발생할 수 있다고 설명한다.
Transformer 모델에서도 초기 버전에서는 RNN과 유사한 그라디언트 소실 문제가 발생할 수 있었지만, 최근에 와서 이러한 문제를 해결하였다고 한다. 이 방법에 대해 지금부터 설명을 할 예정이다.

![스크린샷 2024-07-26 123121](https://github.com/user-attachments/assets/051742d6-512f-4117-97ae-fa60e45c7073){: .responsive-img .align-center}

이전에 본 디코더 모델이다. 트랜스포머 모델은 다중 레이어 구조로 이루어져있다. 해당 이미지의 Nx 가 레이어의 개수 만큼 반복한다는 것을 의미한다고 했었다. 근데 이러한 다중 레이어에 의해 그라디언트 소실 문제가 발생할 수 있다. 이는 특히 모델의 초기에 나타날 수 있다. 이를 해결하기 위해 두 가지 방법을 적용할 수 있다.

### **Layer Normalization**

첫 번째는 레이어 정규화이다. 얘는 그라디언트 소실 문제를 해결하기 보단 그라디언트 폭발을 방지하거나 값이 불안정해지는 것을 방지하는 역할을 한다.
출력 값을 일정한 범위로 정규화하여 학습 과정에서 값의 변동을 줄임으로써 학습이 안정적으로 이루어지게 한다. 레이어 정규화를 수식으로 표현하면 아래와 같다.

![스크린샷 2024-07-26 123127](https://github.com/user-attachments/assets/ebf9f66a-7501-46fd-949a-053510da3d60){: .responsive-img .align-center}

위 식을 설명하자면 우선 입력 벡터의 모든 요소를 더한 후 요소의 개수로 나눈다. 즉, 벡터의 평균을 계산한다. 그 후 Standard deviation 표준 편차를 계산한다. 각 요소에서 평균을 뺀 값을 제곱한 후, 이를 다시 더한 후 평균을 구한 다음, 그 결과의 제곱근을 취합니다. 즉, 벡터의 표준 편차를 계산합니다. $$\sigma(x) = \sqrt{\frac{1}{n} \sum_{i=1}^n (x_i - \mu)^2}$$

이 두 개를 구한 후 벡터의 각 요소에서 평균을 빼고 표준 편차로 나눔으로써 벡터의 값을 정규화한다. 이렇게 하면 벡터의 평균이 0이 되고, 표준 편차가 1이 된다.

정규화 후, 게인 $g$을 곱하고 바이어스 $b$를 더해준다. 이는 벡터를 표준 범위로 이동시킨 후, 다시 원하는 범위로 조정하는 과정이다. 이렇게 함으로써, 모든 벡터가 일관된 공간에 위치하게 된다. 이 위치와 범위는 $g$과  $b$에 의해 결정된다.

이러한 레이어 정규화를 통해, 각 레이어의 출력이 예측 가능한 범위 내에 있게 된다. 이는 학습 과정에서 일관성을 유지하고, 예측 가능한 출력을 얻을 수 있도록 도와준다.

여기서 잠깐 간단하게 Batch Normalization 과 Layer Normalization 의 차이에 대해 설명한다.

-   **Batch Normalization**:
    
    -   배치 내 모든 샘플을 사용하여 정규화.
    -   배치 크기에 따라 통계가 달라질 수 있으며, 추론 시 배치 통계가 필요함.
    -   학습 속도 향상과 그라디언트 소실/폭발 문제 완화.
-   **Layer Normalization**:
    
    -   각 샘플 독립적으로 정규화.
    -   배치 크기에 의존하지 않으며, 일관된 출력을 제공.
    -   배치 통계가 필요 없으므로 추론 시에도 사용 가능.


### **RMS Norm**

기존 레이어 정규화에서 개선이 이루어진 버전인 RMS Normalization 이라는 것도 있다.(Route-Mean-Square)

RMS Norm은 레이어 정규화를 단순화한 형태이다. 레이어 정규화와 달리 평균(normalization step)을 계산하고 빼는 과정이 없다.(값들을 전체적으로 중간?으로 옮기는 과정이 생략, 또한 바이어스나 게인도 없다.) 대신 각 요소의 스프레드(분포)를 조정한다. 즉, 각 요소 간의 상대적인 크기만을 정규화다.

이러한 RMS Norm은 레이어 정규화보다 더 낫거나 그러진 않고 비슷한 결과를 제공하지만, 계산이 더 간단하고 빠르다. 여러 파라미터가 빠졌기 때문! 따라서 Layer Norm 보다 효율적이기 때문에 사용된다. 


### **Residual Connections**

![스크린샷 2024-07-26 131617](https://github.com/user-attachments/assets/875ebfce-2071-4764-ba33-14a4e0fc9d3d){: .responsive-img .align-center}

Residual Connections(잔차 연결) 가 나타내는 것은 위 그림에서 빨간 네모박스가 쳐저있는 저기다.

잔차 연결은 입력과 출력을 더해주는 방식으로 입력이 출력에 직접 추가되는 연결이다. 이걸 식으로 표현하면 다음과 같다.

$$Residual(x,F)=F(x)+x$$

단순히 더하기만 하는 심플한 방식이며 이는 그라디언트 소실을 방지하고, 입력과 출력 간의 차이를 학습하는 데 도움을 준다. 두 값이 얼마나 일치하는가 보단 두 값이 얼마나 차이나는가를 중점적으로 학습하여 출력에 어떤 것을 적용해야 할까를 학습하는 느낌이다.

이 잔차 연결은 멀티헤드 어텐션에도 영향을 주는데, 잔차 연결을 사용하면 입력 정보를 출력에 직접 추가하기 때문에 어텐션 메커니즘이 자기 자신에게 집중할 필요가 줄어든다. 따라서 어텐션 메커니즘이 더 주변의 다른 입력 정보에 집중하게 되고, 이를 통해 더 많은 컨텍스트 정보를 학습할 수 있게 된다.

### **Post- vs. Pre- Layer Norm **

트랜스포머 모델에 있어서 또다른 개선 중 하나는 바로 이 Post, Pre-Layer Norm 에 관한 것이다.

![스크린샷 2024-07-26 133031](https://github.com/user-attachments/assets/064ba852-62d0-4935-816e-8a666afc5384){: .responsive-img .align-center}


원래 Transformer 모델에서는 Multi-Head Attention과 Feed Forward Network 뒤에 Layer Norm이 위치해 있었다고 한다. 이는 위의 그림에서 왼쪽과 같다. 
이런 구조의 문제점이 무엇이냐면 잔차 연결(Residual Connection)을 중간에서 끊어버리는 효과가 있다는 것이다. 즉, Layer Norm이 잔차 연결 경로에 위치해 있어, 잔차 연결의 본래 목적을 방해하게 된다.

> -   잔차 연결은 입력을 그대로 출력에 더해줌으로써 그라디언트 소실 문제를 방지하고, 입력과 출력 간의 직접적인 연결을 유지한다.
> -   Layer Norm이 잔차 연결 경로에 위치하면, 그라디언트 전파가 원활하지 않게 된다

이런 문제를 해결, 수정하기 위해 개선된 방식이 Pre-Layer Norm 방식이다. 이는 위의 그림에서 오른쪽과 같다. 개선된 Transformer 모델에서는 Layer Norm이 각 레이어의 앞에 위치한다.

이렇게 하면 Layer Norm이 잔차 연결 경로에 위치하지 않게 되어, 잔차 연결이 입력과 출력을 직접 연결하게 된다.

> -   이는 그라디언트 전파가 더 원활하게 이루어지게 하여 학습을 더 안정적이고 효과적으로 만든다.

Layer Norm 이 그라디언트 전파에 영향을 미친다고 하는데 어떻게 미치는 걸까?

> Identity 함수(단순한 덧셈 등)는 그라디언트를 변화시키지 않지만, 다른 함수들은 그라디언트를 변화시킨다.  LayerNorm의 표준 편차로 값을 나누어 정규화하기 때문에, 이는 그라디언트를 변화시켜 전파 과정에서 그라디언트를 작게 만들 수 있다. 특히 표준 편차가 큰 경우, Layer Norm은 그라디언트를 더 작게 만들어 그라디언트 소실 문제를 일으킬 수있다. 따라서 이는 그라디언트 전파에 충분히 영향을 끼칠 수 있다는 의미가 된다.

## **Feed Forward Layer**



### 피드포워드 레이어의 역할


1.  **피드포워드 네트워크의 기능**:
    -   피드포워드 네트워크는 어텐션 메커니즘에서 얻은 출력을 독립적으로 처리하여 새로운 특징(feature)을 추출한다.
    -   각 벡터에 대해 독립적으로 작동하므로, 시퀀스의 각 벡터에 대해 동일한 피드포워드 네트워크가 적용된다.
2.  **피드포워드 네트워크의 구조**:
    -   피드포워드 네트워크는 두 개의 선형 변환과 그 사이에 비선형 활성화 함수를 포함한다.
    -   일반적인 수식: $$\text{FFN}(x) = f(W_2 \cdot f(W_1 \cdot x + b_1) + b_2)$$
    -   여기서 $f$는 비선형 활성화 함수이다.
3.  **바이어스 제거**:
    -   최신 연구에서는 피드포워드 네트워크에서 바이어스(bias) 항을 제거하는 것이 일반적이다. 이는 파라미터 수를 줄이고, 학습의 안정성을 높이기 위함이다.
    -   바이어스를 제거하면 수식은 다음과 같이 단순화된다: $$\text{FFN}(x) = W_2 \cdot f(W_1 \cdot x)$$

### 활성화 함수

1.  **ReLU (Rectified Linear Unit)**:
    -   ReLU는 입력이 0보다 작으면 0을 출력하고, 0보다 크면 그 값을 그대로 출력한다.
    -   수식: $$\text{ReLU}(x) = \max(0, x)$$
    -   ReLU의 문제점: 입력 값이 0보다 작으면 그라디언트가 0이 되어, 학습이 멈출 수 있다 (Dead Neurons).
2.  **SiLU (Sigmoid Linear Unit) 또는 Swish**:
    -   SiLU는 ReLU와 유사하지만, 입력이 0보다 작아도 그라디언트가 0이 되지 않는다.
    -   수식: $$\text{SiLU}(x) = x \cdot \sigma(x)$$여기서 $\sigma(x)$는 시그모이드 함수다.
    -   SiLU는 입력이 음수일 때도 작은 그라디언트를 유지하므로, ReLU의 단점을 보완한다.

### 피드포워드 네트워크의 특징 추출

1.  **특징 벡터**:
    -   피드포워드 네트워크는 입력 벡터를 더 큰 차원의 벡터로 확장하여 많은 특징을 추출한다.
    -   이러한 특징들은 Transformer 모델이 학습한 정보와 직접적으로 관련이 있다.
2.  **특징 해석**:
    
    -   연구자들은 Transformer 모델을 해석할 때, 피드포워드 네트워크에서 추출된 특징 벡터를 분석한다.
    -   예를 들어, 특정 사실(예: 미국 대통령이 누구인지)을 모델이 어떻게 기억하는지 분석할 때, 피드포워드 네트워크의 출력 벡터를 조사한다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc4MzE0OTc0MiwzMTU2MTY5MzgsLTQwMT
U0MjU2MSwtMTc4NzgxOTM5NCwxOTIwMTU1MzU4LC0xOTg1MTk1
NDA4LC01NzMyNzgzODcsLTkxMTg0NTk5OSw0NjAzNjAzNzksLT
I2MzY3MTEyNiwtNDAzNzY3NTcyLDk4Nzk0MzEzNCwtNzgzMDYy
MjI3LDE5MDE5MzI3MiwtMjEzNzYzODI2MywyMDIxNDA2MTIzLC
0xOTcwMDMzMDM5LDUwNTYxODAwMSw1MDU2MTgwMDEsMjE1MTY0
ODIwXX0=
-->