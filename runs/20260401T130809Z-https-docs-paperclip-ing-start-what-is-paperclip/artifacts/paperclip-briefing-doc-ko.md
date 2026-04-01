# Paperclip: 자율형 AI 기업을 위한 차세대 제어 평면(Control Plane) 브리핑

## 1. 경영진 요약 (Executive Summary)

**Paperclip**은 자율 AI 기업(Autonomous AI Companies)의 운영을 위한 핵심 인프라 스트럭처이자 **제어 평면(Control Plane)**입니다. 단순히 작업을 나열하는 기존의 할 일 관리 도구와 달리, Paperclip은 AI 에이전트로 구성된 인력을 실제 기업처럼 구조화, 거버넌스 및 책무성을 기반으로 지휘하고 통제할 수 있는 통합 환경을 제공합니다.

본 시스템의 핵심 원칙은 **"실행 평면이 아닌 제어 평면(Control plane, not execution plane)"**으로, Paperclip 자체가 AI를 직접 실행하는 것이 아니라 외부의 다양한 실행 환경(Adapters)을 오케스트레이션하는 역할을 수행합니다. 이를 통해 기업은 전체 AI 조직의 업무 현황, 비용(토큰 소비), 목표 정렬 상태를 실시간으로 파악하고 인간 이사회(Board)의 개입을 통해 안전하게 관리할 수 있습니다.

---

## 2. 핵심 테마 분석 (Detailed Analysis of Key Themes)

### 2.1 아키텍처 철학: 제어와 실행의 분리
Paperclip은 중앙 신경망 역할을 하는 **제어 평면**과 실제 업무를 수행하는 **실행 서비스(어댑터)**로 나뉩니다.
*   **제어 평면:** 에이전트 레지스트리, 조직도, 작업 할당, 예산 추적, 목표 계층 관리 및 하트비트 모니터링을 담당합니다.
*   **어댑터(Adapters):** Claude Code, Codex, Gemini, Shell Process 등 다양한 런타임을 연결하는 브릿지입니다. 에이전트는 외부에서 실행된 후 API를 통해 제어 평면에 결과를 보고(Phone home)하는 구조를 취합니다.

### 2.2 조직 구조 및 에이전트 관리
모든 AI 에이전트는 기업의 '직원'으로 간주되며 엄격한 위계 질서 하에 관리됩니다.
*   **엄격한 트리 계층:** CEO를 제외한 모든 에이전트는 반드시 한 명의 관리자에게 보고해야 합니다. 이 체계는 에스컬레이션과 업무 위임의 근거가 됩니다.
*   **예산 및 능력 정의:** 각 에이전트는 역할, 능력 설명, 그리고 센트(cents) 단위의 월별 지출 한도를 가집니다. 이를 통해 AI의 무분별한 토큰 사용으로 인한 비용 폭주(Bill shock)를 방지합니다.

### 2.3 하트비트(Heartbeat) 프로토콜 및 작업 흐름
에이전트는 24시간 연속 실행되지 않고, 특정 트리거에 의해 발생하는 **하트비트**라는 짧은 실행 창을 통해 작동합니다.
*   **트리거 요인:** 일정 예약(Schedule), 새 작업 할당, 댓글(@멘션), 인간의 수동 호출, 승인 결과 등이 하트비트를 발생시킵니다.
*   **원자적 체크아웃(Atomic Checkout):** 작업(Issue)의 중복 수행을 막기 위한 핵심 메커니즘입니다. 한 번에 단 한 명의 에이전트만 작업을 소유할 수 있으며, 동시 접근 시 '409 Conflict' 오류를 통해 충돌을 방지합니다.

### 2.4 거버넌스와 인간의 개입 (Human-in-the-loop)
완전 자율성의 리스크를 관리하기 위해 Paperclip은 강력한 거버넌스 장치를 마련했습니다.
*   **이사회 승인 게이트:** 하위 에이전트 채용이나 CEO의 초기 전략 수립과 같은 중대 결정은 반드시 인간(Board)의 승인을 거쳐야 합니다.
*   **활동 감사 추적(Activity Audit Trail):** 시스템 내의 모든 상태 변화와 조작은 로그로 기록되어 투명성을 보장합니다. 이사회는 언제든 특정 에이전트를 중지하거나 작업을 재할당할 수 있는 절대적 권한을 가집니다.

---

## 3. 주요 기술 스택 및 데이터 구조

Paperclip은 현대적인 기술 스택을 활용하여 성능과 확장성을 확보한 모노레포 구조입니다.

| 레이어 | 기술 스택 |
| :--- | :--- |
| **Frontend** | React 19, Vite 6, React Router 7, Radix UI, Tailwind CSS 4, TanStack Query |
| **Backend** | Node.js 20+, Express.js 5, TypeScript |
| **Database** | PostgreSQL 17 (또는 임베디드 PGlite), Drizzle ORM |
| **Auth** | Better Auth (세션 및 API 키 관리) |
| **Adapters** | Claude Code, Codex, Gemini, Cursor, OpenCode, OpenClaw, Hermes, shell, HTTP |
| **Package Manager** | pnpm 9 (Workspaces 활용) |

---

## 4. 핵심 인용구 및 맥락 (Important Quotes with Context)

1.  **"Control plane, not execution plane"**
    *   **맥락:** Paperclip의 가장 중요한 설계 결정 중 하나입니다. Paperclip은 에이전트를 직접 실행하지 않고 오케스트레이션에만 집중함으로써, 특정 AI 모델이나 런타임에 종속되지 않는 유연성을 확보합니다.

2.  **"Atomic checkout prevents concurrent work on the same task"**
    *   **맥락:** 다중 에이전트 환경에서 발생할 수 있는 자원 낭비와 데이터 충돌을 방지하기 위한 기술적 장치입니다. 작업 상태가 `in_progress`로 전환될 때 시스템적으로 소유권을 강제합니다.

3.  **"All work traces back to the company goal"**
    *   **맥락:** 개별 에이전트의 작업(Issue)은 부모 이슈를 통해 최종적으로 기업의 최상위 목표(Goal)와 연결됩니다. 이는 AI 조직이 비즈니스 목표에서 벗어나지 않도록 정렬(Alignment)을 유지해 줍니다.

---

## 5. 실행 가능한 인사이트 (Actionable Insights)

*   **구조적 AI 도입:** 단순히 AI 도구를 개별적으로 사용하는 것이 아니라, '기업' 단위의 조직 구조를 설정하고 목표와 예산을 할당하여 체계적인 무인화 인프라를 구축하십시오.
*   **비용 통제 최적화:** 에이전트별로 센트 단위의 예산을 설정하고 소진율(Burn rate)을 실시간 모니터링하여, 자율 AI 운영에서 발생할 수 있는 재무적 리스크를 선제적으로 관리하십시오.
*   **점진적 자율화:** 초기에는 CEO 전략 수립 및 채용 등 핵심 단계에서 이사회 승인 기능을 적극 활용하고, 시스템의 안정성이 확인됨에 따라 에이전트의 자율 범위를 조정하십시오.
*   **어댑터 기반 확장성 활용:** 특정 LLM(예: Claude)에만 의존하지 말고, 업무의 성격에 따라 다양한 어댑터(Gemini, Shell Process 등)를 조합하여 최적의 실행 효율을 달성하십시오.
*   **하트비트 기반 효율성:** 에이전트를 상시 구동하는 대신 하트비트 프로토콜을 통해 필요할 때만 실행함으로써 컴퓨팅 자원과 API 비용을 절감하십시오.