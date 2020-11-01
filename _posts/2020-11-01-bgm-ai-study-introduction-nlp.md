---
title: "자연어 처리"
date: 2020-11-01 14:35:00 -0000
categories: [Study, BGM, AI Introduction]
tags: [TIL, AI, BGM, study]
---

## 자연어 처리는?

사람이 사용하는 언어를 기계도 이해하고 같이 활용하고 사용할 수 있도록 하는 학문이다.

<br>

## 관련 기술

![i1](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i1.png)

#### 많이 풀린 문제

- Spam Detection

	스팸 메일 거르기

- Part-Of-Speech(POS)

	각 단어의 품사 알아내기

- Named Entity Recognition(NER)

	명사들 중, 고유명사 찾아내기

<br>

#### 어느정도 풀린 문제

- Sentiment analysis

	문장의 감정을 알아내기

- Coreference resolution

	지시대명사가 무엇을 의미하는지 찾아내기

- Word Sense Disambiguation(WSD)

	단어가 어떤 의미로 쓰였는지 알아내기

- Parsing
	
	문장이 주어졌을 때, 문장의 구조 알아내기

- Machine Translation (MT)

	문장 번역하기

- Information Extraction (IE)

	자연어로 쓰인 보고서에서 구조화된 정보 뽑아내기

<br>

#### 여전히 어려운 문제

- Question Answering (QA)

	질의응답

- Paraphrase

	어떤 문장을 써놓고, 그 문장과 같은 뜻이지만 다른 형태로 표현하기

- Summariation

	아주 긴 문장을 한 단어 혹은 한 문장으로 요약하기

- Dialog

	대화하기

<br>

## 자연어 처리가 왜 어려운가요?

![i2](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i2.png)

- 모호성

	사람은 정확하게 말을 표현하지는 않지만, 그 의미를 완전히 파악할 수 있다.

- 비문 혹은 단어를 잘못 씀

	이 맥락에서 이 사람이 이 용어를 잘못 썼지만, 이런 뜻으로 했겠지라며 이해할 수 있다. 게다가, 요즘과 같은 SNS 환경에서 일부러 문법적으로 맞지 않는 문장을 쓰는 경우도 많다. 그리고 이런 경우가 매우 빨리 변하기 때문에 이걸 다 해결한다는게 쉽지 않다.

- 분절

	어디서 끊어읽어야하고, 어느 단어와 어느 단어를 합쳐야 하는지 판단하는 것이 어렵다.

- 관용어구

	있는 그대로 해석을 한다면, 실제로 의도한 의미를 제대로 전달할 수 없다.

- 신조어

	언어가 매우 빠르게 변하고 새로운 단어가 계속 나타나게 된다.

- 지식

	제대로 해석하기 위해서는 배경지식이 있어야한다.

- 고유명사

	위의 예시에서, `A Bug's Life` 는 영화 하나를 나타낸다. 그런데 이를 모른다면, 문장을 제대로 이해하는 것이 어려울 것이다.

{: .box-note}
결국, 언어가 매우 빠르게 변하므로 어렵다.

<br>

## QA

- Factoid Questions

	사실관계에 대한 질문이다. 이러한 경우, 단답형으로 답할 수 있을 것이다. 이 경우, 명사 하나 혹은 단어를 여러개 가진 명사로 답할 수 있을 것이다.

- Narrative Questions

	'\~을 설명해보시오', '왜 이렇게 했습니까?' 등은 단순히 단어 한두 개로 표현할 수 있는 것이 아니기 때문에, 매우 어렵다.

<br>

## Information Extraction (IE)

![i3](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i3.png)

이벤트 제목, 날짜, 언제부터 언제까지, 어디서 등 이메일 텍스트만 보고 자동으로 일정을 생성해주는 작업을 IE라고 볼 수 있다.

<br>

![i4](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i4.png)

IE와 관련된 것 중, 정보들에서 특별한 관계를 뽑아내는 기술도 있다. (Relation Extraction)

위의 예시에선, 자연어로 기술된 보고서에서 여러 관계 정보를 알아내는 것을 볼 수 있다. (IBM과 1911은 설립연도라는 관계로 맺어진다 등.)

<br>

![i5](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i5.png)

Sentiment Analysis 와 결합하여, 속성별로 리뷰에서 좋은 평인지 나쁜 평인지를 찾아내고, 거기서 키워드를 뽑아낸다.

<br>

## 감정 분석 (Sentiment Analysis)

![i6](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i6.png)

단순히 어떤 글이 긍정적인지 부정적인지만 알아내는 것이 목적일 수도 있다.

하지만 위의 연구 결과에서 보이듯이, 소비자가 얼마나 소비를 할 것인지에 대한 설문조사의 결과를 트위터의 사람들의 감정을 통해 예측할 수 있다는 것을 보여준다.

즉, 감정 분석의 목적은 아래와 같다.

- 단순히 긍정, 부정을 찾아내는 것

- 어떤 대상에 대한 글에서 나타나는 해당 대상에 대한 별점을 알아내는 것.

- 어떤 감정의 대상이 무엇이고, 감정의 근원이 무엇이며, 여러 속성별로 어떤 복잡한 반응을 가지고 있는지를 다 찾아내는 것.

- 등등

<br>

## 무엇이 감정 분석을 어렵게 만드나요?

- 비꼬는 문장

	사람조차도 알기 어렵다.

- 문장의 구조가 실제 말하고 싶은 부분보다 반대의 부분이 더 많은 경우

	부정적인 얘기를 하고 싶은데 처음에 그냥 좋은 얘기를 쭉 나열하는 것.

	EX) 영화 괜찮고 여러 가지 좋았는데 견딜 수가 없었다.

- 순서

	긍정적인 단어와 부정적인 단어의 순서에 따라 의미가 많이 바뀔 수 있다.

	EX) 어떤 배우는 평소처럼 특별한게 없었고, 놀랍게도 매우 뛰어난 배우인 이 사람이 별로 안 좋았다.

<br>

## Named Entity Recognition (NER)

고유명사를 찾아내는 것이 목적인 기술.

그 고유명사가 사람인지, 날짜인지, 위치인지 혹은 단체인지를 알아내는 것

EX) 맥락에 따라 'Labor' 이라는 단어가 노동이라 해석될 수도 있고, 정당이라 해석될 수도 있다.

뽑혀진 고유명사에 따라 문서로 정리, 인덱싱을 할 수도 있고, 어떤 회사 혹은 상품에 대한 감정을 하려면 이들을 기본적으로 다 찾아내야 한다.

이러한 작업은 IE에서도 필요하고 QA에서도 필요하다. 어떻게 보면 가장 기본적인 작업 중 하나이다.

<br>

## Part-Of-Speech (POS)

![i7](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i7.png)

[여기](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html)를 보면, 각 단어의 품사에 따라 태그가 있다.

예시로, 'Plays'는 상황에 따라 `NNS`와 `VBZ` 중, 3인칭 단수 현재형 동사를 뜻하는 `VBZ` 태그가 붙는다.

영어 같은 경우, 거의 모든 단어가 하나 이상의 품사를 가지고 있다. 그래서 각 단어가 어떻게 쓰이는 지를 주변 단어와 같이 봐서 결정을 해야하기 때문에, 쉽지만은 않은 문제이다.

<br>

## Parsing

![i8](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i8.png)

어떤 문장이 주어지면, 문법적인 구조를 알아내는 과정.

위의 예시에서, 'with a telescope' 와 'saw' 가 연결되었다면, '나는 저 소녀를 망원경으로 봤다.' 라는 뜻이 된다.

하지만, 'telescope' 와 'girl' 이 연결되어 있다고 하면, '나는 망원경을 가지고 있는 소녀를 봤다.' 라는 뜻이 된다.

이 문장 구조를 어떻게 나타내느냐에 따라 두 가지 관점에서 볼 수 있다.

1. 구성 요소로 나누기 (Constituency)

	![i9](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i9.png)

	문장이 주어지면 그를 여러 개의 구로 나누고, 구를 다시 여러 개의 구성요소로 나누는 것.

	- Distribution 

		- John talked [to the children] [about drugs].

		- John talked [about drugs] [to the children].

		위 두 문장을 보면, 'to the children' 과 'about drugs' 는 서로 위치가 바뀌어도 영어 문법 상 둘 다 맞다.

		그런 식으로 어떤 구성요소가 움직일 수 있다. 즉 분배가 될 수 있다고 한다면 그를 하나의 구성요소로 파싱해야 한다.

	- Substitution

		- I sat [on the box/right on top of the box/there].

		어떤 구성요소가 다른 구성요소로 치환이 가능하다면, 그게 하나의 구성요소로 파싱한다고 이해할 수 있다.

2. 종속 관계로 나누기 (Dependency)

	![i10](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i10.png)
	
	'I' 는 'saw' 에 종속되어 있고, 'a' 는 'girl' 이라는 명사에 종속되어 있다.

	이런 종속관계를 알아내는 관점으로 문장 구조를 해석한다.

	각 단어가 어디에 종속되어 있는지에 따라 의미가 바뀌기 때문에, 이를 파악하는 것도 아주 중요한 파싱의 관점이라 볼 수 있다.

<br>

## Word Meaning and Similarity

단어가 어떤 뜻으로 활용되었는지를 판단하는 과정

1. Homonymy(동형이의어)

	Bank 라는 단어가 은행이라는 뜻일 수도 있고, 강둑이라는 뜻일 수도 있다.

	이는 하나의 단어가 두 가지 서로 다른 뜻으로 해석된다기 보단, 원래 각각 근원의 단어가 있었으나, 이 둘이 알파벳이 같았다고 보는것이 더 타당하다.

	이 때문에 번역을 할 때도 어려워질 수 있고, 단어로부터 말을 만들어낼 때(Text-to-Speech)도 어렵다.

2. Polysemy

	영어 단어 하나가 여러 뜻을 갖는 경우가 많다.

	'Jane Austen'이라고 쓰면 이게 책의 저자를 얘기할 수도 있고, 그 저자의 작품을 얘기할 수도 있다.

3. Synonyms(동의어)

	같은 뜻을 가진 다른 말이 있다.

	하지만, 어떤 경우에서는 두 단어가 동의어인데 또 다른 경우에서는 동의어가 아닐 수도 있다.

	- EX) Big vs Large

		- How big is that plane? / Can I fly on a large or small plane? (동의어)

		- Miss Nelson became a kind of big/large sister to Benjamin (동의어가 아니다. 언니를 뜻하는 것일 수도 있고, 단순히 덩치가 더 큰 자매일 수도 있다.)

4. Antonyms(반대말)

	정확히 반대의 의미를 가지는 경우, 둘은 문법적으로 완전히 같다는 특징을 보인다.

<br>

## 기계번역(Machine Translation)

![i11](/assets/img/2020-11-01-bgm-ai-study-introduction-nlp/i11.png)

구글 번역기의 모델인 GNMT(Google Neural Machine Translation system)을 보면, 딥러닝을 기반으로 만들었다.

<br>

## Text Sumarization (요약)

1. Single-document Summarization

	아주 긴 기사가 있을 때, 그걸 한 문장으로 요약하는 등.

2. Multiple-document Summarization

	여러 문서를 참조하여 요약하는 것.

	EX) 간디의 일생에 대해서 요약을 하라, 어떤 사건에 대해 올해 초부터 현재까지 나온 기사를 스토리별로 요약하자 등

3. Generic Sumarization

	문서가 주어지면 그를 대표하는 문장 하나 혹은 여러 개의 문장으로 요약하는 것

4. Query-focused Summarization

	사용자가 어떤 질의를 주면, 그것에 기반하여 요약하는 것.

	영화를 요약할 때도 인물 중심, 사건 중심, 관계 중심 등 여러 가지 요약을 할 수 있다.

5. Extractive Summarization

	주어진 문서에서 특정 구 혹은 단어를 뽑아가면서 요약하는 것.

6. Abstractive Summarization

	전체 글을 다 이해한 후에 해당 글을 하나로 요약하는 것.

	그 글에서 사용된 단어 뿐 아니라, 새로운 단어나 표현을 활용하여 요약하는 과정.

<br>

---

<br>

이 글은 [부산 개발자 모임(BGM)](https://cafe.naver.com/busandevelopers)에서 진행하고 있는 AI 개론 스터디에서 배운 내용을 기반으로 작성되었습니다.

해당 스터디는 [K-MOOC 인공지능의 기초 강좌](http://www.kmooc.kr/courses/course-v1:SNUk+SNU048_011k+2020_T2/about)의 내용을 기반하여 진행하며, 글에서 나온 모든 출처가 명시되지 않은 이미지는 해당 강좌에서 나왔음을 밝힙니다.