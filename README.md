# AI Systems Brain

AI를 더 잘 쓰는 법보다, AI 시스템이 어떻게 구현되고 어디서 병목이 생기는지를 이해하기 위한 개인 지식 저장소입니다.

목표는 거창한 공부 노트가 아니라, 하루 10분이라도 꾸준히 남길 수 있는 가벼운 지식 저장소를 만드는 것입니다. 1주에 많아야 4~5시간 정도 쓴다는 현실을 전제로, 부담 없이 적고 가끔만 정리합니다.

이 저장소의 방향은 분명합니다. AI를 잘 쓰는 요령보다 LLM, agent, inference, GPU, distributed systems, observability, platform engineering이 실제 시스템에서 어떻게 맞물리는지 이해합니다.

중요한 점은 이 저장소가 LLM에만 국한된 저장소가 아니라는 것입니다. LLM은 지금 가장 좋은 진입점일 뿐이고, 핵심 주제는 AI workload가 실제 컴퓨터 시스템 위에서 어떻게 실행되고, 어디서 병목이 생기며, 어떤 구조로 더 빠르고 안정적으로 운영되는지입니다.

따라서 이 저장소는 LLM inference뿐 아니라 agent runtime, model serving, GPU/NPU, distributed training, data pipeline, vector search/RAG, multimodal serving, AI accelerator architecture까지 넓게 다룹니다. 중심 질문은 언제나 같습니다.

> AI를 어떻게 잘 쓰는가보다, AI가 시스템 위에서 어떻게 동작하고 어디서 막히는가?

## 디렉터리 구조

```text
ai-systems-brain/
├── README.md
├── 00-career/
│   ├── index.md
│   └── roadmap.md
├── 01-fundamentals/
│   └── index.md
├── 02-llm/
│   └── index.md
├── 03-ai-systems/
│   └── index.md
├── 04-labs/
│   └── index.md
├── 05-open-source/
│   └── index.md
├── 90-questions/
│   └── index.md
├── 99-daily/
│   └── index.md
└── templates/
    ├── concept.md
    ├── daily-note.md
    └── incident-analysis.md
```

## 각 영역의 역할

- `00-career`: 커리어 방향, 목표, 회고, 로드맵을 기록합니다.
- `01-fundamentals`: Linux, OS, network, database, distributed systems, computer architecture 같은 기반 지식을 정리합니다.
- `02-llm`: Transformer, attention, tokenization, KV cache, sampling, context window 같은 LLM 핵심 개념을 정리합니다. 단, LLM은 AI systems로 들어가기 위한 진입점으로 봅니다.
- `03-ai-systems`: vLLM, inference serving, batching, GPU scheduling, model serving, observability 같은 AI 시스템 주제를 다룹니다.
- `04-labs`: 공부 중 궁금한 현상을 확인하기 위한 짧은 실험, benchmark, 장애 분석을 기록합니다.
- `05-open-source`: vLLM, OpenHands, LangGraph, MCP, KServe 등 읽어볼 오픈소스와 기여 후보를 관리합니다.
- `90-questions`: 아직 답을 모르는 질문만 모읍니다.
- `99-daily`: 매일 또는 매주 배운 점, 이해한 단서, 다음 질문을 기록합니다.
- `templates`: 반복해서 사용할 노트 템플릿을 보관합니다.

## 노트 작성 원칙

1. 하루 기록은 짧아도 됩니다.
   - 3줄만 적어도 성공입니다. "오늘 본 것", "이해한 것", "남은 질문"이면 충분합니다.

2. 설명보다 질문에서 시작합니다.
   - "KV cache란 무엇인가?"보다 "왜 KV cache가 inference latency를 줄이면서 GPU memory를 많이 쓰게 만드는가?"처럼 적습니다.

3. 개념은 가능하면 병목과 연결합니다.
   - 개념을 외우는 것이 아니라, 어떤 성능 문제를 설명하기 위해 필요한지 기록합니다.

4. 나중에 다시 이해할 수 있게 적습니다.
   - 특정 상황을 그대로 외우기보다 timeout, retry, scheduling, memory, throughput, latency, observability처럼 다른 개념과 연결되는 단서를 남깁니다.

5. 실험은 선택입니다.
   - 모든 노트에 실험을 붙이려 하지 않습니다. "나중에 직접 확인하면 좋겠다" 정도의 단서만 있어도 됩니다.

6. 완벽한 글보다 다시 돌아올 수 있는 단서를 남깁니다.
   - 처음부터 블로그처럼 쓰지 않아도 됩니다. 미래의 내가 이어서 팔 수 있으면 충분합니다.

## 노트의 세 가지 상태

모든 노트를 완성된 문서로 만들 필요는 없습니다.

- `seed`: 질문, 링크, 한 줄 메모만 있는 상태
- `note`: 대략 이해한 내용을 정리한 상태
- `essay`: 블로그나 발표 자료로 바꿀 수 있을 만큼 정리된 상태

대부분의 노트는 `seed`나 `note`에 머물러도 괜찮습니다.

## 링크 방식

노트 사이에는 상대 경로 링크를 사용합니다.

예시:

```markdown
- [KV Cache](../02-llm/kv-cache.md)
- [GPU Memory](../03-ai-systems/gpu-memory.md)
- [Batching](../03-ai-systems/batching.md)
```

문서 하단에는 가능한 한 `관련 개념` 섹션을 둡니다. 시간이 지나면 개별 노트가 하나의 지식 그래프처럼 연결됩니다.

## 현실적인 주간 루틴

기본 전제는 1주에 4~5시간입니다. 바쁜 주는 1시간만 해도 유지한 것입니다.

### 평일 10분

1. 오늘 업무나 공부에서 나온 질문을 하나 적습니다.
2. 이해한 내용을 3줄 이내로 적습니다.
3. 다음에 볼 링크나 키워드를 하나 남깁니다.

### 주 1회 30분

1. `99-daily`에서 이번 주 기록을 훑습니다.
2. 계속 신경 쓰이는 질문 1개만 고릅니다.
3. 필요하면 `90-questions/index.md`나 관련 디렉터리의 `index.md`에 옮깁니다.
4. 개념 노트로 승격할지는 선택합니다.

### 여유 있는 주 1~2시간

1. 개념 하나를 `templates/concept.md`로 정리합니다.
2. 작은 실험 하나를 해봅니다.
3. 글이 좋아지면 블로그/발표 후보로 표시합니다.

핵심 질문은 항상 같습니다.

> 나는 AI를 더 잘 쓰는 법을 배우고 있는가, 아니면 AI 시스템이 왜 그렇게 동작하는지를 이해하고 있는가?
