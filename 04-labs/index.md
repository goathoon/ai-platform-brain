# 04 Labs

공부 중 직접 확인해보고 싶은 질문, 짧은 실험, benchmark, 장애 분석을 모읍니다.

## 기본 방향

- 포트폴리오용 제품 완성을 목표로 하지 않습니다.
- 질문 하나를 확인하는 작은 실험도 충분합니다.
- 이전 코드나 환경이 유용하면 재사용하고, 그렇지 않으면 독립적으로 실험합니다.
- 기능 수보다 무엇을 예상했고 실제로 무엇을 관찰했는지를 기록합니다.
- 공부에 필요하지 않은 platform 기능은 억지로 구현하지 않습니다.

## AI Runtime Lab

반복 실험에 도움이 될 때만 유지하는 가벼운 공용 환경입니다.

- 간단한 LLM gateway 또는 proxy
- Ollama 또는 vLLM
- 부하 생성기
- metrics, logs, traces
- failure injection
- 실험 결과를 비교할 수 있는 기록 방식

처음부터 모두 구성하지 않습니다. 현재 질문을 확인하는 데 필요한 요소만 추가합니다.

## 실험 기록 기준

- 확인하고 싶은 질문과 예상
- workload와 실험 조건
- 실제로 관찰한 latency, throughput, memory, reliability, cost
- metric, trace, profile을 이용한 병목 분석
- 실패한 가설과 반례
- 결과를 운영 환경에 적용할 때의 한계
- 다음에 이어서 확인할 질문

모든 항목을 매번 채울 필요는 없습니다. 실험 규모에 맞게 기록합니다.

## 학습 실험 후보

- queue와 retry amplification 실험
- context length와 KV cache memory 실험
- concurrency와 TTFT/tail latency 실험
- continuous batching과 throughput 실험
- quantization의 memory/performance/quality 비교
- model cold start와 loading time 실험

후보를 순서대로 완료할 필요는 없습니다. 공부 중 가장 궁금해진 질문을 선택합니다.
