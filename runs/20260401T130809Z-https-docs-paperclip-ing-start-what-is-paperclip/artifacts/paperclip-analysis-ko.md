# Paperclip 심층 분석 요약

## 한 줄 정의

Paperclip은 자율 AI 조직을 위한 제어 평면이다. 에이전트를 직접 실행하는 대신, 조직 구조와 작업 흐름, 예산, 승인, 감사 체계를 중앙에서 관리한다.

## 핵심 포인트

1. Paperclip은 일반 작업 관리 도구보다 상위 계층의 제품이다.
2. Company, Agents, Issues, Heartbeats, Governance라는 운영 모델을 중심으로 설계된다.
3. 실행은 외부 런타임과 어댑터에 맡기고, Paperclip은 오케스트레이션만 수행한다.
4. 비용 폭주와 중복 작업을 막기 위해 예산 한도와 원자적 체크아웃을 사용한다.
5. 완전 자율보다 인간 승인과 감사 추적을 포함한 통제된 자율성에 가깝다.

## 왜 중요한가

다중 AI 에이전트를 실제 조직처럼 운영하려면 "누가 무엇을 하고 있는지", "얼마를 쓰고 있는지", "누가 승인했는지"를 한 번에 봐야 한다. Paperclip은 이 운영 문제를 제품의 중심에 놓는다. 따라서 이 제품은 에이전트 실행 도구가 아니라 AI 조직 운영 시스템으로 이해하는 편이 정확하다.

## 한계와 리스크

- 외부 LLM/API 런타임 안정성에 의존한다.
- 조직 구조가 엄격한 트리 기반이어서 유연성이 떨어질 수 있다.
- 인간 승인 게이트는 안전장치이지만 확장 시 병목이 될 수 있다.
- 공개 시작 문서만으로는 운영 규모나 실전 도입 사례를 검증하기 어렵다.

## 사용한 문서

- https://docs.paperclip.ing/start/what-is-paperclip
- https://docs.paperclip.ing/start/quickstart
- https://docs.paperclip.ing/start/core-concepts
- https://docs.paperclip.ing/start/architecture
