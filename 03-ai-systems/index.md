# 03 AI Systems

LLM을 실제 서비스로 운영하기 위한 inference, serving, GPU, platform 주제를 정리합니다.

## 우선 정리할 개념

- GPU Execution Model
- Warp / SIMT
- GPU Memory Hierarchy
- Memory Bandwidth / Data Movement
- Compute-bound vs Memory-bound
- Matrix Multiplication
- Prefill / Decode
- KV Cache
- vLLM
- PagedAttention
- Continuous Batching
- Triton Inference Server
- Ray Serve
- GPU Scheduling
- NVLink
- Observability for Inference

## 질문

- LLM inference의 어떤 단계가 GPU에서 compute-bound이고 어떤 단계가 memory-bound일까?
- GPU의 execution model과 memory hierarchy는 prefill/decode 성능에 어떻게 연결될까?
- Throughput과 latency는 왜 자주 충돌하는가?
- GPU utilization이 낮을 때 어디부터 봐야 하는가?
- Prefill과 decode는 어떤 병목 특성이 다른가?
- Model serving에서 autoscaling은 일반 web server와 어떻게 다른가?
