---
title: "Multivariable linear Regression"
date: 2020-10-25 23:28:00 -0000
categories: [Study, BGM, AI Practice]
tags: [TIL, AI, BGM, study]
---

저번에는 [한 개의 x를 통해 예측하는 선형회귀](https://coalery.github.io/2020-10-18-bgm-ai-study-practice-linear-regression/)에 대해서 배워보았다.

이번에는 여러 x를 통해 예측하는 선형회귀에 대해서 배워보겠다.

## 어떻게 정의할까!

![eq1](/assets/img/2020-10-25-bgm-ai-study-practice-multi-variable-lr/eq1.png)

3개의 x에 대한 Hypothesis는 위와 같이 정의한다.

![eq2](/assets/img/2020-10-25-bgm-ai-study-practice-multi-variable-lr/eq2.png)

따라서, Cost(Loss) Function은 위와 같이 정의한다. 위 첨자의 (i)는 i번째 값이라는 뜻.

다른 경우도 위와 같이 정의할 수 있으나, 너무 길어질 수도 있다.

![eq3](/assets/img/2020-10-25-bgm-ai-study-practice-multi-variable-lr/eq3.png)

![eq4](/assets/img/2020-10-25-bgm-ai-study-practice-multi-variable-lr/eq4.png)

그래서 행렬을 사용하여 위와같이 간단하게 나타낸다.

<br>

## 인스턴스가 너무 많아..

|x1|x2|x3|Y|
|:---:|:---:|:---:|:---:|
|73|80|75|152|
|93|88|93|185|
|89|91|90|180|
|96|98|100|196|
|73|66|70|142|

한 행 한 행 각각을 인스턴스라고 부른다.

현재는 5개지만, 만약 인스턴스가 10,000개나 그 이상이 될 수도 있는데 그 수마다 계산하기엔 비효율적이다. 그러므로 행렬 곱셈을 활용하여 아래와 같이 나타내어 계산하면 더욱 효율적으로 계산할 수 있다.

![eq5](/assets/img/2020-10-25-bgm-ai-study-practice-multi-variable-lr/eq5.png)

각각을 계산할 필요없이, 하나의 긴 행렬에 넣고 계산하면 바로 원하는 값이 나오게 된다.

<br>

## 직접 만들어봅시다!

![code1](/assets/img/2020-10-25-bgm-ai-study-practice-multi-variable-lr/code1.png)

코드는 위와 같이 구성할 수 있다.

x1, x2, x3 로 3개의 placeholder로 정의되어 데이터를 받고 있으며, 가중치도 w1, w2, w3 으로 3개를 이용한다.

![i1](/assets/img/2020-10-25-bgm-ai-study-practice-multi-variable-lr/i1.png)

그 결과이다.

이는 각각의 변수에 대해 선언하므로, 비효율적이다.

<br>

## 행렬 써볼까요!

![code2](/assets/img/2020-10-25-bgm-ai-study-practice-multi-variable-lr/code2.png)

행렬을 활용하여 코드를 구성하였다.

주목할 점은,

- `hypothesis`를 정의할 때 matmul 함수를 사용하였다

- `x_data`와 `y_data`를 정의할 때 행렬처럼 정의하였다.

- `X`와 `Y`의 placeholder의 shape를 정의할 때, `None`을 사용하였다.

- Variable `W`를 정의할 때, shape를 [3, 1]로 주었다.

![i2](/assets/img/2020-10-25-bgm-ai-study-practice-multi-variable-lr/i2.png)

그 결과이다.

<br>

---

<br>

이 글은 [부산 개발자 모임(BGM)](https://cafe.naver.com/busandevelopers)에서 진행하고 있는 AI 실습위주 스터디에서 배운 내용을 기반으로 작성되었습니다.

해당 스터디는 [모두를 위한 딥러닝 강좌 시즌1](https://www.youtube.com/playlist?list=PLlMkM4tgfjnLSOjrEJN31gZATbcj_MpUm)의 내용을 기반하여 진행하며, 글에서 나온 모든 출처가 명시되지 않은 이미지는 해당 강좌에서 나왔음을 밝힙니다.