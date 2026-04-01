# Paperclip 자료조사 요약

`https://docs.paperclip.ing/start/what-is-paperclip`를 중심으로 `quickstart`, `core-concepts`, `architecture`까지 함께 NotebookLM에 넣어 한글 심층 조사를 수행했다. 결론적으로 Paperclip은 개별 에이전트 실행기가 아니라, 자율 AI 조직의 구조, 작업, 예산, 거버넌스를 통제하는 제어 평면으로 해석하는 것이 가장 정확하다.

NotebookLM 산출물은 가능한 범위까지 모두 생성했고, 공개용 패키지는 `outputs/public/`에 정리했다. `audio`, `report`, `slides`, `infographic`, `quiz`, `flashcards`, `data table`, `mind map`은 확보했다. 다만 `video overview`는 NotebookLM 렌더가 장시간 `in_progress`에 머물러 이번 실행 안에서는 MP4 파일을 회수하지 못했다. 대신 한국어 `paperclip-deliverable-brief-ko.md`에 영상 개요와 나머지 제작 브리프를 넣었다.

추가 메모:

- NotebookLM raw 산출물 중 `quiz`, `flashcards`, `mind map`은 영어로 생성되어, 공개용 패키지에는 한국어 로컬라이즈드 버전을 별도로 만들었다.
- 프로젝트 규칙상 이 요청 디렉터리 밖 수정이 금지되어 있어 Obsidian 게시 단계는 수행하지 않았다.
- 스킬 확인 결과, 앞으로 "자료조사해줘" 같은 요청은 기본적으로 `notebooklm-research-pipeline`으로 처리하는 흐름이 맞고, 이번처럼 NotebookLM 질의를 여러 번 돌리고 산출물을 넓게 회수하는 경우에는 `notebooklm-research-publisher`까지 같이 쓰는 구성이 적절하다.

아티팩트 인벤토리:

- 공개용 패키지: `outputs/public/paperclip-analysis-ko.md`
- 공개용 패키지: `outputs/public/paperclip-briefing-doc-ko.md`
- 공개용 패키지: `outputs/public/paperclip-comparison-table-ko.csv`
- 공개용 패키지: `outputs/public/paperclip-deliverable-brief-ko.md`
- 공개용 패키지: `outputs/public/paperclip-infographic-ko.png`
- 공개용 패키지: `outputs/public/paperclip-slides-ko.pdf`
- 공개용 패키지: `outputs/public/paperclip-slides-ko.pptx`
- 공개용 패키지: `outputs/public/paperclip-audio-overview-ko.m4a`
- 공개용 패키지: `outputs/public/paperclip-quiz-ko.md`
- 공개용 패키지: `outputs/public/paperclip-flashcards-ko.md`
- 공개용 패키지: `outputs/public/paperclip-mindmap-ko.json`
- 원문 보관: `outputs/public/paperclip-what-is-paperclip-source.html`
- 작업 번들: `outputs/2026-W14/20260401-221103-paperclip-what-is-paperclip-ko/`
