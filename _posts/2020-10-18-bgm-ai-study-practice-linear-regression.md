---
title: "선형 회귀(Linear Regression)"
date: 2020-10-18 23:44:00 -0000
categories: [Study, BGM, AI Practice]
tags: [TIL, AI, BGM, study]
---

## 선형 회귀(Linear Regression)?

![i1](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/i1.png)

선형 회귀는 적절한 선을 찾는 기법이다.

정확히는, 종속 변수 y와 한 개 이상의 독립 변수 X와의 선형 상관 관계를 모델링하는 회귀분석 기법이다.

<br>

![eq1](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/eq1.png)

해당 선은 위처럼 하나의 함수로 나타날 수 있다.

<br>

## Cost(Loss) Function

![i2](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/i2.png)

만들어진 선이 학습 데이터와 얼마나 맞는지를 확인하기 위한 함수.

![eq2](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/eq2.png)

함수값과 실제 데이터의 값의 차이의 제곱을 모두 더한 것이 이 함수의 값이다.

이 함숫값을 최소화하는 것이 선형 회귀의 목적이다.

<br>

## 직접 만들어봅시다

![i3](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/i3.png)

`Variable` 은 텐서플로우가 사용하는 변수로서, 학습 과정에서 자체적으로 변경시키는 값을 선언할 때 사용한다.

`random_normal` 함수는 Tensor의 Shape를 받아서 랜덤하게 Tensor를 만들어준다.

`reduce_mean` 함수는 Tensor의 평균을 구해주는 역할을 한다.

`GradientDescentOptimizer` 는 경사 하강법 알고리즘을 활용하여 최솟값을 찾아내는 역할을 한다.

`global_variables_initializer` 함수는 `Variable` 을 사용하였을 때에 이들을 초기화 시켜주는 역할을 한다.

갈수록 cost가 작아지는 것을 볼 수 있고, W는 1로, b는 0으로 수렴하는 것을 볼 수 있다.

<br>

![i4](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/i4.png)

![i5](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/i5.png)

물론, Placeholder 를 사용하여 만들수도 있다.

2000번의 학습을 거친 모델을 통해 특정 값에 대한 예상되는 Y를 구하는 것도 가능하다.

<br>

## Cost(Loss)를 어떻게 최소화 시킬까?

![eq3](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/eq3.png)

먼저, 함수 H(x)를 위와 같이 간단하게 만들어보자.

<br>

![eq4](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/eq4.png)

그러면 우리는 위와 같은 Cost(Loss) 함수를 얻을 수 있다.

이 함수를 한번 자세히 들여다보자.

W = 1 일 때, cost(W) = 0

W = 0 일 때, cost(W) = 4.66···

W = 2 일 때, cost(W) = 4.66···

<br>

![i6](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/i6.png)

이를 반복하면, 위와 같은 그래프가 만들어진다.

눈으로 보면 최솟값이 바로 0임을 알고 있으나, 이를 계산하는 것은 컴퓨터임을 알아야한다.

이 때, 사용할 수 있는 알고리즘이 경사 하강법 알고리즘이다.

<br>

## 경사 하강법 알고리즘(Gradient Descent Algorithm)

Cost(Lost)를 최소화하는 알고리즘 중, 많이 쓰이는 알고리즘으로써 변수가 2개가 아닌 그 이상일 때도 사용이 가능하다.

기본 개념은 함수의 기울기(경사)를 구하고 경사의 절댓값이 낮은 쪽으로 계속 이동시켜 극값에 이를 때까지 반복시키는 것이다.

<br>

![eq1](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/eq1.png)

위의 함수 H(x)를 예로 들면, 경사도에 따라 W와 b 값을 계속 바꿔가며 cost(W, b)를 조금씩 줄여나간다.

<br>

## 직접 만들어봅시다.

![eq3](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/eq3.png)

여기서는 간소화된 함수를 사용한다.

<br>

![i7](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/i7.png)

-3부터 5(4.9)까지 0.1씩 증가되며 cost와 W 값을 구하여 그래프를 그려보면 위와 같이 그려진다.

경사 하강법을 구현하기 위해서는 그래프의 경사도를 구해야하는데, 이는 미분을 통해 구할 수 있다.

<br>

![eq4](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/eq4.png)

![eq5](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/eq5.png)

cost(W)를 미분하였다. α 는 학습률(Learning Rate)을 나타내고, 여기서는 0.1이라는 상수이다.

이를 텐서플로우를 통해 구현하면 아래와 같다.

<br>

![i8](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/i8.png)

위에서 볼 수 있듯이, `learning_rate`는 α=0.1로 초기화되었고, 이와 함께 미분된 식을 구현하였다.

`descent` 를 다시 `W` 에 할당하여 반복적으로 계산하는 것을 볼 수 있다.

출력 결과를 보면 1로 수렴하는 것을 볼 수 있다.

<br>

![i9](/assets/img/2020-10-18-bgm-ai-study-practice-linear-regression/i9.png)

물론, 이는 위처럼 텐서플로우의 `GradientDescentOptimizer` 클래스를 사용하여 해결할 수 있다.

초기 값인 5.0이 1.0으로 수렴하는 것을 볼 수 있다.

<br>

---

<br>

## 출처

Linear Regression Explanation : [Wekipedia](https://ko.wikipedia.org/wiki/%EC%84%A0%ED%98%95_%ED%9A%8C%EA%B7%80)

Gradient Descent Explanation : [Wekipedia](https://ko.wikipedia.org/wiki/%EA%B2%BD%EC%82%AC_%ED%95%98%EA%B0%95%EB%B2%95)

<br>

---

<br>

이 글은 [부산 개발자 모임(BGM)](https://cafe.naver.com/busandevelopers)에서 진행하고 있는 AI 실습위주 스터디에서 배운 내용을 기반으로 작성되었습니다.

해당 스터디는 [모두를 위한 딥러닝 강좌 시즌1](https://www.youtube.com/playlist?list=PLlMkM4tgfjnLSOjrEJN31gZATbcj_MpUm)의 내용을 기반하여 진행하며, 글에서 나온 모든 출처가 명시되지 않은 이미지는 해당 강좌에서 나왔음을 밝힙니다.