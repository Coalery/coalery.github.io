---
title: "마르코프 결정 과정(MDP)"
date: 2020-10-24 10:49:00 -0000
categories: [Study, BGM, AI Introduction]
tags: [TIL, AI, BGM, study]
---

## 마르코프 결정 과정(MDP)

마르코프 결정 과정은 아래처럼 구성되어있다.

- 상태(State)들의 집합 S

- 행동(Action)들의 집합 A

- 전이 함수 P : S×A → S

- 보상 함수 R : S×A → 실수 집합 R

- 할인율 𝛾 ∈ [0, 1]

<br>

## 정책(Policy)

![eq1](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/eq1.png)

- 히스토리가 아닌, 현재 상태에 의존한다.

- 시간에 따라 변화하지 않는다. 즉, 10번째 스텝이나 100번째 스텝이나 같은 상태에 있을 경우, 행동의 확률분포는 동일하게 주어진다.

<br>

## 가치 함수(Value Function)

1. 상태 가치 함수

	![eq2](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/eq2.png)

	- 정책이 정의됨에 따라, 한 단계 더 업그레이드된 가치 함수이다.

	- 어떤 정책 아래에서 가치 함수가 정의되어있는지를 알려주기 위해 아래첨자에 𝜋를 썼다.

	- 어떠한 상태의 가치의 기댓값을 구하는 함수이다.

2. 행동 가치 함수
	
	![eq3](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/eq3.png)

	- 어떠한 상태에서 어떠한 행동을 취했을 때 얻을 수 있는 가치의 기댓값을 구하는 함수이다.

<br>

## Example : Student MDP

![i1](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i1.png)

- 위의 예시는 현재 𝛾 = 1, 랜덤 정책이다.

- Pub이 이전에는 상태로 정의되었는데, 이번에는 행동으로 정의되어있다.

- Pub이라는 행동을 취하면 보상 +1를 받고, 각 확률로 다른 상태로 간다.

<br>

## 벨만 방정식

1. 벨만 기대 방정식(Bellman Expectation Equation)
	
	![eq4](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/eq4.png)

	- 현재의 상태 가치 함수와 다음의 상태 가치 함수의 상관관계를 정의한 것.

	![eq5](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/eq5.png)

	- 현재의 행동 가치 함수와 다음의 행동 가치 함수의 상관관계를 정의한 것.

2. 벨만 최적 방정식(Bellman Optimality Equation)

	![eq6](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/eq6.png)

	- 현재의 상태 가치 함수에서 얻을 수 있는 최적의(최대의) 가치를 다음의 상태 가치 함수와의 상관관계로 정의한 것.

	![eq7](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/eq7.png)

	- 현재의 행동 가치 함수에서 얻을 수 있는 최적의(최대의) 가치를 다음의 행동 가치 함수와의 상관관계로 정의한 것.

<br>

## 벨만 방정식에서의 상태 가치 함수와 행동 가치 함수의 관계

![i2](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i2.png)

- 현재 상태에서 취할 수 있는 행동에 대한 확률과 그 행동의 가치를 곱한 것을 모두 더한 것.

- 한마디로 평균이다.

![i3](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i3.png)

- 현재 상태에서 어떤 행동을 취했을 때 얻을 수 있는 보상과 현재 상태에서 다음 상태로의 상태 전이 확률과 각각의 다음 상태의 상태 가치를 곱한 것을 모두 더한 뒤, 할인율을 곱하여 더한 것.

- 다음 스텝이기 때문에 할인율을 취한 것.

{: .box-note}
V를 구하려면 Q를, Q를 구하려면 V가 필요하게 된다. 그러므로 둘을 합쳐서 각각으로 나눠보자.

<br>

## 나눠봅시다.

![i4](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i4.png)

- 위의 식에서 Q 자리에 식을 대입한 것이다.

![i5](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i5.png)

- 위의 식에서 V 자리에 식을 대입한 것이다.

- 주의해야할 점은, 대입한 식이 현재 상태 s 에 대한 식이 아니라 다음 상태 s' 에 대한 식이라는 것.

<br>

## 예제에 적용해봅시다.

![i6](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i6.png)

<br>

## 처음부터 가치를 구하는 방법?

![i7](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i7.png)

![i8](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i8.png)

- 행렬을 통해 구할 수 있다. 처음에 V를 초기화(Initialize)한 다음, 계속 행렬 곱셈으로 주어진 수식을 반복하여 계산하면 결국 V가 수렴한다.

- 다만, 위의 계산을 처리할 때 소요되는 시간 복잡도는 O(n³)이다.

- 그래서 좀 더 효율적으로 풀기 위해 동적 프로그래밍(Dynamic Programming, DP)을 활용한다.

<br>

## Example : Small Gridworld

![i9](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i9.png)

- 𝛾 = 1, 종료되는 상태는 회색 정사각형.

- 격자 외부로 나가는 행동은 상태가 변하지 않게 된다.

- 한 번 움직일 때마다 -1 보상을 준다. 즉, 최단거리로 끝내는 정책이 학습된다.

- 랜덤 정책이다. 어떤 상태든 각 방향으로 가는 행동을 취할 확률은 모두 같다.

<br>

## 예제를 풀어봅시다.

![i10](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i10.png)

- 처음에는 모두 0으로 초기한 뒤, 반복해서 계산하면 수렴한다.

- 오른쪽의 화살표들은 행렬의 값에 따라 만들어진 탐욕적인 정책이다.

- 재미있는 점은, k=3 일 때부터, 이미 수렴되었다는 것.

<br>

## 정책을 더 향상시킬 수는 없을까?

1. 정책 𝜋를 초기화한다. 특별한 방법이 없다믄 그냥 랜덤 정책으로 초기화한다.

2. 그 정책 𝜋에 대한 가치 함수를 구한다.

3. 탐욕적 방법으로 정책을 업데이트한다.

	![eq8](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/eq8.png)

	- 해당 상태에서 취할 수 있는 행동들 중, 가치 함수의 값이 최대가 되는 행동을 취하도록 정책을 바꾼다.

4. 2와 3을 반복한다.

이를 도식화하면 아래와 같다.

![i11](/assets/img/2020-10-24-bgm-ai-study-introduction-mdp/i11.png)

<br>

## DP

- V를 통해 정책을 구하면 m 개의 행동들과 n 개의 상태들이 있을 때, 한 번의 반복에 대해 O(mn²)의 시간 복잡도를 가진다.

- 물론 Q를 통해서도 구할 수 있으나, 이는 한 번의 반복에 대해 O(m²n²)의 시간 복잡도를 가지므로 일반적으로 V를 활용한다.

<br>

---

<br>

## 출처

- Bellman Optimality Equation: [Reinforcement Learnig: An Introduction](https://web.stanford.edu/class/psych209/Readings/SuttonBartoIPRLBook2ndEd.pdf)

<br>

---

<br>

이 글은 [부산 개발자 모임(BGM)](https://cafe.naver.com/busandevelopers)에서 진행하고 있는 AI 개론 스터디에서 배운 내용을 기반으로 작성되었습니다.

해당 스터디는 [K-MOOC 인공지능의 기초 강좌](http://www.kmooc.kr/courses/course-v1:SNUk+SNU048_011k+2020_T2/about)의 내용을 기반하여 진행하며, 글에서 나온 모든 출처가 명시되지 않은 이미지는 해당 강좌에서 나왔음을 밝힙니다.