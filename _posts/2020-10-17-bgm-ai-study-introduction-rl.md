---
title: "강화 학습 소개"
date: 2020-10-17 15:24:00 -0000
categories: [Study, BGM, AI Introduction]
tags: [TIL, AI, BGM, study]
---

# 강화 학습

'무엇을 어떻게 하라.' 가 아닌, 스스로 할 수 있게 한 다음 결과를 놓고 보상 혹은 벌을 주는 방식으로 학습한다.

비효율적인 학습방법이라 할 수도 있으나, 룰을 일일이 알려주기 힘든 환경의 경우 유리하게 사용될 수 있다.

- 보상 함수를 통해 학습한다.

- 자세한 내용은 에이전트가 스스로 배운다.

- 보상 혹은 벌이 한참 후에 주어질 수도 있다.

- 어떤 순서로 강화 학습 에이전트가 학습할 것인가. (Non i.i.d, 학습 데이터가 서로 독립 사건이 아니며, 똑같은 확률분포에서 주어지지 않는다.)

- 에이전트가 특정 스텝에서 어떤 행동(Action)을 취했느냐가 다음에 얻을 데이터가 어떤 형태로 올지 결정하는 경우가 많다.

<br>

## 기본 모델

![i1](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i1.png)

- 에이전트와 환경이 있다.

- 에이전트는 주변 환경과의 상호작용을 통해 학습한다.

- 강화 학습의 목적 : 에이전트가 최대의 보상을 얻을 수 있는 행동/제어 정책을 찾는 것.

1. 에이전트가 어떤 상태에 있다가, 해당 상태에서 취할 수 있는 행동들이 있는데, 이 중 하나를 선택해서 수행한다.

2. 해당 행동을 통해 에이전트는 다음 상태로 변경이 되고, 해당 행동에 대한 보상이 주어진다.

3. 이를 반복하며 보상을 계속 관측함으로써 스스로 배울 수 있도록 한다.

{: .box-note}
보상을 어떻게 정의하고 어떻게 주느냐가 가장 중요하다.

<br>

## 주요 요소

- 정책(Policy) : 에이전트의 행동 함수. 에이전트가 어떤 상태에서 어떤 행동을 할지를 정해주는 함수.

- 가치 함수(Value Function) : 어떤 상태에 갔을 때, 그 상태가 얼마나 좋은지를 나타내는 함수.

- 모델(Model) : 에이전트가 환경을 어떻게 표현하고 있는지에 대한 모든 것.

<br>

## 정책(Policy)

1. Deterministic Policy

    ![eq1](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq1.png)

    어떤 상태에서 어떤 행동을 할지를 정의해 놓은 것.

2. Stochastic Policy

    ![eq2](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq2.png)

    어떤 상태에서 어떤 행동을 취할지를 확률분포로 주어지는 것. 어떤 행동을 취할 확률이 높긴 하나 항상 그 행동을 취하지는 않는다.

<br>

## 가치 함수(Value Function)

![eq3](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq3.png)

- π 라는 정책을 따라 행동한다고 할 때, S라는 상태의 가치를 나타내는 함수.

- 미래에 대한 보상의 기댓값

- γ는 할인율(Discound Rate)이다. 미래에 대한 보상을 할인한다는 것이며, 먼 미래일 수록 그것에 대한 보상은 더욱 할인된 값으로 계산에 적용된다.

<br>

## 모델(Model)

1. P

    ![eq4](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq4.png)

    S라는 상태에 있을 때 a 라는 행동을 취하면 S'이라는 상태로 갈 확률

2. R

    ![eq5](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq5.png)

    S라는 상태에 있을 때 a 라는 행동을 취하면 그때 얻는 보상에 대한 확률분포

<br>

## Example : Maze

![i2](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i2.png)

- 보상 : 한번 타임 스텝을 할 때마다 -1을 준다.

- 행동 : 동쪽, 서쪽, 북쪽, 남쪽

- 상태 : 현재 에이전트의 위치

<br>

![i3](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i3.png)

왼쪽의 그림에서 각 상태마다 화살표가 있는데, 그것이 정책이다. 특정 상태에서 어떻게 행동해야하는지를 화살표로 표현한 것.

오른쪽 그림은 가치 함수의 예를 보여주고 있다. 각각의 상태가 얼마나 가치가 있는지를 나타낸다.

<br>

![i4](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i4.png)

위의 격자에서 흰 색으로 표현된 부분은 갈 수 있다는 것을 표현하고, 검은색으로 표현된 부분은 갈 수 없다는 것을 표현한다. (P 모델)

각각의 격자마다 -1로 채워져 있는데, 이것이 보상 함수의 값이다.

<br>

## 탐험(Exploration) vs 활용(Exploitation)

많은 경우 알고 있는 지식을 활용한다. 그러나 그것만을 활용하면 더 나은 해를 구할 수 없을 수도 있다.

그래서 일종의 랜덤적인 행동을 취하여 해당 행동에 대한 보상을 학습하는 과정도 필요하다.

<br>

## Prediction, Control

강화학습에서의 예측(Prediction)은 정책이 주어졌을 때, 가치 함수를 구하는 것이다.

제어(Control)은 문제가 주어졌을 때, 최적의 정책(보상을 최대한으로 할 수 있는 정책)을 찾는 과정이다.

<br>

## Example : Gridworld

![i5](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i5.png)

- 에이전트가 A라는 위치에 도달한 경우 보상으로 10을 받고, A'로 이동하게 된다.

- 에이전트가 B라는 위치에 도달한 경우 보상으로 5를 받고, B'로 이동하게 된다.

여기서 만약 Uniform Random Policy로 정책을 정하면, 동 서 남 북 각각으로 가는 행동을 선택할 확률이 모두 0.25로 동일하다. (무작위로 간다.)

<br>

![i6](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i6.png)

- 여기서 V\*는 많은 가치 함수 중 최적의 가치함수이고, π\*는 많은 정책 중 보상을 가장 최대화시키는 정책이다.

<br>

---

<br>

# MDP(Markov Decision Processes)

<br>

## Markov Processes

1. 마르코프 프로세스는 S, P 두 가지를 가진 튜플이다.

    - S : 상태들의 집합
    
    - P : 상태 전이 함수. 상태를 받아서 다른 상태로 맵핑(Mapping)해주는 함수이며 확률분포 형태로 주어진다. (행렬로 표현이 가능하다.)
    
    ![eq6](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq6.png)

2. Memoryless : 히스토리가 상태 하나로 설명이 된다. 그러므로 현재 상태만 알면 이전의 히스토리는 몰라도 된다.

3. Random Process : 상태 전이가 어떠한 확률분포를 따라서 간다.

4. Markov Property가 있는 랜덤 상태의 연속이다.

<br>

## Markov Property

- 상태는 히스토리로부터 주어진 모든 정보를 가지고 있다.

![eq7](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq7.png)

{: .box-note}
현재 상태가 주어졌을 때 다음 상태를 어떻게 결정할 것인지에 대한 확률 분포와 어느 상태를 방문했는지를 가진 모든 히스토리가 주어졌을 때 다음 상태를 어떻게 결정할 것인지에 대한 확률 분포가 같다. 즉, 현재 상태만 알면 어디로 갈지에 대한 확률분포가 정해진다.

<br>

## Example : Student Markov Processes

![i7](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i7.png)

![i8](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i8.png)

상태 전이 함수 P에 대한 행렬이 표현되어 있고, 각 상태에 대한 전이 확률이 주어지게 된다.

여기서 각 행에 대해서 합을 구해보면 모두 1이다.

실제로 강화학습에서 게임을 하는 인공지능을 만들 경우, 게임을 여러 판을 하게 되는데 그 각각의 판이 하나의 에피소드가 된다.

이를 통해 P를 예측할 수도 있고, 정책을 구할수도 있다.

<br>

## Markov Reward Processes

Markov Process에서 보상 함수 R, 할인율 γ가 추가된다.

- 보상 함수 R : 어떤 상태가 주어졌을 때, 그 상태의 보상 값을 맵핑(Mapping)하는 함수이다.

    ![eq8](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq8.png)

- 할인율(Discount Factor) : 먼 미래일 수록 보상을 얼마나 할인할 것인가에 대한 스칼라 값.

    ![eq9](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq9.png)

<br>

## Example : Student Markov Reward Processes

![i9](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i9.png)

<br>

## Return and Value Function

![eq10](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq10.png)

현재 타임 스텝 t로부터 미래에 얻을 수 있는 보상을 할인을 적용하여 모두 합한 것.

{: .box-note}
즉, 당장 얻을 수 있는 보상이 나중에 얻는 보상보다 훨씬 더 높은 가치를 주는 것이다.

<br>

![eq11](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/eq11.png)

가치 함수는 s라는 상태에 있을 때 얻을 수 있는 Return 의 기댓값이다.

<br>

## 할인율에 대해 더 깊이 들어가봅시다.

![i10](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i10.png)

만약 위와같은 Markov Reward Processes 예제가 있다고 할 때, 만약 우리가 S1 상태에서의 가치를 구하면 무한대로 되는 문제가 있다.

이때 할인율을 사용하면 가치 함수의 값을 특정 값에 수렴시킬 수 있다.

그 외에도 여러가지 이유가 있다.

1. 시간이 지날수록 에이전트가 살아있을 확률이 줄어드는 것에 대한 표현

2. 두 스텝 이후 얼마만큼의 보상을 받을 것이라 생각하나, 세상에는 불확실성이 존재하고 그만큼 할인을 해줘야 한다.

<br>

![i11](/assets/img/2020-10-17-bgm-ai-study-introduction-rl/i11.png)

Student Markov Reward Processes 예제에서 여러가지 에피소드에 대한 가치를 할인율 0.5을 적용하여 구한 것을 보여준다.

<br>

---

<br>

이 글은 [부산 개발자 모임(BGM)](https://cafe.naver.com/busandevelopers)에서 진행하고 있는 AI 개론 스터디에서 배운 내용을 기반으로 작성되었습니다.

해당 스터디는 [K-MOOC 인공지능의 기초 강좌](http://www.kmooc.kr/courses/course-v1:SNUk+SNU048_011k+2020_T2/about)의 내용을 기반하여 진행하며, 글에서 나온 모든 출처가 명시되지 않은 이미지는 해당 강좌에서 나왔음을 밝힙니다.