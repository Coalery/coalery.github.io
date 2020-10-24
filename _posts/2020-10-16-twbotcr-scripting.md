---
title: "트위치 봇 스크립팅 부분 완료!"
date: 2020-10-16 01:42:00 -0000
categories: [Toy Project, TwitchBotCreator]
tags: [twitch, bot, toy]
---

![i1](/assets/img/2020-10-16-twbotcr-scripting/i1.png)

- 자바스크립트 파일을 저장하고 불러오기
- 매개변수로 여러 정보를 정상적으로 건네주기

채팅을 보낸 사람의 뱃지 배열을 매개변수로 넘겨줘야하는데 그냥 `Object Array`로 넘기니 `null`로 넘어가고,

`NativeArray`로 만들어서 넘겼더니 함수를 호출할 때 오류가 발생했습니다.

그래서 찾아봤더니 오늘도 [스택 오버플로우](https://stackoverflow.com/questions/3090923/how-to-create-a-real-javascript-array-in-rhino)의 도움을 받아, 완성하였습니다.

`NativeArray`가 아니라, `Context.newArray(Scope, Object Array)`를 사용하니 정상적으로 작동되었습니다.

이제 봇을 활성화할 채널의 설정과 OAuth 설정을 만들고, 스크립트에 제공할 API를 만들면 이 프로젝트도 대충 마무리가 될거같네요.