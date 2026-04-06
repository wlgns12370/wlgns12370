## 유지훈 · Backend Developer

비즈니스 기반 개념간 격벽을 중요하게 생각하고, 성장을 중요시 하는 백엔드 개발자입니다.  
팀원과의 기술적 의사결정 과정을 중요하게 생각하고, 수치와 시스템 안정성 기반으로 합의점을 찾습니다.

📬 wlgns12370@gmail.com · [Blog](https://keephun.tistory.com/3)

---

## Skills

**Backend** &nbsp; `Java` `Spring Boot` `Spring Data JPA`  
**Database** &nbsp; `MySQL` `Redis`  
**Testing** &nbsp;&nbsp;&nbsp; `JUnit5` `Mockito` `Locust` `K6`  
**DevOps** &nbsp;&nbsp;&nbsp; `Docker` `AWS EC2 · RDS · S3`

---

## Projects

### [모의 수능 신청 서비스](https://github.com/mosu-dev)
> DAU 580 · MAU 11,400 · 등록 사용자 3,000명 | Java 21, Spring Boot, MySQL, Locust

- 정원 초과 없이 20초 안에 1,800명을 동시 처리해야 하는 문제를, 팀원과 전략별 부하 테스트 비교 후 ConcurrentHashMap + CAS로 합의
- 락 없음(93 RPS) 대비 **처리량 43% 향상(133.54 RPS)**, 데이터 정합성 동시 확보
- Discord 웹훅 에러를 경고·주의·확인 3단계로 분리하여 운영 중 장애 대응 체계화

### [비수도권 스타트업 인력난 문제 해소 서비스](https://github.com/Principes-Artis-Mechanicae)
> Java 17, Spring Boot, MySQL, Redis | 2022 대구 북구 청년창업 경진대회 수상

- 선택도가 낮은 ENUM 컬럼의 복합 인덱스 포함 여부를 두고 EXPLAIN ANALYZE로 직접 검증 → **쿼리 실행 시간 2.02ms → 0.069ms (29x 단축)**
- JPA → MyBatis 교체 가능성을 고려해 30개 Port 인터페이스로 의존성 역전, Port & Adapter 아키텍처 도입

### [가두모집 홍보 서비스](https://github.com/Ring-Us)
> DAU 2,200 · 동아리 부스 84개 | Java 21, Spring Boot, MySQL, Redis, K6

- Redis Sorted Set + 1시간 주기 RDB 스냅샷 + AOF로 실시간 랭킹 구현 및 데이터 지속성 확보
- 기획팀 당일 요청으로 피크 타임 이벤트 기능을 Feature Toggle 패턴 적용해 2시간 내 배포
- k6로 사용자 페르소나 기반 부하 시나리오 직접 설계, 1,000 RPS 환경에서 p95 응답속도 50ms 이하 확인

---

## Awards

| 수상 | 주최 | 연도 |
|---|---|---|
| 창업 성과 경진대회 **대상** | 경북대학교 소프트웨어교육원 | 2025.12 |
| KNU 창업 경진대회 **최우수상** | 경북대학교 LINC 사업단 | 2022.08 |
| 창업 성과 경진대회 최우수상 | 경북대학교 소프트웨어교육원 | 2022.06 |
| 대구 북구 청년창업 경진대회 수상 | 대구광역시 북구청장 | 2022.03 |

---

## Education & Certifications

- **경북대학교** 소프트웨어학부 · 전공 GPA 3.71 / 4.5 &nbsp; `2021.03 –`
- **정보처리산업기사** `2022.08` &nbsp;·&nbsp; **SQLD** `2022.12`
- **LG AIMERS 3기** 수료 `2023`

---

## Activity

- Google Developer Group on Campus KNU · Core 5기 &nbsp; `2025.09 –`
- [시스템도서위원회](https://github.com/Committee-of-System-Library/knu-tech-talk-arena-server) &nbsp; `2025.9 –`
- [Principes](https://github.com/Principes-Artis-Mechanicae) (개발 동아리) &nbsp; `2023.03 – 2024.12`
- [Get-P](https://github.com/get-p-dev) &nbsp; `2022.02 – 2022.12`
