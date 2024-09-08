---
categories: 
 - LLM_RAG
layout: single
title: "(LLM_RAG) LangChain 구성"
---

# Ice Breaker

# Project Setup
 -  Clone Starting Branch
    -  [https://github.com/emarco177/ice_breaker/tree/1-start-here](https://github.com/emarco177/ice_breaker/tree/1-start-here)
 -  Create pipenv environment
 -  Install LangChain
 -  Write boilerplate code
 -  Setup vscode Runner

```python
pipenv shell

pipenv install langchain
pipenv install langchain-community
pipenv install langchain-openai
pipenv install langchain-langchainhub
```

# The GIST of LangChain (Simple application)
  - [LangChain Quickstart](https://python.langchain.com/v0.1/docs/get_started/quickstart/)
## PromptTemplate
  - 프롬프트의 기본 틀을 정의하는 클래스
  - 언어 모델에 입력으로 전달될 프롬프트를 구조화하고 커스터마이즈할 수 있게 해줌
  - 이 틀은 변수화된 형태로 구성되며, 여러 상황에 맞게 변수를 동적으로 바꿔가며 사용할 수 있음<br>
    ex) 하나의 프롬프트 템플릿에서 여러 문장을 생성하거나 다양한 사용자 입력에 따라 프롬프트를 변경할 수 있음 

### 주요 특징
1. 변수화된 프롬프트: 프롬프트 안에 {}로 변수 자리를 지정할 수 있으며, 실행 시점에 해당 변수를 채워넣는 방식으로 프롬프트가 동적으로 생성됨
2. 유연성: 다양한 변수를 쉽게 조작할 수 있어, 상황에 맞게 프롬프트를 자동으로 수정하거나 업데이트할 수 있음
3. 재사용 가능성: 하나의 템플릿을 여러 작업에서 재사용할 수 있어 코드 중복을 줄이고 유지보수를 쉽게 함

### PromptTemplate 사용 예시
```python
from langchain.prompts import PromptTemplate

# 프롬프트 템플릿 정의
template = "Write a {adjective} story about a {subject}."
prompt = PromptTemplate(
    input_variables=["adjective", "subject"],  # 변수들 정의
    template=template  # 템플릿 지정
)

# 변수 값으로 프롬프트 생성
prompt_text = prompt.format(adjective="funny", subject="robot")
print(prompt_text)
```
위 예제에서, template은 "Write a {adjective} story about a {subject}."로 정의되며, adjective와 subject라는 변수에 각각 "funny"와 "robot"을 대입하여 최종 프롬프트가 "Write a funny story about a robot."으로 출력됩니다.

## ChatModel
  - LLM 주변의 wrapper로 상호작용을 돕는 것
  - 자연어 처리(NLP)에서 대화형 AI 시스템을 구축하는 데 사용되는 언어 모델의 한 형태
  - 인간과 자연스러운 대화를 주고받을 수 있도록 설계되었으며, 일반적인 질의응답 시스템에서부터 고도화된 대화형 애플리케이션까지 다양한 용도로 사용
  - 최근에 널리 사용되는 언어 모델, 예를 들어 GPT 시리즈(예: GPT-4)도 이 카테고리에 속함

`Chat model`은 자연어 처리(NLP)에서 대화형 AI 시스템을 구축하는 데 사용되는 언어 모델의 한 형태입니다. 이 모델은 인간과 자연스러운 대화를 주고받을 수 있도록 설계되었으며, 일반적인 질의응답 시스템에서부터 고도화된 대화형 애플리케이션까지 다양한 용도로 사용됩니다. 최근에 널리 사용되는 언어 모델, 예를 들어 GPT 시리즈(예: GPT-4)도 이 카테고리에 속합니다.

### 주요 개념

1. **대화 맥락 유지**: Chat model의 가장 중요한 특징 중 하나는 대화의 문맥을 이해하고 유지하는 능력입니다. 이 모델은 대화를 시작한 후, 이전에 했던 질문과 답변을 기억하고 그에 따라 적절한 답변을 제공합니다. 이는 단순한 질의응답 모델과의 차이점입니다.
   
2. **다양한 태스크 처리**: Chat model은 단순히 질문에 답변하는 것을 넘어서, 다양한 대화형 태스크를 처리할 수 있습니다. 예를 들어:
   - 질의응답
   - 텍스트 생성
   - 번역
   - 요약
   - 코딩 도우미 역할
   - 창의적인 글쓰기 등
   
3. **프롬프트의 중요성**: Chat model은 주어진 입력(프롬프트)을 통해 응답을 생성합니다. 프롬프트는 모델에게 "어떻게" 대답할지를 지시하는 역할을 합니다. 좋은 프롬프트는 모델이 더 적절하고 유용한 응답을 생성하는 데 중요한 역할을 합니다.

4. **세션 기반 대화**: 일반적으로 Chat model은 세션 기반으로 동작하여 여러 턴의 대화를 통해 사용자와 상호작용합니다. 이를 통해 대화는 더 연속적이고 일관성 있게 진행될 수 있습니다. 세션이 끝나면 대화 내역은 초기화되지만, 각 세션 내에서는 문맥이 유지됩니다.

### Chat model의 구조

Chat model의 내부 구조는 대개 **Transformer** 기반의 아키텍처를 따릅니다. 이 구조는 문맥을 이해하고 장기적인 의존성을 유지하는 데 탁월한 성능을 보입니다. 주요 구조적 특징은 다음과 같습니다.

1. **Encoder-Decoder 구조**: 일부 모델은 인코더-디코더 구조를 사용하여 입력된 문장을 인코딩하고, 그에 대한 적절한 응답을 생성합니다.
   
2. **자연어 이해(NLU)와 자연어 생성(NLG)**: Chat model은 자연어 이해와 자연어 생성 모두를 수행할 수 있습니다. 즉, 주어진 질문을 이해하고, 그에 대한 적절한 답변을 생성합니다.

3. **사전 학습**: 대부분의 Chat model은 방대한 양의 텍스트 데이터를 바탕으로 사전 학습됩니다. 이 사전 학습을 통해 모델은 언어의 다양한 규칙, 상식, 그리고 실제 대화에서 필요한 패턴을 학습하게 됩니다.

4. **미세 조정(Fine-Tuning)**: Chat model은 특정한 용도에 맞게 미세 조정될 수 있습니다. 예를 들어, 고객 지원, 기술 상담, 법률 자문 등 특정 분야에 맞게 학습된 모델이 있습니다.

### Chat model의 응용

1. **챗봇**: 고객 서비스, 기술 지원, 쇼핑 도우미 등에서 사용되는 챗봇은 Chat model의 대표적인 응용입니다.
   
2. **언어 학습 도우미**: 사용자에게 피드백을 주거나 대화 연습을 통해 외국어 학습을 도와줍니다.

3. **창작 도우미**: 글쓰기, 시나리오 작성, 음악 가사 생성 등 창의적인 작업을 지원합니다.

4. **코딩 도우미**: 프로그래밍 언어에 대한 질문에 답하거나 코드 생성 및 디버깅을 도와주는 용도로도 사용됩니다.

Chat model은 사람과 자연스러운 상호작용을 제공할 수 있는 매우 강력한 도구로, 다양한 산업 분야에서 유용하게 활용되고 있습니다.



## Chains

`Chains`는 LangChain에서 제공하는 기능으로, 다양한 작업을 여러 단계를 거쳐 체계적으로 수행할 수 있도록 만든 일종의 워크플로우입니다. 각 단계는 개별적인 모듈로 구성될 수 있으며, 이 모듈들이 연속적으로 실행되어 복잡한 작업을 처리합니다. 쉽게 말해, **여러 개의 작업을 순차적으로 연결하여 실행하는 것**입니다.

### `Chains`의 기본 개념

`Chains`는 하나 이상의 구성 요소를 연결해, 복합적인 프로세스를 자동화하거나 더 복잡한 태스크를 처리할 수 있도록 합니다. 예를 들어, **하나의 입력을 받아서 가공하고**, 그 결과를 다음 단계로 넘겨주는 방식으로 작동합니다. 각 단계는 LangChain의 다양한 모듈(예: 프롬프트 템플릿, 언어 모델 호출, 도구 사용 등)로 구성될 수 있습니다.

### `Chains`의 유형

1. **단일 체인(Simple Chain)**: 입력을 받아 하나의 작업을 수행한 후 결과를 반환하는 기본적인 형태입니다.
   - 예: 질문에 대한 답변을 생성하고, 그 답변을 출력하는 간단한 질의응답 체인.

2. **다중 체인(Sequential Chain)**: 여러 작업을 순차적으로 실행하며, 각 단계의 출력이 다음 단계의 입력으로 사용됩니다.
   - 예: 사용자의 질문을 받아, 먼저 관련된 정보를 검색한 후, 그 정보를 바탕으로 답변을 생성하는 체인.

3. **병렬 체인(Parallel Chain)**: 여러 작업을 동시에 처리하여 각각의 결과를 병합하거나 특정 방식으로 결합하는 방식입니다.
   - 예: 하나의 입력을 받아 여러 언어 모델로 처리한 결과를 비교하는 방식.

4. **브랜칭 체인(Branching Chain)**: 조건에 따라 다른 체인을 실행하는 방식으로, 분기점이 존재하는 체인입니다.
   - 예: 특정 조건을 만족하는 경우에는 정보를 검색하고, 그렇지 않으면 직접 답변을 생성하는 방식.

### `Chains` 사용 예시

다음은 간단한 `Sequential Chain`을 사용하는 예시입니다.

```python
from langchain.prompts import PromptTemplate
from langchain.chains import LLMChain
from langchain.llms import OpenAI

# 두 개의 프롬프트 템플릿 정의
template_1 = "What is a good name for a company that makes {product}?"
template_2 = "Write a tagline for a company named {company_name}."

# LLM 체인 설정
llm = OpenAI(model_name="text-davinci-003")

# 첫 번째 체인: 회사 이름을 생성하는 체인
prompt_1 = PromptTemplate(input_variables=["product"], template=template_1)
chain_1 = LLMChain(llm=llm, prompt=prompt_1)

# 두 번째 체인: 생성된 회사 이름을 바탕으로 태그라인을 만드는 체인
prompt_2 = PromptTemplate(input_variables=["company_name"], template=template_2)
chain_2 = LLMChain(llm=llm, prompt=prompt_2)

# 전체 체인을 순차적으로 실행하는 방법
from langchain.chains import SimpleSequentialChain

overall_chain = SimpleSequentialChain(chains=[chain_1, chain_2])

# 입력을 받아 순차적으로 실행
tagline = overall_chain.run("artificial intelligence software")
print(tagline)
```

이 예시는 다음과 같은 두 개의 작업을 순차적으로 실행하는 체인입니다:
1. 입력된 제품을 바탕으로 회사 이름을 생성.
2. 생성된 회사 이름을 바탕으로 태그라인(tagline)을 작성.

이와 같은 방식으로, `Chains`는 더 복잡한 작업들을 자동화하는 데 사용될 수 있습니다.

### 주요 구성 요소

- **LLMChain**: 언어 모델을 호출하는 작업을 포함하는 체인. 주로 프롬프트 템플릿과 연계하여 사용됩니다.
- **SequentialChain**: 여러 개의 체인을 순차적으로 실행하는 체인.
- **Custom Chains**: 사용자가 필요에 따라 직접 정의한 체인을 생성할 수 있습니다.

### `Chains`의 응용

1. **정보 검색 및 생성**: 먼저 정보를 검색하고, 그 결과를 바탕으로 답변을 생성하는 체인.
2. **멀티모달 체인**: 텍스트, 이미지, 오디오 등의 여러 데이터를 동시에 처리하는 체인.
3. **분석 및 요약**: 복잡한 텍스트 데이터를 분석하고, 그 결과를 요약하는 체인.

`Chains`는 복잡한 작업을 여러 단계로 분리하여 효율적으로 처리할 수 있는 방법을 제공합니다. 이를 통해 대화형 AI 모델이나 정보 검색 시스템을 보다 유연하고 강력하게 만들 수 있습니다.

## Agents

**Agents**는 특정 작업을 수행하기 위해 주어진 입력에 따라 다양한 도구와 함수를 동적으로 호출하는 시스템입니다. LangChain에서의 Agents는 언어 모델이 특정 작업을 수행하기 위해 여러 개의 도구를 조합하여 사용할 수 있게 해줍니다. 이때, 언어 모델은 단순한 응답 생성을 넘어, 주어진 목표를 달성하기 위해 필요한 일련의 액션을 계획하고 실행하게 됩니다.

### Agents의 구성 요소

1. **Agent**: Agent는 주어진 목표를 달성하기 위해 다양한 도구를 활용할 수 있는 주체입니다. 사용자는 Agent에게 자연어로 목표를 제공하면, Agent는 이 목표를 달성하기 위한 일련의 액션을 결정합니다.

2. **Tool**: Tool은 Agent가 작업을 수행하는 데 사용하는 함수, API, 데이터베이스 등의 도구입니다. 예를 들어, 특정 데이터를 조회하기 위해 데이터베이스에 질의하거나, 계산을 수행하기 위해 계산기를 호출하는 등의 역할을 합니다.

3. **Toolkit**: Toolkit은 여러 개의 Tool을 묶어 하나의 패키지로 만든 것입니다. Agent는 필요에 따라 다양한 Toolkits를 사용할 수 있습니다.

4. **Action**: Action은 Agent가 수행하는 구체적인 작업 단위입니다. 이는 특정 Tool을 사용하여 어떤 작업을 실행하거나, 결과를 평가하는 등의 행위를 포함합니다.

### Agents의 작동 원리

1. **입력 분석**: 사용자가 Agent에게 질문이나 목표를 제공하면, Agent는 이를 분석하여 작업의 성격을 파악합니다.

2. **계획 수립**: Agent는 목표를 달성하기 위해 어떤 도구들을 사용할지, 어떤 순서로 사용할지를 계획합니다.

3. **Action 실행**: 계획에 따라 Agent는 순차적으로 Action을 실행합니다. 이 과정에서 각 Action은 필요한 Tool을 호출하고, 그 결과를 바탕으로 다음 Action을 결정합니다.

4. **결과 반환**: 모든 Action이 완료되면, Agent는 최종 결과를 사용자에게 반환합니다.

### 예시

예를 들어, 사용자가 "다음 주 날씨를 알려주고, 그에 맞춰 옷차림을 추천해줘"라고 Agent에게 요청한다고 가정해봅시다. 이 경우 Agent는 다음과 같은 일련의 작업을 수행할 수 있습니다.

1. 날씨 API를 호출하여 다음 주 날씨 정보를 얻음.
2. 얻은 날씨 정보를 분석하여 특정 날짜에 대한 날씨를 파악함.
3. 날씨에 맞는 옷차림을 추천하는 함수를 호출함.
4. 최종적으로 날씨 정보와 옷차림 추천 결과를 사용자에게 제공함.

LangChain의 Agents는 이러한 복잡한 작업을 언어 모델과 도구들의 조합을 통해 자동화할 수 있도록 돕는 강력한 기능입니다.