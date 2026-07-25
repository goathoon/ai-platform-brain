# Roadmap

## 목표

기존 서버 개발자의 분산 시스템, 성능 분석, 장애 대응 경험을 기반으로 LLM과 agent workload의 실행 경로를 관찰하고 병목을 찾아 개선하는 AI Runtime / Serving Platform Engineer가 됩니다.

모델을 직접 연구하는 것보다 모델 요청이 gateway, queue, runtime, model server, GPU, tool을 거치는 전체 과정에 집중합니다. 최종적으로 latency, throughput, memory, utilization, reliability, cost, quality의 관계를 수치로 설명하고 개선할 수 있어야 합니다.

## 목표 포지셔닝

```text
Backend Engineer
  -> Platform / Reliability 역량 강화
  -> LLM Inference와 Agent Runtime 이해
  -> AI Runtime / Serving Platform Engineer
  -> AI Infrastructure / Systems Engineer
```

이 로드맵의 주력 분야는 `Inference Platform & Reliability`입니다.

- 주력: LLM gateway, inference serving, agent runtime, observability, reliability, performance engineering
- 기반: Linux, network, distributed systems, Kubernetes, cloud, CI/CD, infrastructure as code
- 필요한 만큼 학습: Transformer inference, GPU architecture, model lifecycle, evaluation
- 당장은 주변 영역: training platform, feature store, 대규모 data pipeline, accelerator kernel 최적화

## 학습 원칙

### 1. 서버 개발 경험에서 출발합니다

기존 개념을 버리고 새로 시작하지 않습니다.

| Backend 관점 | AI platform 관점 |
| --- | --- |
| request latency | E2E latency, TTFT, inter-token latency |
| RPS/TPS | requests/sec, input/output tokens/sec |
| queue와 thread pool | request queue, batching, scheduler |
| memory pressure | model weight, activation, KV cache, GPU memory |
| cache hit rate | prefix/prompt/KV cache hit rate |
| load balancing | model/replica/provider routing |
| timeout과 retry | model/tool/provider timeout과 retry |
| graceful degradation | smaller model, provider fallback |
| distributed tracing | gateway-agent-tool-model trace |
| capacity planning | GPU capacity, token throughput, cost |

### 2. 설명보다 측정 가능한 결과를 남깁니다

개념을 이해했다는 기준은 용어를 설명하는 것이 아닙니다.

1. workload와 가설을 정의합니다.
2. metric, trace, profile로 병목 후보를 좁힙니다.
3. 설정이나 구조를 변경합니다.
4. 변경 전후를 같은 조건에서 측정합니다.
5. 성능, 안정성, 비용, 품질의 trade-off를 기록합니다.
6. 같은 문제가 재발하지 않도록 test, alert, deploy gate 중 하나로 자동화합니다.

### 3. 하나의 학습 환경에서 질문을 누적합니다

완성된 제품이나 포트폴리오를 만드는 것을 목표로 삼지 않습니다. 필요할 때 다시 실행할 수 있는 작은 `AI Runtime Lab`을 유지하고, 공부하다 생긴 질문을 코드와 실험으로 확인합니다.

각 실험은 독립적이어도 됩니다. 이전 실험의 gateway, 부하 생성기, metric 수집 환경을 재사용할 수 있을 때만 자연스럽게 연결합니다. 학습을 위해 필요하지 않은 기능은 만들지 않습니다.

### 4. 실험은 필수이고 노트는 보조입니다

권장 시간 배분은 다음과 같습니다.

- 구현, 운영, 측정: 60%
- 공식 문서와 오픈소스 코드 읽기: 20%
- 개념 학습: 10%
- 노트와 글쓰기: 10%

## 핵심 질문

- AI 요청의 E2E latency는 gateway, queue, prefill, decode, tool 중 어디에서 증가하는가?
- 평균 latency는 정상인데 tail latency가 나빠지는 이유는 무엇인가?
- input/output token 길이와 concurrency는 처리량과 latency를 어떻게 바꾸는가?
- batching은 언제 throughput을 높이고 언제 queue time을 악화시키는가?
- GPU utilization이 낮을 때 실제 병목은 CPU, memory, network, scheduler 중 어디인가?
- KV cache는 latency를 줄이는 대신 얼마만큼의 memory pressure를 만드는가?
- retry와 fallback은 장애를 복구하는가, 아니면 부하를 증폭시키는가?
- agent의 tool call을 어떻게 추적하고 중단된 실행을 안전하게 재개하는가?
- 모델과 설정 변경으로 성능이 좋아졌을 때 품질 회귀는 어떻게 검출하는가?
- platform 사용자가 안전하게 배포할 수 있도록 어떤 API와 기본값을 제공해야 하는가?

## 지식 축과 우선순위

### 1. Performance and Reliability Fundamentals

- Linux process, thread, memory, file system, network
- concurrency, queueing, backpressure, load shedding
- timeout, retry, circuit breaker, idempotency
- latency distribution, percentile, coordinated omission
- profiling, benchmarking, capacity planning
- SLI, SLO, alert, incident response, runbook

### 2. Platform Engineering

- container, image, registry
- Kubernetes workload, network, storage, scheduler
- Helm 또는 Kustomize
- 하나의 public cloud
- Terraform과 infrastructure as code
- CI/CD, canary, rollback, GitOps
- authentication, RBAC, secret, quota, multi-tenancy
- Prometheus, Grafana, OpenTelemetry

### 3. LLM Inference Fundamentals

- tokenization과 token 단위 비용
- Transformer와 attention의 데이터 흐름
- training과 inference의 차이
- autoregressive generation
- prefill과 decode
- KV cache와 context length
- sampling과 streaming
- FP32, FP16, BF16, INT8/INT4
- quantization과 quality/performance trade-off
- batching과 continuous batching
- tensor, device, model artifact에 대한 PyTorch 기초

목표는 수식을 전개하거나 새 모델을 설계하는 것이 아닙니다. 다음 질문을 시스템 관점에서 설명하고 실험으로 확인할 수 있으면 됩니다.

- attention과 긴 context가 계산량과 memory 사용량을 왜 늘리는가?
- decode가 순차적이라는 특성이 serving throughput에 어떤 제약을 만드는가?
- KV cache가 왜 latency를 줄이면서 동시 처리 가능한 요청 수를 제한하는가?
- precision과 quantization이 memory, latency, throughput, quality에 어떤 영향을 주는가?

### 4. Runtime and Serving Platform

- LLM gateway와 OpenAI-compatible API
- model/provider routing
- streaming, timeout, retry, fallback
- rate limit, quota, admission control
- vLLM과 inference server request lifecycle
- queueing, scheduling, continuous batching
- model loading, cold start, versioning
- autoscaling, canary, rollback, shadow traffic
- request/model/tool/GPU 단위 observability
- 성능 및 품질 regression gate

### 5. Agent Runtime

- tool registry와 tool execution policy
- execution state와 checkpoint
- idempotency, retry, timeout
- durable workflow와 resume
- human approval과 permission boundary
- context 관리와 실행 이력
- agent/tool/model trace

Agent의 지능을 높이는 것보다 장시간 실행을 안전하고 관측 가능하게 만드는 데 집중합니다.

### 6. GPU and Compute Basics

- GPU execution model의 기초
- VRAM, HBM, memory bandwidth
- PCIe와 CPU-GPU data movement
- GPU utilization과 memory utilization의 차이
- OOM, fragmentation, model weight, KV cache
- multi-GPU와 tensor parallelism의 기본

초기 목표는 kernel을 직접 최적화하는 것이 아니라 GPU가 병목인지, 다른 계층이 GPU를 놀게 만드는지 구분하는 것입니다.

## 학습 환경: AI Runtime Lab

`AI Runtime Lab`은 완성해야 하는 프로젝트가 아니라 개념을 직접 확인하기 위한 개인 실험실입니다. 처음부터 전체 구성을 만들지 않고, 현재 질문에 필요한 부분만 준비합니다.

### 환경 1. Request Path 관찰

- 간단한 LLM gateway 또는 proxy
- streaming response
- metrics, logs, distributed trace
- timeout, retry, fallback을 관찰할 수 있는 failure injection
- token usage와 latency 기록

이 환경으로 E2E latency, streaming, timeout, retry가 요청 경로에 미치는 영향을 공부합니다.

### 환경 2. Inference 관찰

- Ollama 또는 vLLM 기반 model serving
- workload별 load test
- TTFT, inter-token latency, throughput, queue time 측정
- context length, concurrency, batch 설정 실험
- GPU memory와 KV cache 관찰
- quantization별 성능, memory, quality 비교

이 환경으로 Transformer inference, prefill/decode, KV cache, batching이 실제 성능 현상으로 어떻게 나타나는지 공부합니다.

### 환경 3. Runtime Reliability 관찰

- tool call을 포함한 간단한 agent execution
- tool timeout, retry, idempotency
- execution state, checkpoint, resume
- agent/tool/model trace
- queue, rate limit, admission control

이 환경으로 장시간 실행과 외부 의존성이 있는 AI workload의 실패 및 복구 방식을 공부합니다.

### 필요할 때만 추가하는 운영 환경

- Kubernetes와 Helm
- Terraform과 CI/CD
- autoscaling, canary, rollback
- quota와 multi-tenancy
- SLO, alert, runbook

이 도구들은 체크리스트를 채우기 위해 붙이지 않습니다. 현재 공부하는 질문이 단일 프로세스나 로컬 환경에서 설명되지 않을 때만 사용합니다.

## 24개월 실행 계획

### 0~3개월: 서버 성능 분석 기반을 계측 가능한 형태로 만들기

- latency percentile, queueing, backpressure, retry amplification을 실험합니다.
- 작은 backend service에 metrics, trace, profile, SLO를 적용합니다.
- 간단한 LLM request path를 만들고 구간별 latency를 관찰합니다.

점검 기준:

- 요청 경로를 trace로 분해할 수 있습니다.
- 부하 증가에 따른 p50/p95/p99와 queue 변화를 설명할 수 있습니다.
- timeout, retry, fallback의 동작을 test로 검증합니다.

### 4~6개월: LLM inference 원리를 성능 현상과 연결하기

- tokenization, attention, prefill/decode, KV cache, batching을 학습합니다.
- Ollama 또는 vLLM으로 input/output 길이와 concurrency 실험을 수행합니다.
- 결과를 benchmark report로 남깁니다.

점검 기준:

- TTFT, inter-token latency, tokens/sec를 구분해 측정합니다.
- context length와 concurrency가 latency와 memory에 미치는 영향을 그래프로 설명합니다.
- 병목에 대한 가설을 최소 2개 이상 실험으로 검증합니다.

### 7~12개월: Self-hosted Inference의 분석 범위 넓히기

- vLLM serving을 gateway와 연결합니다.
- workload를 바꾸며 queue, batching, memory, tail latency를 분석합니다.
- 필요할 경우에만 Kubernetes, autoscaling, canary, rollback을 실험합니다.
- 장애를 주입해 metric과 trace에서 어떤 신호가 나타나는지 확인합니다.

점검 기준:

- 다른 workload에서도 같은 측정 과정을 반복할 수 있습니다.
- 설정 변경 전후의 차이를 수치로 설명할 수 있습니다.
- 장애 증상에서 원인 후보를 좁히는 과정을 기록합니다.

### 13~18개월: Inference Reliability를 깊게 다루기

- continuous batching, queueing, tail latency를 실험합니다.
- model loading, cold start, memory pressure를 분석합니다.
- 성능과 품질 regression을 배포 전에 검출합니다.
- runtime/serving 관련 오픈소스의 request path를 읽습니다.

점검 기준:

- 복합 부하에서 발생한 병목을 E2E로 추적하고 개선합니다.
- benchmark 조건과 한계를 다른 사람이 이해할 수 있게 기록합니다.
- 관심이 이어진다면 관련 오픈소스의 문서, test, issue, bug fix에 참여합니다.

### 19~24개월: 학습한 내용을 커리어 언어로 정리하기

- 그동안의 성능 분석, benchmark, incident note를 다시 읽고 반복해서 등장한 관심사를 찾습니다.
- 가능하면 배운 관점을 현재 업무의 성능, 관측성, 장애 대응 문제에 적용합니다.
- 자신이 깊게 설명할 수 있는 inference/runtime 사례를 선별합니다.
- 시스템 설계, 성능 분석, 장애 대응 사례 중심으로 이력서를 재구성합니다.

점검 기준:

- LLM 요청의 E2E 경로와 주요 병목을 자신의 언어로 설명할 수 있습니다.
- metric, trace, profile로 원인을 좁힌 사례가 있습니다.
- 설정이나 구조 변경의 효과를 수치로 비교한 사례가 있습니다.
- 잘못 세운 가설과 그 가설을 수정한 과정도 설명할 수 있습니다.
- 목표 채용 공고를 읽고 현재 강점과 부족한 역량을 구분할 수 있습니다.

## 주당 학습 예산

기본 예산은 4~5시간입니다.

- 1시간: 이번 주 병목 질문과 관련 개념 학습
- 2시간: 구현 또는 부하 실험
- 1시간: metric, trace, profile 분석
- 30분: 결과와 반례 기록
- 30분: 다음 실험 결정

매주 아래 형식으로 하나의 질문을 끝까지 추적합니다.

1. 예상한 결과
2. 실험 조건과 workload
3. 실제 결과
4. 원인에 대한 가설
5. 변경 사항과 전후 비교
6. 운영 환경에서의 의미
7. 다음 질문

## 당장 하지 않아도 되는 것

- 새로운 model architecture를 제안하는 ML research
- 수학 증명 중심의 deep learning 학습
- CUDA kernel 최적화
- 대규모 distributed training
- feature store와 범용 data platform
- 모든 serving framework 비교
- NPU와 여러 accelerator 동시 학습
- 기능 경쟁 중심의 coding agent 만들기

필요한 경우 실험에서 관찰한 병목을 따라 더 낮은 계층으로 내려갑니다. 학습 순서는 기술 목록이 아니라 관찰된 병목이 결정합니다.
