<p align="center">
  <img src="https://github.com/user-attachments/assets/e62b2a41-740a-4b73-a011-ecbefb8fa80c"
       width="150" height="150" alt="Eventee Logo" />
</p>

<h2 align="center">“모든 단기 이벤트를 티켓 한 장처럼 가볍게”</h2>

<p align="center">
참여자 명단, 공지, 투표, 게시글처럼 여러 곳에 흩어진 운영 요소들을<br>
<b>한 화면에서 빠르게 관리할 수 있는 행사 운영 올인원 플랫폼</b>입니다.<br>
Eventee는 팀·동아리 행사, 공연, MT, 데모데이, 소규모 모임 등<br>
누구나 Google 계정만으로 즉시 시작할 수 있는 실용 중심 서비스입니다.
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/3c690eb1-bc1a-4858-be33-83caf95797ab"
       width="600" alt="Eventee Preview" />
</p>

---

## 🌼 **Core Values**

### **01. 참여자 목록을 한눈에**

- 이벤트 참여자/팀원을 한 화면에서 빠르게 확인
- 그룹 UI로 운영자가 즉시 파악 가능

### **02. 중요한 공지를 빠르게 전달**

- 일정 변경, 안내 사항 등 공지를 손쉽게 전달
- 구성원에게 실시간으로 반영되는 알림 구조

### **03. 투표·게시글 기반 실시간 소통**

- 게시글/댓글을 통한 자연스러운 커뮤니케이션
- 투표 기능으로 의견 수집 및 빠른 의사결정

---

## 🏗️ **Service Architecture (3-Tier)**

### **Frontend (Presentation Tier)**

- **React**
- **CloudFront + S3** 정적 호스팅
- 사용자 요청/응답 및 UI 렌더링 담당

### **Backend (Application Tier)**

- **Spring Boot 3.x**
- **JWT 기반 인증/인가**
- 이벤트·그룹·공지·투표 등 핵심 비즈니스 로직 처리

### **Data Tier**

- **PostgreSQL (RDS)** — 메인 DB
- **Redis (ElastiCache)** — Token/Cache Store
- **S3** — 이미지 및 파일 저장소

<p align="center">
  <img src="https://github.com/user-attachments/assets/4fd33203-cac2-4f98-9e10-8419b9f58263"
       width="620"
       alt="Service Architecture Diagram" />
</p>

---

## ☁️ **Infra Architecture**

- **Route53 + ACM** 기반 HTTPS 인증
- **Application Load Balancer(ALB)** 로 API 트래픽 분산
- **Auto Scaling Group(ASG)** 기반 API 서버 운영
- **S3 Presigned URL** 기반 안전한 이미지 업로드
- **Docker + Watchtower** 자동 업데이트 환경
- **GitHub Actions** CI/CD 배포 자동화
- **Grafana · Prometheus · Loki** 서버·로그 모니터링
- **AWS CostExplorer + Lambda** 기반 비용 자동 알림 (Discord Webhook)

<p align="center">
  <img src="https://github.com/user-attachments/assets/833ac4e7-1c37-467a-b069-724df2825fd4"
       width="700"
       alt="Infra Architecture Diagram" />
</p>

---

# 🔧 **Monitoring & Ops**

Eventee는 Auto Scaling 환경에서도 안정적인 관측성을 유지하기 위해  
모니터링 인프라를 **전용 EC2**에서 별도로 운영합니다.

### ✔ Prometheus — 자동 메트릭 수집
- EC2 **Tag 기반 Service Discovery** 적용  
- ASG 인스턴스 생성/삭제에도 자동 감지  
- `/actuator/prometheus` 메트릭 수집  
- Node Exporter / cAdvisor 포함

### ✔ Loki — 로그 수집
- Spring App(ASG) 로그를 loki4j로 전송해 Loki에 저장
- Grafana에서 메트릭 + 로그를 한 화면에서 통합 조회 가능

### ✔ Grafana — 실시간 대시보드
- API 성능, 오류율, 상태 지표 시각화  
- Loki 로그 기반 문제 추적 가능

### ✔ 비용 자동 알림 (Cost Monitoring)
- AWS Cost Explorer  
- Lambda 분석 후 Discord Webhook 전송  
- 일일 비용 / 월 예측 비용 / 이상 패턴 감지

<p align="center">
  <img src="https://github.com/user-attachments/assets/816556f8-3fa0-4337-a89b-5706a4f46ca7"
       width="700"
       alt="Monitoring Architecture Diagram" />
</p>


---

