# Roadmap

## 목표

분산 시스템과 성능 엔지니어링을 기반으로 AI workload를 안정적으로 실행하고 운영하는 AI Platform Engineer가 됩니다.

여기서 AI는 LLM에만 국한하지 않습니다. LLM은 중요한 진입점이지만, 이 로드맵의 중심은 model serving, inference platform, training platform, GPU/NPU cluster, data pipeline, observability, reliability, developer experience를 포괄하는 AI platform입니다.

## 관심사의 흐름

```text
Backend
  -> Platform Engineering
  -> Distributed Systems
  -> AI Workload 이해
  -> AI Platform Engineering
  -> AI Infrastructure / Systems Architect
```

## 핵심 질문

- AI workload는 일반 backend workload와 무엇이 다른가?
- GPU/NPU 같은 accelerator는 어떤 방식으로 할당되고 스케줄링되는가?
- Model serving에서 latency, throughput, cost는 왜 자주 충돌하는가?
- Training, inference, batch processing, online serving은 운영 관점에서 어떻게 다른가?
- AI platform에서 data pipeline, feature store, vector search, artifact registry는 어떤 역할을 하는가?
- Observability는 request, model, GPU, data, cost를 어떻게 함께 보여줘야 하는가?
- AI 개발자가 모델을 더 쉽게 배포하고 실험하려면 platform은 어떤 추상화를 제공해야 하는가?
- 장애가 나도 AI 서비스가 계속 동작하게 하려면 어떤 degradation, rollback, fallback 전략이 필요한가?

## 지식 축

### 1. Systems Fundamentals

- Linux, process, thread, memory, file system, network
- Computer architecture, memory hierarchy, cache, NUMA
- Distributed systems, consensus, replication, queue, backpressure
- Kubernetes, scheduler, controller, CRI/CNI/CSI
- Observability, metrics, tracing, logging, profiling

### 2. AI Workloads

- Inference serving
- Training pipeline
- Batch inference
- Online prediction
- Embedding generation
- Vector search / RAG
- Recommendation / ranking workload
- Multimodal workload

### 3. AI Compute Platform

- GPU/NPU basics
- GPU memory, HBM, PCIe, NVLink
- Accelerator scheduling
- Cluster resource management
- Autoscaling
- Quota, priority, preemption
- Utilization and cost optimization

### 4. Model Serving Platform

- Model packaging and registry
- Deployment strategy
- Canary, rollback, shadow traffic
- Batching and queueing
- Latency and throughput tradeoff
- Model versioning
- Fallback and degradation

### 5. Data and Experiment Platform

- Data pipeline
- Feature pipeline
- Dataset/version management
- Experiment tracking
- Evaluation pipeline
- Offline/online metric gap

### 6. Developer Experience

- Self-service deployment
- Internal platform API
- CLI and dashboard
- Templates and golden paths
- Safe defaults
- Documentation and examples

## 6개월 목표

- AI platform의 큰 구성 요소를 말로 설명할 수 있게 됩니다.
- 매주 1개 이상 질문을 남기고, 한 달에 1개 정도만 제대로 정리합니다.
- LLM, recommender, vision, embedding 같은 AI workload를 "서비스 운영 관점"에서 비교합니다.
- vLLM, KServe, Ray, Triton Inference Server, Kubeflow 중 하나를 가볍게 실행하거나 구조를 읽어봅니다.
- 업무에서 얻은 E2E, observability, reliability 경험을 AI platform 관점의 메모로 연결합니다.

## 주당 학습 예산

기본 예산은 4~5시간입니다.

- 평일: 하루 10분 메모
- 주말: 1~2시간 읽기 또는 실험
- 바쁜 주: 질문 1개만 남겨도 성공
- 여유 있는 주: 개념 노트 1개 정리

## 2년 목표

- AI platform 관련 실무/프로젝트 경험을 만듭니다.
- Model serving, data pipeline, GPU scheduling, observability 중 하나 이상을 깊게 다룹니다.
- Latency, throughput, utilization, memory, cost, reliability 지표를 함께 보고 설명할 수 있습니다.
- 관련 오픈소스 코드를 읽고 작은 기여를 시도합니다.
- "AI workload를 안정적으로 운영하는 플랫폼 엔지니어"라는 방향으로 이력서를 재구성합니다.

## 당장 하지 않아도 되는 것

- 새로운 모델 구조를 제안하는 ML research
- 수학 중심의 딥러닝 이론 파고들기
- CUDA kernel 최적화부터 깊게 들어가기
- 모든 AI framework를 한 번에 익히기

필요하면 나중에 내려가도 됩니다. 지금의 우선순위는 AI를 둘러싼 compute, data, serving, operations를 하나의 platform으로 이해하는 것입니다.
