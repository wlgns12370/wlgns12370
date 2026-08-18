## 유지훈 · Backend Developer

제약이 있는 환경에서 **운영 비용이 낮은 구조**를 설계하는 데 관심이 많습니다.  
학과 시스템도서위원회에서 4년간 학부생 1,400명이 쓰는 내부 서비스를 개발·운영하며,  
좋은 기술을 먼저 고르기보다 **주어진 제약에 맞는 실용적인 아키텍처를 설계**했습니다.

기술 선택은 가능한 한 **공개된 기록으로 남깁니다.** 아래 프로젝트의 대안 비교와 의사결정 과정은  
GitHub Discussions와 PR 리뷰에 그대로 남아 있습니다.

📬 wlgns12370@gmail.com

---

## Skills

**Backend** &nbsp; `Java` `Spring Boot` `Spring Data JPA`  
**Database** &nbsp; `MySQL` `Redis`  
**DevOps** &nbsp;&nbsp; `Docker` `Kubernetes(K3s)`  
**Infra** &nbsp; `AWS EC2 · RDS · S3`

---

## Projects

### [환전소 예약 서비스](https://github.com/vietnam-internship/server) &nbsp;`FPT Information System 인턴`
> 베트남 다낭 FPT IS 과제 · 2026.07 – 2026.08 | Java 21, Spring Boot, MySQL, K3s, Stripe

- 30분 단위 타임 슬롯의 **선점 기준을 "슬롯 선택 시점"으로 확정**하고 신청·결제 API를 분리해, 결제 실패·재시도 중에도 예약 기회가 유실되지 않는 흐름 구현
- 신청과 Stripe 결제가 하나의 트랜잭션으로 묶이지 않는 구조에서, **만료 스케줄러와 사용자 취소가 동일 예약을 동시에 처리해 재고가 이중 복원되는 경쟁 상태**를 발견하고 낙관적 락으로 제어
- 충돌 빈도가 낮은 워크로드로 판단해 비관적 락 대신 낙관적 락을 선택 — **락 대기로 인한 처리량 저하를 피하는 것이 목적**
- 동시성 제어에만 의존하지 않도록 **재고 정합성 검사와 Discord 알림·복구 스크립트**를 별도 운영 장치로 구성

🔗 **의사결정 기록**  
&nbsp;&nbsp;· [결제 API 통합 vs 분리 — 고스트 좌석과 선점 유실의 트레이드오프](https://github.com/vietnam-internship/server/discussions/15)  
&nbsp;&nbsp;· [좌석 선점 동시성 전략 — Row Lock vs SKIP LOCKED](https://github.com/vietnam-internship/server/discussions/13)  
&nbsp;&nbsp;· [비관적 락 vs SKIP LOCKED — 멘토 리뷰](https://github.com/vietnam-internship/server/discussions/14)  
&nbsp;&nbsp;· [보상 처리 충돌 — 낙관적 락 도입](https://github.com/vietnam-internship/server/discussions/41)  
&nbsp;&nbsp;· [PR #10 — K8s 배포 및 환경별 매니페스트 구성](https://github.com/vietnam-internship/server/pull/10)

<br>

### [선착순 야식 배부 서비스](https://github.com/Committee-of-System-Library) <!-- TODO: 레포 URL 확인 -->
> 오프라인 배부 대기열의 온라인 전환 · 대상 814명 · 2026.04 – | Java 21, Spring Boot, MySQL, Docker, k6

- 매 회 30~60분씩 줄을 서던 현장 배부를 모바일 선착순 신청으로 전환, **정원 100~150명에 약 400명이 경쟁하는 스파이크에서 초과 발급 0건**
- Redis·슬롯 테이블·WAS 메모리 세 방식을 비교한 뒤 **MySQL 원자적 UPDATE 채택** — 조회와 갱신 사이의 Race Condition을 단일 문장으로 제거하고, 재고의 단일 진실 공급원을 유지
- 추정치(400명)를 설계 근거로만 두지 않고 **k6 부하 테스트로 검증** (약 400 RPS, p95 474ms)
- 신청 자격 검증에서 **외부 재정 서비스 의존성을 제거** — 납부자 명단을 로컬 스냅샷으로 관리해, 신청이 집중되는 시간대에 외부 지연·장애가 신청 실패로 전파되지 않도록 격리
- 전체 정원의 10%를 배부 인력 전용 물량으로 **자원 자체를 분리**해, 일반 신청자가 예약분을 침범하는 코드 경로를 제거하고 **물량 부족에 따른 추가 구매 0회**

🔗 **의사결정 기록**  
&nbsp;&nbsp;· [동시성 전략 비교 Discussion ](https://github.com/Committee-of-System-Library/comit-backend/discussions/96) 
&nbsp;&nbsp;· [야식마차 신청 PR1](https://github.com/Committee-of-System-Library/comit-backend/pull/166)  

<br>

## Education & Certifications

- **경북대학교** 컴퓨터학부 · 전공 `2021.03 – 2027.02 (졸업 예정)`
- **정보처리산업기사** `2022.08` &nbsp;·&nbsp; **SQLD** `2022.12`

---

## Awards

| 수상 | 주최 | 연도 |
|---|---|---|
| 하계 종합 학술대회 **동상** | 한국정보기술학회장 | 2026.06 |
| 창업 성과 경진대회 **대상** | 경북대학교 소프트웨어교육원 | 2025.12 |
| KNU 창업 경진대회 **최우수상** | 경북대학교 LINC 사업단 | 2022.08 |
| 창업 성과 경진대회 최우수상 | 경북대학교 소프트웨어교육원 | 2022.06 |
| 대구 북구 청년창업 경진대회 수상 | 대구광역시 북구청장 | 2022.03 |

---
