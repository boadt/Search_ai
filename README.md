# Search_ai
# Agent 구현해서 간단한 Chatbot 만들어보기

> **목적** Agent에 대해서 학습하고, 그 내용을 바탕으로 실습하기. <br>
> **작성일** 2025.6.20.

---

## 1. 서론

![Uploading ChatGPT Image 2025년 6월 26일 오후 08_30_49.png…]()
![Uploading ChatGPT Image 2025년 6월 26일 오후 08_30_49.png…]()
![Uploading ChatGPT Image 2025년 6월 26일 오후 08_30_49.png…]()
![Uploading ChatGPT Image 2025년 6월 26일 오후 08_30_49.png…]()

최근 AI 분야에서 단순한 질의응답을 넘어, 복잡한 작업을 스스로 계획하고 수행하는 Agent 시스템이 주목받고 있다.
LangChain이나 LangGraph, ReAct 같은 프레임워크를 접하며 Agent의 개념과 활용 가능성에 흥미를 느껴 학습하게 되었다.

이 글에서는 Agent의 개념을 정리하고, 이를 바탕으로 간단한 챗봇을 직접 구현해본 과정을 공유하고자 한다.

---

## 2. AI Agent란?


 | Workflows |Agents|
 |-----------|------|
 |미리 정의된 코드 경로를 통해 LLM과 Tool이 운영되는 시스템|LLM이 자신의 프로세스와 Tool 사용을 동적으로 지시하고 컨트롤하는 시스템|

일반적인 RAG를 구현하기 위해서 질문의 관련된 문서를 찾고 그 문서를 기반으로 답변을 생성한다는 흐름을 미리 Workflows에 정의를 해 두었다면, Agents는 어떤 동작을 진행할지 LLM 스스로 판단할 수 있다.
하지만 결국 둘다 LLM의 개입이 진행되므로, 둘을 통틀어서 **Agentic System**이라고 부름 

---

## 3. Router
<ul>
  <li>
    Router는 LLM이 다음에 어떤 단계를 취할 지 결정하는 역할
  </li>
  <li>
    여러 Tool중 어떤 Tool을 선택할 지 등 <strong>선택</strong>을 나타내는 구조
  </li>
</ul><br>

**Agent**는 동적으로 LLM이 판단을하고 동작들을 스스로 판단한다는 것인데, 예를 들어 문서검색 후에 다시 검색을 한다거나 다시 작성해야할지 새롭게 답변을 생성해야 할지 판단들을 스스로 진행하는 것이다.

---

## 4. ReAct(Reasoning and Acting)

* **ReAct**란 추론(Reasoning)과 행동(Acting)을 언어 모델에 결합하여 복잡한 문제를 해결하기 위한 방법
* **Thought(사고)** ➜ **Action(행동)** ➜ **Observation(관찰)** <br>

LLM이 다음 동작을 위해 스스로 사고하는 과정을 추가해 의미없는 행동을 줄여줌

---

참고 : https://youtu.be/t4RdOgUReKo?si=eqWXrMrMy1egb6ln, https://www.anthropic.com/engineering/building-effective-agents


 
