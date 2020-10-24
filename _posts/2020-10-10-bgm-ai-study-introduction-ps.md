---
title: "문제 해결 및 탐색 전략"
date: 2020-10-10 13:48:00 -0000
categories: [Study, BGM, Ai Introduction]
tags: [TIL, AI, BGM, study]
---

### Example : Romania

![i1](/assets/img/2020-10-10-bgm-ai-study-introuction-ps/i1.png)

`Romania`에서 휴가를 보내고, 내일 `Romania`를 떠나야 한다.

떠날 때는 `Bucharest`라는 도시로 돌아가서 비행기를 타야 하는데, 내가 `Arad`라는 도시에 있는 경우 어떻게 해야 `Bucharest`까지 갈 수 있는가.

<br>

---

<br>

**초기 상태와 목표 정의**

- 초기 상태(Initial State) : 현재 있는 `Arad` 도시

- 목표(Goal State) : 비행기를 탈 수 있는 `Bucharest` 도시로 가는 것.

<br>

**문제 표현**

- 상태(State) : 여러 도시들

- 행동(Action) : 운전을 통해 도시 사이를 이동하는 것.

{: .box-note}
`Arad`라는 상태(State)에서 시작하여 여러 개의 행동(Action)을 통해 도시를 옮겨 다니며 결국 `Bucharest`에 도착하는 행동들의 연속을 이 문제의 해(Solution)라고 정의할 수 있다.

<br>

**최고의 해**

- 최단거리를 이동하여 `Bucharest`에 도달하는 경로

<br>

---

<br>

### 인공지능에서 문제 정의 시 필요한 4가지 구성요소

**초기상태**

- 이 문제를 푸는 데 있어서 첫 상태.

- Romania 예제에서는 `Arad`라는 도시

<br>

**가능한 행동들(Actions)**

- 어떤 상태에서 다른 상태로 이동하기 위한 행동

- Romania 예제에서는 `Arad` 상태(도시)에서 할 수 있는 행동들(갈 수 있는 도시들 중 하나로 이동)

<br>

**목표 테스트(Goal Test)**

- 목표에 도달하였는지 아닌지를 판단해주는 일종의 테스트

- 문제에 따라서는 하나의 상태를 목표로 설정할 수도 있으나, 많은 경우에서 조건으로 정의하는게 더 좋음(체스 등).

<br>

**경로 비용(Path Cost)**

- 하나의 경로를 수행하는데 있어서의 비용

- Romania 예제에서는 도시들 사이의 거리이다.

{: .box-note}
실제 문제를 추상화(Abstraction)하기 위해 어떻게 상태를 정의할 것인가.

<br>

---

<br>

### Tree Search Algorithms

![i2](/assets/img/2020-10-10-bgm-ai-study-introuction-ps/i2.png)

초기 상태가 루트이고, 각 노드는 상태를 나타낼 수 있으며, 각각의 Edge는 행동이라고 정의할 수 있다.

{: .box-note}
**Question**: 어떤 노드부터 탐색할 것인가?

<br>

**전략 판단 기준**

- 완전성(Completeness) : 반드시 해를 찾을 수 있는가.

- 시간 복잡도(Time Complexity) : 얼마만큼 노드를 탐색해야만 목표를 찾을 수 있는가.

- 공간 복잡도(Space Complexity) : 나중에 탐색할 노드를 메모리상에 저장해 놓을 때, 그 공간이 얼마나 필요한가.

- 최적도(Optimality) : 항상 최적의 해를 찾을 수 있는가.

<br>

**무정보 탐색(Uninformed search)**

문제 정의의 4가지 구성요소에서 주어진 정보만을 활용하여 탐색하는 전략

- 너비 우선 탐색(Breadth-First Search, BFS)

- 깊이 우선 탐색(Depth-First Search, DFS)

- 그 외(Uniform-cost search, Depth-limited search, Iterative deepening search)

<br>

**너비 우선 탐색(Breadth-First Search, BFS)**

![i3](/assets/img/2020-10-10-bgm-ai-study-introuction-ps/i3.png)

가장 얕은 노드부터 탐색한다. FIFO(First In First Out) 데이터 구조(큐, Queue)로 구현이 가능하다.

1. A(루트)에 방문한 뒤, 큐에 A를 넣는다.

2. 다음 방문할 노드를 찾기 위해 큐에서 값(A)을 가져온다.

3. 가져온 값의 자식 노드(X)에 방문 한 뒤, 큐에 넣는다.

4. 다음 방문할 노드를 찾기 위해 큐에서 값(X)을 가져온다.

5. 가져온 값의 자식 노드(G, H)에 방문 한 뒤, 큐에 넣는다.

6. 반복

<br>

**깊이 우선 탐색(Depth-First Search, DFS)**

![i4](/assets/img/2020-10-10-bgm-ai-study-introuction-ps/i4.png)

특정 경로를 정해서 끝까지 탐색해본 뒤, 다시 위로 올라와서 탐색한다. LIFO(Last In First Out) 데이터 구조(스택, Stack)로 구현이 가능하다.

1. A(루트)에 방문한 뒤, 스택에 A를 넣는다.

2. 다음 방문할 노드를 찾기 위해 스택에서 값(A)을 가져온다.

3. 가져온 값의 자식 노드(X)에 방문 한 뒤, 스택에 넣는다.

4. 다음 방문할 노드를 찾기 위해 스택에서 값을 가져온다.

5. 가져온 값의 자식 노드(H, G)에 방문 한 뒤, 스택에 넣는다.

6. 반복

<br>

**BFS vs DFS**

|기준|BFS|DFS|
|:---:|:---:|:---:|
|완전성|T|F|
|시간 복잡도|![eq1](https://latex.codecogs.com/png.latex?O%28b%5E%7Bd%2B1%7D%29)|![eq2](https://latex.codecogs.com/png.latex?O%28b%5E%7Bm%7D%29)|
|공간 복잡도|![eq3](https://latex.codecogs.com/png.latex?O%28b%5E%7Bd%2B1%7D%29)|![eq4](https://latex.codecogs.com/png.latex?O%28bm%29)|
|최적도|T|F|

{: .box-note}
BFS는 목표를 찾는 것을 보장하지만, 시간이 많이 걸리고 공간을 많이 사용한다.
DFS는 목표를 찾는 것을 보장하지 못하나, 시간과 공간을 비교적 적게 사용한다.

<br>

---

<br>

### 출처

너비 우선 탐색 이미지, 깊이 우선 탐색 이미지 : https://www.zerocho.com/category/Algorithm/post/5870153c37e1c80018b64eb0

<br>

---

<br>

이 글은 [부산 개발자 모임(BGM)](https://cafe.naver.com/busandevelopers)에서 진행하고 있는 AI 개론 스터디에서 배운 내용을 기반으로 작성되었습니다.

해당 스터디는 [K-MOOC 인공지능의 기초 강좌](http://www.kmooc.kr/courses/course-v1:SNUk+SNU048_011k+2020_T2/about)의 내용을 기반하여 진행하며, 글에서 나온 모든 출처가 명시되지 않은 이미지는 해당 강좌에서 나왔음을 밝힙니다.