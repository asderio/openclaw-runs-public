# NotebookLM MCP CLI 개선 요약

원인 확인 결과, 현재 NotebookLM MCP 등록 커맨드가 `npx -y notebooklm-mcp@latest`라서 네트워크 제한 환경에서 npm registry 조회 단계에서 바로 실패하고 있었습니다. 추가로 캐시된 패키지 안에는 `require is not defined`를 일으키는 ESM 설정 로더 버그도 확인했습니다.

이 요청 폴더 안에 오프라인 실행용 래퍼와 복구 문서를 만들었고, `./outputs/notebooklm-mcp-offline.sh config get`로 실제 실행 검증까지 마쳤습니다. 다만 실제 Codex MCP 전역 설정 파일은 이 요청 범위 밖이라 직접 변경하지 않았고, NotebookLM 인증도 현재 `authenticated: false` 상태라 별도 auth setup이 필요합니다.

## Artifact Inventory

- `outputs/notebooklm-mcp-offline.sh`: `npx` 없이 `~/.npm/_npx` 캐시 바이너리를 직접 실행하는 오프라인 래퍼
- `outputs/notebooklm-mcp-diagnosis.md`: 원인 분석과 복구 순서 정리
- `outputs/notebooklm-mcp-settings-manager.patch`: ESM `require(...)` 버그 수정 패치
- `outputs/public/notebooklm-mcp-recovery.md`: 공유 가능한 짧은 복구 가이드
