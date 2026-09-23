## 유지훈 · Server Developer · [GitHub](https://github.com/wlgns12370)

제약이 있는 환경에서 **운영 비용이 낮은 구조**를 설계하는 데 관심이 많습니다.

학과 시스템도서위원회에서 4년간 학부생 1,400명이 쓰는 내부 서비스를 개발·운영하며  
좋은 기술을 먼저 고르기보다 **주어진 제약에 맞는 실용적인 아키텍처를 설계**하였습니다.

기술 선택은 가능한 한 **공개된 기록으로 남깁니다.** 아래 프로젝트의 대안 비교와 의사결정 과정은  
GitHub Discussions와 PR 리뷰에 그대로 남아 있습니다.

📬 wlgns12370@gmail.com

---

## Projects

### OPRO · 소상공인 정책자금 추천 AI 에이전트 [(Repository)](https://github.com/KB-AI-Challenge-Just-it/opro)
> 사용자별 정보 보완과 정책자금 자격 검증을 연결한 프로액티브 AI 서비스 · 팀 JustIT

- 초기 사업자 프로필의 빈 항목을 진단하고, 필요한 질문을 동적으로 생성해 답변을 추천 입력으로 연결
- Spring에서 프로필·답변을 AI 서비스로 전달하고, BM25·벡터 하이브리드 RAG로 공고를 검색
- 지원 요건과 사용자 정보를 대조해 부적합 공고를 추천 목록에서 제외하는 검증 흐름 구현
- **기술:** Java, Spring Boot, Python, FastAPI, Next.js, PostgreSQL, ChromaDB, BM25, Claude API, Docker

[![OPRO 서비스 소개 영상](https://img.youtube.com/vi/S0kno8-PiE0/hqdefault.jpg)](https://youtu.be/S0kno8-PiE0)

### 공군 창의 혁신 해커톤 · 문서 기반 RAG [(Repository)](https://github.com/air-force-hackathon/rag)
> PDF 문서의 구조를 보존하고 검색 근거를 개선한 내부 문서 질의응답 시스템

- PDF 표 파싱으로 이름·연락처의 행 관계가 깨지는 문제를 추적하고 PyMuPDF·Camelot 기반 `CustomPDFReader` 구현
- Kiwi 형태소 분석을 거친 BM25 키워드 검색과 의미 기반 Vector Search를 결합
- BM25 점수를 Min-Max Scaling한 뒤 Vector 0.6·BM25 0.4로 결합해 검색 결과를 LLM 근거로 전달

### 종합설계프로젝트2 · 버티포트 CCTV 통합 관제 [(Repository)](https://github.com/2026-1-2)
> 장비가 저장한 감지 이미지를 웹 관제 화면의 알림으로 연결한 시스템

- NestJS와 `chokidar`로 신규 이미지를 감지하고 파일 쓰기 완료 후 SSE로 관제 화면에 전달 [(PR링크)](https://github.com/2026-1-2/mmp-server/pull/12)
- 서버 재시작 시 기존 파일을 제외해 중복 알림을 방지하고, 백엔드·인프라 연동에 참여
- 공동 논문을 게재하고 한국정보기술학회 대학생 논문경진대회 우수논문상 동상 수상


### 선착순 야식 배부 서비스 [(배포 링크)](https://chcse.knu.ac.kr/snack)
> 오프라인 배부 대기열의 온라인 전환 · 대상 1400명 · 2026.04 – | Java 21, Spring Boot, MySQL, Docker, k6

- 매 회 30\~60분씩 줄을 서던 현장 배부를 모바일 선착순 신청으로 전환, 정원 100\~150명에 약 400명이 경쟁하는 스파이크에서 초과 발급 0건
- `SkipLocked`, `Redis cache`, `WAS cache` 세 방식을 비교한 뒤 **MySQL 원자적 UPDATE 채택**
- 의사결정 근거를 얻기 위해 페르소나 기반 400명 인원에 대한 k6 부하 테스트 및 의사결정 (약 400 RPS, p95 474ms)
- 신청 자격 검증에서 **외부 재정 서비스 의존성을 제거**
  - 납부자 명단을 로컬 스냅샷으로 관리해, 신청이 집중되는 시간대에 외부 지연 및 장애가 신청 실패로 전파되지 않도록 격리
- 전체 정원의 10%를 배부 인력 전용 물량으로 **자원 자체를 분리**해, 일반 신청자가 예약분을 침범하는 코드 경로를 제거하고 **물량 부족에 따른 추가 구매 0회**

🔗 **의사결정 기록**  
&nbsp;&nbsp;· [[디스커션1] 데이터 모델 및 동시성 전략 설계 과정 → MySQL 원자적 UPDATE 합의](https://github.com/Committee-of-System-Library/comit-backend/discussions/96)  
&nbsp;&nbsp;· [[PR1] 관리자 수동 오픈 의존성 제거](https://github.com/Committee-of-System-Library/comit-backend/pull/166)


### 환전소 예약 서비스
> 베트남 다낭 FPT IS 과제 · 2026.07 – 2026.08 | Java 21, Spring Boot, MySQL, K3s, Stripe

- 30분 단위 타임 슬롯의 **선점 기준을 슬롯 선택 시점으로 확정**하고 신청·결제 API를 분리해, 결제 실패·재시도 중에도 예약 기회가 유실되지 않는 흐름 구현
- 신청과 Stripe 결제가 하나의 트랜잭션으로 묶이지 않는 구조에서, **만료 스케줄러와 사용자 취소가 동일 예약을 동시에 처리해 재고가 이중 복원되는 경쟁 상태**를 발견하고 낙관적 락으로 제어
  - 충돌 빈도가 낮은 워크로드로 판단해 비관적 락 대신 낙관적 락을 선택 — **락 대기로 인한 처리량 저하를 피하는 것이 목적**
- 동시성 제어에만 의존하지 않도록 **재고 정합성 검사와 Discord 알림·복구 스크립트**를 별도 운영 장치로 구성

🔗 **의사결정 기록**  
&nbsp;&nbsp;· [[디스커션1]취소·만료 스케줄러가 동일 예약을 처리해 재고가 이중 복원되는 문제 -> 낙관적 락으로 해결](https://github.com/vietnam-internship/server/discussions/41)  
&nbsp;&nbsp;· [[디스커션2]좌석 선점 동시성 전략 —> Row Lock](https://github.com/vietnam-internship/server/discussions/13)  
&nbsp;&nbsp;· [[디스커션3]결제 API 통합 vs 분리 -> 분리 선택](https://github.com/vietnam-internship/server/discussions/15)  
&nbsp;&nbsp;· [[PR1]K3s 배포 및 환경별 매니페스트 구성](https://github.com/vietnam-internship/server/pull/10)

## Experience

### 학생회 시스템 도서위원회 · 서비스 통합 및 운영

- 학부생 약 1,400명이 사용하는 학생회비·사물함·커뮤니티 등 6개 서비스를 운영
- AWS 계정마다 흩어진 데이터와 기술 부채를 해결하기 위해 온프레미스 서버로 이관
- `6 WAS + 1 DB` 구조를 선택해 서비스별 배포 단위는 유지하고 회원 데이터의 기준을 통합
- 7명이 함께 개발할 수 있도록 Multi-Repo와 Flyway 기반 DB 변경 관리 체계를 정비하고 약 2개월 만에 이관

### FPT IS 인턴십 · TravelX 예약·결제 백엔드 [(Repository)](https://github.com/vietnam-internship/server)

- 베트남 다낭 FPT IS에서 좌석 선점·Stripe 결제·예약 취소가 연결된 여행 예약 서비스를 개발
- 결제 API를 예약 API와 분리하고, 만료·취소가 동시에 실행될 때 좌석이 이중 복원되는 문제를 낙관적 락으로 제어
- K3s 배포 매니페스트를 환경별로 구성하고, 기술 선택 근거를 GitHub Discussion으로 공유해 멘토 검토를 받음

### 공군 정보체계관리병 · 분산 서버 관제 및 배포·롤백

- A·B 지역으로 분산된 서버의 CPU·메모리와 로그를 교대근무로 점검하고 한화시스템 빌드의 배포·롤백을 담당
- B 지역 서버 전체를 동시에 재부팅하던 절차에서 일부 서버를 운영하며 나머지를 업데이트하는 롤링 업데이트·Blue-Green 방식을 제안
- 개발 이후에도 관측·복구 절차가 서비스 안정성의 일부라는 점을 경험

### 링어스 · 비전공자와 함께 만든 멘토·멘티 매칭 서비스

- 기획자·디자이너가 포함된 11명 팀에서 백엔드 리더로 API 설계와 개발 프로세스를 조율
- 개발 시작 전 애자일·QA 스터디를 진행해 기획자와 개발자의 용어와 요구사항을 맞추고 API 명세 작성 과정의 재작업을 줄임

## Education & Certifications

- **경북대학교** 컴퓨터학부 · 전공 `2021.03 – 2027.02 (졸업 예정)`
- **정보처리산업기사** `2022.08` &nbsp;·&nbsp; **SQLD** `2022.12`

---

## Awards

| 수상 | 주최 | 연도 |
|---|---|---|
| [하계 종합 학술대회 **동상**](<https://github.com/wlgns12370/wlgns12370/blob/main/%EC%88%98%EC%83%81%EB%B0%8F%EA%B2%BD%EB%A0%A5%EC%9D%B8%EC%A6%9D/2026_06_06_2026%EB%85%84%20%ED%95%9C%EA%B5%AD%EC%A0%95%EB%B3%B4%EA%B8%B0%EC%88%A0%ED%95%99%ED%9A%8C%20%ED%95%98%EA%B3%84%EC%A2%85%ED%95%A9%ED%95%99%EC%88%A0%EB%8C%80%ED%9A%8C.pdf>) | 한국정보기술학회장 | 2026.06 |
| [창업 성과 경진대회 **대상**](<https://github.com/wlgns12370/wlgns12370/blob/main/%EC%88%98%EC%83%81%EB%B0%8F%EA%B2%BD%EB%A0%A5%EC%9D%B8%EC%A6%9D/2025_12_10_2025%ED%95%99%EB%85%84%EB%8F%84_%ED%95%98%EB%B0%98%EA%B8%B0_%EC%B0%BD%EC%97%85_%EC%84%B1%EA%B3%BC_%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C.JPG>) | 경북대학교 소프트웨어교육원 | 2025.12 |
| [창업 성과 경진대회 **장려상**](<https://github.com/wlgns12370/wlgns12370/blob/main/%EC%88%98%EC%83%81%EB%B0%8F%EA%B2%BD%EB%A0%A5%EC%9D%B8%EC%A6%9D/2022_11_28_%EA%B2%BD%EB%B6%81%EB%8C%80%ED%95%99%EA%B5%90_IT_%EB%8C%80%ED%95%99_%EC%BB%B4%ED%93%A8%ED%84%B0%ED%95%99%EB%B6%80_%EC%B0%BD%EC%97%85_%EC%84%B1%EA%B3%BC_%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C.JPG>) | 경북대학교 LINC 사업단 | 2022.11 |
| [KNU 창업 경진대회 **최우수상**](<https://github.com/wlgns12370/wlgns12370/blob/main/%EC%88%98%EC%83%81%EB%B0%8F%EA%B2%BD%EB%A0%A5%EC%9D%B8%EC%A6%9D/2022_08_25_%EB%8C%80%EA%B5%AC_%EB%B6%81%EA%B5%AC_%EC%B2%AD%EB%85%84_%EB%86%80%EC%9D%B4%ED%84%B0%EC%99%80_%ED%95%A8%EA%BB%98%ED%95%98%EB%8A%94_2022_KNU_%EC%B0%BD%EC%97%85%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C.JPG>) | 경북대학교 LINC 사업단 | 2022.08 |
| [창업아이템 경진대회 **최우수상**](<https://github.com/wlgns12370/wlgns12370/blob/main/%EC%88%98%EC%83%81%EB%B0%8F%EA%B2%BD%EB%A0%A5%EC%9D%B8%EC%A6%9D/2022_06_20_2022-1%ED%95%99%EA%B8%B0_%EC%B0%BD%EC%97%85%EC%95%84%EC%9D%B4%ED%85%9C_%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C.JPG>) | 경북대학교 소프트웨어교육원 | 2022.06 |
| [대구 북구 청년창업 경진대회 수상](<https://github.com/wlgns12370/wlgns12370/blob/main/%EC%88%98%EC%83%81%EB%B0%8F%EA%B2%BD%EB%A0%A5%EC%9D%B8%EC%A6%9D/2022_03_29_2022%EB%85%84_%EC%B2%AD%EB%85%84%EC%B0%BD%EC%97%85%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C.JPG>) | 대구광역시 북구청장 | 2022.03 |

---
