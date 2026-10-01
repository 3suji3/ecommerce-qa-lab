# Architecture

구현 전 단계의 최소 구조 초안이다. 기술 스택과 엔티티는 예정 사항이며, 상세 API 계약과 DB 스키마는 아직 정의하지 않았다.

## 예상 구조

```text
React (Vite)
  ↓ REST API
Express (Node.js)
  ↓
SQLite
```

## 주요 도메인 엔티티 후보

| 엔티티 | 역할 |
| --- | --- |
| products | 상품 이름, 가격, 재고 |
| orders | 주문 금액과 상태 |
| order_items | 주문에 포함된 상품과 수량 |
| payments | 결제 시뮬레이션 결과 |
| coupons | 쿠폰과 할인 정책 |

실제 PG는 연동하지 않으며, 테스트 가능한 결제 성공/실패 시뮬레이션을 구현할 예정이다.

## 주문 상태 후보 및 전이

상태 값은 `PENDING`, `PAID`, `PAYMENT_FAILED`, `CANCELLED`다. 현재 확정된 전이는 다음과 같다.

```text
PENDING
├─ payment success → PAID
│                    └─ cancel → CANCELLED
└─ payment failure → PAYMENT_FAILED

PAYMENT_FAILED
├─ retry success → PAID
└─ retry failure → PAYMENT_FAILED
```

`PAYMENT_FAILED` 이후 동일 주문의 재결제를 허용한다. 동일 주문의 성공 결제는 한 번만 가능하다.

재고는 주문 생성 시점에 차감하고 미결제 중 유지한다. 주문 실패 시 즉시 복구하며 재결제에도 같은 처리 원칙을 적용한다. 주문 취소 시에는 구매 수량만큼 복구한다.

취소 가능 시간은 1시간이며, 쿠폰 사용은 결제 진행 중 확정한다. 취소 시간의 기준점과 경계, 주문 실패의 의미와 재결제 시 재고 재차감 흐름, 쿠폰의 정확한 사용 확정 시점과 이력 처리는 [Open Question](requirements.md#open-question)으로 남겨 둔다. 세부 사항 확인 전에는 추가 상태나 전이를 정의하지 않는다.

## 예정 QA 검증 계층

- UI: 입력과 사용자 피드백
- API: 요청 검증과 비즈니스 규칙
- Database: 저장 데이터와 상태의 정합성
- E2E: 주문·결제·취소 흐름
- Data Quality: 누락, 중복, 데이터 간 불일치
