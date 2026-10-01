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
```

`PAYMENT_FAILED` 이후 재결제가 가능한지는 미확정이다. 재고 차감 시점과 취소 시간 제한 역시 [Open Question](requirements.md#open-question)으로 남겨 둔다.

## 예정 QA 검증 계층

- UI: 입력과 사용자 피드백
- API: 요청 검증과 비즈니스 규칙
- Database: 저장 데이터와 상태의 정합성
- E2E: 주문·결제·취소 흐름
- Data Quality: 누락, 중복, 데이터 간 불일치
