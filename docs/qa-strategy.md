# QA Strategy

현재 문서는 QA 전략 초안이다. 상세 테스트케이스 작성과 테스트 실행은 아직 진행하지 않았다.

## QA 목표

- 요구사항 분석
- 테스트 설계
- API 검증
- SQL 데이터 검증
- 상태 전이 테스트
- 데이터 품질 분석
- Playwright 기반 회귀 테스트 자동화

## Test Levels

| 계층 | 검증 방향 | 예정 도구 |
| --- | --- | --- |
| UI | 수량 입력, 오류 안내, 주문 상태 표시 | 수동 확인, Playwright |
| API | 요청·응답과 주문·결제·취소 규칙 | Postman |
| DB | 주문 금액, 상태, 재고 및 결제 데이터 정합성 | SQLite, SQL |
| E2E | 사용자 동작부터 데이터 반영까지 주요 흐름 | Playwright |
| Data Quality | 데이터 누락, 중복 및 불일치 분석 | SQL, Python + Pandas |

## Test Techniques

향후 다음 기법을 사용할 예정이다.

- **Equivalence Partitioning**: 유효·무효 입력을 그룹으로 나누어 검증한다.
- **Boundary Value Analysis**: 수량 제한, 재고, 할인 상한의 경계를 검증한다.
- **State Transition Testing**: 주문 상태 전이와 허용되지 않는 동작을 검증한다.
- **Exploratory Testing**: 탐색 과정에서 예상하지 못한 흐름과 오류를 확인한다.

## 예정 자동화 후보

- 정상 주문 및 결제
- 쿠폰 적용 주문
- 재고 부족 주문
- 결제 실패
- 주문 취소
- 중복 결제 방지
- 최소/최대 주문 수량 검증

## 적용 원칙

확정된 [요구사항](requirements.md)을 검증 기준으로 사용한다. Open Question에 의존하는 기대 결과는 정책 결정 후 정의한다. 구현과 API 계약이 마련되면 상세 테스트케이스와 자동화 범위를 구체화한다.
