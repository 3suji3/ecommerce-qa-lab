# ecommerce-qa-lab

가상의 이커머스 주문·결제 시스템으로 QA, API 테스트, SQL 데이터 검증과 테스트 자동화를 실습하는 미니 프로젝트.

## 프로젝트 목적

QA 역량 강화와 QA 포트폴리오 작성을 목표로 한다. 서비스 구현은 테스트에 필요한 최소 범위로 유지하며, production-grade 쇼핑몰 구축은 범위에 포함하지 않는다.

## 현재 상태

**Day 1 - Initial setup**

초기 요구사항과 QA 전략을 문서화한 단계다. 애플리케이션 구현, 패키지 설치, DB 생성 및 테스트 실행은 아직 진행하지 않았다.

## 예정 기술 스택

| 영역 | 기술 |
| --- | --- |
| Frontend | React + Vite |
| Backend | Node.js + Express |
| Database | SQLite |
| Automation | Playwright |
| API Test | Postman |
| Data Analysis | Python + Pandas |

## QA 학습 목표

- 요구사항 분석과 테스트 설계
- API 검증
- SQL 기반 데이터 검증
- 주문 상태 전이 테스트
- 데이터 품질 분석
- Playwright 기반 회귀 테스트 자동화

## 문서

- [Requirements](docs/requirements.md): 확정 요구사항과 미확정 정책
- [Architecture](docs/architecture.md): 예정 구조와 주문 상태 전이
- [QA Strategy](docs/qa-strategy.md): 검증 계층, 테스트 기법, 자동화 후보
- [Decisions](docs/decisions.md): 날짜별 주요 의사결정
- [Agent Rules](AGENTS.md): AI 에이전트 작업 규칙
