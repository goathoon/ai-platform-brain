# 03 AI Systems

LLM을 실제 서비스로 운영하기 위한 inference, serving, GPU, platform 주제를 정리합니다.

## 우선 정리할 개념

- vLLM
- PagedAttention
- Continuous Batching
- Triton Inference Server
- Ray Serve
- GPU Scheduling
- GPU Memory
- HBM
- NVLink
- Observability for Inference

## 질문

- Throughput과 latency는 왜 자주 충돌하는가?
- GPU utilization이 낮을 때 어디부터 봐야 하는가?
- Prefill과 decode는 어떤 병목 특성이 다른가?
- Model serving에서 autoscaling은 일반 web server와 어떻게 다른가?
