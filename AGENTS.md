# Project Rules

## Project Purpose

`ecommerce-qa-lab`은 가상의 이커머스 주문·결제 시스템을 대상으로 QA 역량을 강화하고 증명하는 미니 프로젝트다. production-grade 쇼핑몰 개발이나 개발 포트폴리오 제작이 목적이 아니다.

실습 목표는 QA, API 테스트, SQL 데이터 검증, 데이터 분석, 테스트 자동화다. 기능과 아키텍처는 이 목표에 필요한 최소 범위로 유지한다.

## 예정 기술 스택

| 영역 | 기술 |
| --- | --- |
| Frontend | React + Vite |
| Backend | Node.js + Express |
| Database | SQLite |
| Automation | Playwright |
| API Test | Postman |
| Data Analysis | Python + Pandas |

현재는 문서 초기 세팅 단계다. 실제 프로젝트 코드가 아직 없다면 기술 스택만 문서화하고, 패키지 설치나 코드 생성은 하지 않는다. 구현은 후속 개발 요청에 따라 진행한다.

## Development Rules

- `docs/requirements.md`에 없는 기능을 임의로 추가하지 않는다.
- 요구사항이 모호하면 정책을 임의로 결정하지 않고 Open Question으로 기록한다.
- 중요한 정책 변경은 구현 전에 문서에 먼저 반영한다.
- 과도한 추상화, 불필요한 라이브러리, 지나친 리팩터링을 피한다.
- 테스트 가능한 구조를 우선한다.
- 비즈니스 로직은 읽기 쉽고 추적 가능하게 작성한다.
- DB 상태를 QA가 쉽게 확인할 수 있어야 한다.
- 오류를 조용히 무시하지 않는다.
- 기존 API 계약을 임의로 변경하지 않는다.
- UI는 포트폴리오 캡처가 가능한 수준으로 깔끔하게 만들되 디자인에 과도한 시간을 사용하지 않는다.
- Playwright에서는 role, label, text 등 안정적인 selector를 우선 사용하고 필요할 때만 `data-testid`를 사용한다.
- 코드 수정 시 관련 없는 영역을 함께 리팩터링하지 않는다.

## AI Agent Workflow

1. `AGENTS.md`를 확인한다.
2. `docs/requirements.md`를 확인한다.
3. 변경 요청이 기존 요구사항과 충돌하는지 확인한다. 모호한 정책은 확인 후 진행한다.
4. 필요한 최소 범위만 수정한다.
5. 비즈니스 정책 변경 시 관련 문서도 함께 수정한다. 중요한 변경은 문서에 먼저 반영한다.
6. 중요한 기술적 판단은 `docs/decisions.md`에 기록한다.
