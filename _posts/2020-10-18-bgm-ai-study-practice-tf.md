---
title: "텐서플로우의 기초"
date: 2020-10-18 18:47:00 -0000
categories: [Study, BGM, AI Practice]
tags: [TIL, AI, BGM, study]
---

## TensorFlow?

![tf](https://www.gstatic.com/devrel-devsite/prod/v36e9b4a2fdc696650f09851e8c880b958655492821ded3455f80aaef87b6b52b/tensorflow/images/logo.png)

텐서플로우는 데이터 플로우 그래프(Data Flow Graph)를 사용하여 수학적 계산을하는 오픈 소스 라이브러리이다.

<br>

## 데이터 플로우 그래프(Data Flow Graph)

![i1](/assets/img/2020-10-18-bgm-ai-study-practice-tf/i1.png)

- 노드 하나하나가 수학적인 연산이다.

- 간선(Edge)는 다차원의 데이터 배열(Tensor)이 흘러가는 길을 나타낸다.

<br>

## Hello World!

![i2](/assets/img/2020-10-18-bgm-ai-study-practice-tf/i2.png)

무언가를 배우면 꼭 해보는 `Hello, TensorFlow!` 를 출력해보았다.

해당 값을 가진 노드를 만들고, 세션을 만든 다음 실행시켰다.

문자 앞에 붙은 'b' 는 바이트 문자열이라는 뜻이다.

<br>

## 간단한 계산을 해보자

![i3](/assets/img/2020-10-18-bgm-ai-study-practice-tf/i3.png)

3과 4를 더해보았다. 이때, 각 노드는 Tensor로 이루어져있는 것을 볼 수 있다.

그래프를 만들기(Build) 위해 노드를 만들었고, 이를 세션을 만든 다음 실행시켰다.

<br>

## Placeholder

![i4](/assets/img/2020-10-18-bgm-ai-study-practice-tf/i4.png)

`adder_node` 를 통해 계산 노드를 미리 만들고, 값을 나중에 `feed_dict` 를 통해 줄 수 있다.

여기서 `a + b` 부분은 `tf.add(a, b)` 와 같다.

<br>

## Tensor

![i5](/assets/img/2020-10-18-bgm-ai-study-practice-tf/i5.png)

![i6](/assets/img/2020-10-18-bgm-ai-study-practice-tf/i6.png)

- Rank : 차원

- Shape : 모양

- Type : 데이터 타입(float32, float64, etc.)

<br>

---

<br>

# 출처

- Tensorflow Logo : [Tensorflow HomePage](https://www.tensorflow.org/?hl=ko)

<br>

---

<br>

이 글은 [부산 개발자 모임(BGM)](https://cafe.naver.com/busandevelopers)에서 진행하고 있는 AI 실습위주 스터디에서 배운 내용을 기반으로 작성되었습니다.

해당 스터디는 [모두를 위한 딥러닝 강좌 시즌1](https://www.youtube.com/playlist?list=PLlMkM4tgfjnLSOjrEJN31gZATbcj_MpUm)의 내용을 기반하여 진행하며, 글에서 나온 모든 출처가 명시되지 않은 이미지는 해당 강좌에서 나왔음을 밝힙니다.