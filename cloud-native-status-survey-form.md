# 클라우드 네이티브 전환 현황조사서 양식

## 0. 문서 정보

| 항목 | 작성값 |
|---|---|
| 기관명 |  |
| 사업명 |  |
| 조사 대상 시스템 |  |
| 작성 부서 |  |
| 작성자 |  |
| 연락처 |  |
| 작성일 |  |
| 검토자 |  |
| 버전 | v0.1 |

## 작성 기준

- 본 양식은 행정·공공기관 클라우드 전환·통합사업의 현황조사에 활용한다.
- 각 항목은 가능한 한 `현행값`, `근거 자료`, `Cloud 전환 영향`, `상세설계 반영사항`을 함께 작성한다.
- 불명확한 항목은 비워두지 말고 `확인 필요`, `자료 없음`, `담당자 인터뷰 필요`처럼 상태를 명시한다.
- Cloud Native 전환 검토를 위해 Session, File, Config, Log, Interface, DB 종속성, License, 보안 제약을 중점적으로 확인한다.

---

# 1. 정보시스템 현황조사

## 1.1 정보시스템 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 시스템명 |  | 공식 명칭, 약칭 포함 | 시스템 목록, 운영 문서 | 전환 대상 식별 기준 | 시스템 식별자 정의 |
| 2 | 업무명 |  | 지원하는 업무 영역 | 업무 매뉴얼 | 업무 영향도 판단 | 업무 도메인 분류 |
| 3 | 운영기관 |  | 주관기관, 운영기관 | 조직도, 계약서 | 책임 범위 판단 | 운영 R&R 반영 |
| 4 | 담당부서 |  | 업무/운영/기술 담당 구분 | 담당자 인터뷰 | 협의 채널 확보 | 의사결정 체계 반영 |
| 5 | 서비스 대상 |  | 대국민/내부/유관기관/행정기관 | 서비스 소개서 | 보안 및 가용성 수준 판단 | 접근 경로 설계 |
| 6 | 운영 상태 |  | 운영중/개선중/폐기예정/신규 | 운영 현황 자료 | 전환 제외 여부 판단 | Migration 범위 정의 |
| 7 | 운영 시간 |  | 24x365/업무시간/특정기간 | 운영 정책 | Cutover 가능 시간 판단 | 배포/전환 계획 반영 |
| 8 | 사용자 규모 |  | 일/월 사용자, 동시접속자 | 접속 로그, 통계 | 용량 산정 영향 | Scaling 기준 반영 |
| 9 | 트래픽 특성 |  | 평상시/피크/시즌성 | 모니터링 자료 | Auto Scaling 필요성 | 성능 설계 반영 |
| 10 | 장애 영향도 |  | 국민 불편, 법정업무 지연 등 | 장애 보고서 | 가용성 등급 산정 | HA/DR 설계 반영 |
| 11 | 현행 운영환경 |  | 자체 IDC/G-Cloud/민간 Cloud/Hybrid | 구성도 | 전환 방식 판단 | Landing Zone 설계 |
| 12 | 전환 희망 여부 |  | 필요/보류/제외/검토필요 | 기관 요구사항 | 우선순위 판단 | 전환 Roadmap 반영 |

## 1.2 서버 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 서버명 |  | Hostname, 관리번호 | CMDB, 서버 목록 | 대상 서버 식별 | Resource Naming 반영 |
| 2 | 서버 역할 |  | Web/WAS/DB/Batch/File/Interface | 구성도 | 서비스 분리 기준 | Tier별 설계 |
| 3 | 물리/가상 구분 |  | Physical/VM | 인프라 목록 | Rehost 난이도 | VM 또는 Container 전환 기준 |
| 4 | OS |  | 제품명, Version, Bit | 서버 점검 결과 | 호환성, EOS/EOL 판단 | Base Image/OS 선정 |
| 5 | CPU |  | Core, 평균/최대 사용률 | 모니터링 | 용량 산정 | vCPU 산정 |
| 6 | Memory |  | 총량, 평균/최대 사용률 | 모니터링 | 용량 산정 | Memory Request/Limit 산정 |
| 7 | Disk |  | OS/Data/Log 영역 | df, 스토리지 자료 | Storage 유형 판단 | Block/File/Object 설계 |
| 8 | IP 정보 |  | 공인/사설/NAT 여부 | 네트워크 구성도 | 방화벽, Routing 영향 | IP 대역 및 NAT 설계 |
| 9 | 이중화 구성 |  | Active-Active/Active-Standby/단일 | 구성도 | 가용성 Gap 판단 | HA 설계 |
| 10 | 서버 간 의존성 |  | 특정 서버 고정 처리 여부 | 설정파일, 인터뷰 | Container 전환 제약 | Affinity 제거 방안 |
| 11 | 노후도 |  | EOS/EOL, 교체 필요 | 제조사 공지 | Migration 위험 | Modernization 범위 |
| 12 | Container 전환 가능성 |  | 가능/일부/어려움 | 실행 방식 분석 | Cloud Native 적합성 | Container 설계 여부 |

## 1.3 스토리지 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 스토리지 종류 |  | SAN/NAS/DAS/Object Storage | 스토리지 목록 | 대체 서비스 판단 | Storage Class 선정 |
| 2 | 사용 시스템 |  | 연결 시스템명 | 구성도 | 영향 범위 판단 | 공유 Storage 설계 |
| 3 | 할당 용량 |  | 전체 할당량 | 관리 콘솔 | 비용/용량 산정 | 초기 용량 산정 |
| 4 | 실제 사용량 |  | 사용량, 사용률 | 모니터링 | 이관 시간 산정 | Migration 계획 |
| 5 | 증가율 |  | 일/월/년 증가량 | 사용량 추이 | 확장성 필요성 | Auto Expansion 기준 |
| 6 | 저장 데이터 유형 |  | 첨부파일/로그/이미지/문서 | 디렉터리 분석 | Object 전환 가능성 | Object Storage 설계 |
| 7 | 공유 여부 |  | 단일/다중 서버 공유 | Mount 정보 | Stateless 영향 | Shared Storage 설계 |
| 8 | 성능 요구 |  | IOPS, Throughput, Latency | 성능 자료 | Storage Tier 영향 | 성능 등급 선정 |
| 9 | 암호화 여부 |  | 적용/미적용 | 보안 설정 | 보안요건 영향 | KMS/Encryption 설계 |
| 10 | Local Disk 의존 |  | 있음/없음 | 소스, 설정파일 | Container 전환 위험 | 경로 외부화 방안 |

## 1.4 백업 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 백업 대상 |  | 서버/DB/File/설정/Application | 백업 정책서 | 누락 대상 확인 | Backup Scope 정의 |
| 2 | 백업 방식 |  | Full/Incremental/Differential/Snapshot | 백업 솔루션 | 복구 방식 영향 | Backup Architecture |
| 3 | 백업 주기 |  | 일/주/月/실시간 | 백업 스케줄 | RPO 판단 | Backup Schedule |
| 4 | 보관 위치 |  | Tape/NAS/Object/원격지 | 백업 구성도 | DR 영향 | Cross Region 보관 |
| 5 | 보관 기간 |  | 단기/장기 기간 | 규정, 정책 | 비용/규정 영향 | Lifecycle 정책 |
| 6 | RTO |  | 목표 복구 시간 | SLA | HA/DR 수준 판단 | 복구 설계 |
| 7 | RPO |  | 허용 데이터 손실 | SLA | Replication 필요성 | 복제 전략 |
| 8 | 복구 테스트 |  | 수행/미수행/주기 | 테스트 결과 | 신뢰성 판단 | DR Drill 계획 |
| 9 | 백업 암호화 |  | 적용/미적용 | 설정값 | 보안요건 | 암호화 설계 |
| 10 | Managed Backup 가능성 |  | 가능/일부/어려움 | 대상 분석 | 운영 자동화 영향 | Managed Service 활용 |

## 1.5 네트워크 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 네트워크 구성도 |  | L2/L3/Router/Switch/LB | 구성도 | 구조 이해 | Target Network 설계 |
| 2 | 망 구분 |  | 인터넷망/업무망/행정망/DMZ | 망 구성도 | 보안 경계 판단 | Subnet 분리 |
| 3 | IP 대역 |  | CIDR, VLAN, Subnet | IP 관리대장 | 주소 충돌 위험 | VPC/VNet CIDR 설계 |
| 4 | 외부 접속 경로 |  | 사용자, 기관, 관리자 경로 | 구성도 | 접근 통제 영향 | Ingress/Egress 설계 |
| 5 | Load Balancer |  | L4/L7, VIP, Health Check | LB 설정 | 가용성 영향 | Cloud LB 설계 |
| 6 | DNS |  | 내부/외부 DNS, 도메인 | DNS 설정 | 전환 Cutover 영향 | DNS 전환 계획 |
| 7 | VPN/전용회선 |  | IPsec/SSL/전용회선 | 회선 계약 | Hybrid 연결 영향 | Connectivity 설계 |
| 8 | Inbound Port |  | 출발지, 목적지, Port | 방화벽 정책 | 보안정책 변경 | Security Group 정책 |
| 9 | Outbound Port |  | 목적지, Port, 용도 | 방화벽 정책 | 연계 영향 | Egress 정책 |
| 10 | 대역폭 |  | 평균/최대 사용량 | 회선 모니터링 | 회선 용량 산정 | Direct Connect/VPN 용량 |

## 1.6 보안장비 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | Firewall |  | 장비명, 정책 수, 주요 Rule | 보안정책서 | 정책 이관 필요 | Security Group/NACL 설계 |
| 2 | WAF |  | 적용 URL, 정책 | WAF 설정 | Web 보호 수준 | Cloud WAF 설계 |
| 3 | IPS/IDS |  | 탐지/차단 구성 | 보안장비 설정 | 관제 연계 영향 | Cloud IDS/IPS 검토 |
| 4 | DDoS 대응 |  | 장비/서비스 | 보안 구성도 | 대국민 서비스 보호 | DDoS Protection 설계 |
| 5 | VPN |  | SSL/IPsec, 사용자 수 | VPN 설정 | 관리자 접근 영향 | Bastion/VPN 설계 |
| 6 | NAC |  | 적용 범위 | NAC 정책 | 내부 접근 제어 | 접근통제 설계 |
| 7 | Proxy/Web Gateway |  | URL Filtering, Proxy | Proxy 설정 | Outbound 제어 | Egress Gateway 설계 |
| 8 | SIEM 연계 |  | 관제 시스템 연계 | 로그 연계 문서 | 로그 수집 영향 | Security Logging 설계 |
| 9 | 인증서 |  | 인증서명, 만료일, 발급기관 | 인증서 목록 | Cutover 위험 | Certificate 관리 |
| 10 | KMS/HSM |  | 적용 여부 | 보안정책 | 암호키 관리 | Key Management 설계 |

## 1.7 SW 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | SW 명 |  | OS/Middleware/DB/Tool/Solution | SW 자산대장 | 전환 대상 식별 | 대체/이관 전략 |
| 2 | Version |  | 상세 Version | 설치 정보 | 호환성 판단 | Upgrade 필요성 |
| 3 | 제조사/공급사 |  | Vendor, 파트너 | 계약서 | 지원 가능성 | 지원 체계 반영 |
| 4 | License 방식 |  | Core/User/Server/Subscription | 라이선스 계약 | Cloud 반입 제약 | BYOL/구독 설계 |
| 5 | 보유/사용 수량 |  | 보유, 사용, 잔여 | 자산대장 | 증설 가능성 | 비용 산정 |
| 6 | 유지보수 여부 |  | 계약기간, 지원 종료일 | 계약서 | 운영 위험 | 교체 계획 |
| 7 | EOS/EOL |  | 종료 여부, 날짜 | Vendor 공지 | 보안/기술 위험 | Modernization 필요 |
| 8 | Cloud 사용 가능 여부 |  | 가능/불가/확인필요 | 라이선스 조건 | 전환 제약 | 대체안 검토 |
| 9 | Managed Service 대체 |  | 가능/일부/불가 | 기능 비교 | 운영 효율 영향 | Managed Service 설계 |
| 10 | 특수 제약 |  | Dongle, MAC 인증, 전용 HW | 인터뷰, 계약 | Cloud 이전 위험 | 예외 설계 |

## 1.8 어플리케이션 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | Application 명 |  | 서비스명, 모듈명 | 소스 구조, 운영 문서 | 대상 식별 | 서비스 단위 정의 |
| 2 | 개발 언어 |  | Java/.NET/PHP/Python/Node.js 등 | 소스, 빌드 파일 | Runtime 호환성 | Runtime 선정 |
| 3 | Framework |  | Spring/전자정부프레임워크/Struts 등 | pom.xml, 설정파일 | Container 호환성 | Framework Upgrade 검토 |
| 4 | Runtime/WAS |  | Tomcat/WebLogic/JEUS/JBoss 등 | WAS 설정 | License, 호환성 | Container Image 설계 |
| 5 | 배포 단위 |  | WAR/JAR/EAR/Binary/Script | 배포 파일 | CI/CD 영향 | Build Pipeline 설계 |
| 6 | 실행 방식 |  | WAS/독립 프로세스/Batch | 기동 스크립트 | Container 전환 영향 | Entrypoint 설계 |
| 7 | Session 관리 |  | Memory/DB/Redis/Sticky | 소스, WAS 설정 | 수평 확장 영향 | Session Store 설계 |
| 8 | File 처리 |  | Local/NAS/Object | 소스, 설정 | Stateless 영향 | Object/File Storage 설계 |
| 9 | Config 관리 |  | 소스/파일/환경변수 | 설정파일 | 환경 분리 영향 | ConfigMap/Secret 설계 |
| 10 | Log 처리 |  | Local/중앙/미수집 | 로그 설정 | Observability 영향 | Logging 설계 |
| 11 | Health Check |  | 있음/없음 | Endpoint 확인 | Kubernetes 운영 영향 | Liveness/Readiness 설계 |
| 12 | 수평 확장 가능성 |  | 가능/제한/불가 | 구조 분석 | Scale-out 영향 | Scaling 정책 |

## 1.9 연계 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 연계명 |  | 업무 기준 명칭 | 연계 목록 | 식별 기준 | Interface ID 정의 |
| 2 | 연계 시스템 |  | 송신/수신 시스템 | 연계 정의서 | 영향 범위 | Dependency Map |
| 3 | 연계 기관 |  | 내부/외부/타 행정기관 | 계약, 협약 | 협의 필요성 | 대외 협의 계획 |
| 4 | 연계 방향 |  | Inbound/Outbound/양방향 | 흐름도 | 방화벽 영향 | Network Policy 설계 |
| 5 | 연계 방식 |  | REST/SOAP/File/DB Link/EAI/MQ/Socket | 소스, 설정 | 전환 난이도 | 연계 전환 방식 |
| 6 | 연계 주기 |  | 실시간/배치/수시 | 스케줄 | 성능/장애 영향 | Queue/Retry 설계 |
| 7 | 데이터 형식 |  | JSON/XML/CSV/Fixed Length | 전문 정의서 | 변환 필요성 | Schema 관리 |
| 8 | 인증 방식 |  | 인증서/API Key/OAuth/IP 제한 | 연계 설정 | 인증 변경 필요 | Secret/Certificate 설계 |
| 9 | 암호화 |  | TLS/전문/파일 암호화 | 보안정책 | 보안요건 | 암호화 설계 |
| 10 | 오류 처리 |  | Retry/Queue/수동 재처리 | 운영 절차 | 장애 복원력 | Resilience Pattern |
| 11 | 전환 영향 |  | IP/Endpoint/Port 변경 여부 | 인터뷰 | Cutover 위험 | 연계 테스트 계획 |

## 1.10 DBMS 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | DBMS 명 |  | Oracle/Tibero/PostgreSQL/MySQL/MSSQL 등 | DB 자산대장 | 전환 방식 판단 | DB Target 선정 |
| 2 | Version |  | 상세 Version | DB 접속 정보 | 호환성 판단 | Upgrade/Migration 계획 |
| 3 | 구성 방식 |  | Single/HA/RAC/Replication | DB 구성도 | 가용성 영향 | Managed DB HA 설계 |
| 4 | DB 용량 |  | Data/Index/Log/Archive | DBA 자료 | 이관 시간/비용 | Migration 용량 산정 |
| 5 | 접속 Application |  | 연결 App 목록 | Connection 정보 | 영향 범위 | Connection 설계 |
| 6 | 계정 현황 |  | 업무/운영/관리자 계정 | 계정 목록 | 보안 영향 | IAM/DB 권한 설계 |
| 7 | 백업 방식 |  | Dump/RMAN/Snapshot | 백업 정책 | 복구 방식 | Backup 설계 |
| 8 | 암호화 |  | TDE/Column/File | DB 설정 | 보안요건 | Encryption 설계 |
| 9 | 성능 지표 |  | TPS/QPS/Connection/Slow Query | AWR, 모니터링 | DB Sizing | 성능 설계 |
| 10 | Managed DB 가능성 |  | 가능/일부/어려움 | 기능 비교 | 운영 방식 영향 | DB 운영 모델 |

## 1.11 DBMS 현황 상세

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | Schema 목록 |  | 업무별 Schema, Owner | DBA 자료 | 이관 범위 | Schema Migration |
| 2 | Table 수 |  | 전체/핵심 Table | DB Dictionary | 이관 복잡도 | Data Migration 범위 |
| 3 | 대용량 Table |  | 용량 상위 Table | 용량 분석 | 이관 시간 | 분할 이관 전략 |
| 4 | Index 현황 |  | 주요 Index, 비효율 Index | DBA 분석 | 성능 영향 | Index 재구성 |
| 5 | Procedure/Function |  | 목록, 업무 의존도 | DB Dictionary | DB 종속성 | Application 전환 검토 |
| 6 | Trigger |  | 목록, 처리 내용 | DB Dictionary | Hidden Logic 위험 | 로직 재설계 |
| 7 | DB Link |  | 대상 DB, 용도 | DB 설정 | Cloud 네트워크 영향 | 대체 연계 방식 |
| 8 | Sequence/채번 |  | 채번 방식 | DB Dictionary | 분산 처리 영향 | ID 생성 전략 |
| 9 | Partition |  | 적용 Table, 기준 | DBA 자료 | 성능/이관 영향 | Partition 전략 |
| 10 | Character Set |  | DB/Client Character Set | DB 설정 | 데이터 깨짐 위험 | 변환 검증 |
| 11 | Vendor 종속 SQL |  | Oracle Hint, 전용 함수 등 | 소스 분석 | DB 전환 위험 | SQL Refactoring |

## 1.12 클라우드 전환관련 시스템현황 및 요구사항 조사

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 전환 목적 |  | 비용/확장성/안정성/Cloud Native | 요구사항 인터뷰 | 방향성 결정 | 목표 Architecture |
| 2 | 전환 유형 |  | Rehost/Replatform/Refactor/Rebuild/Retire | 진단 결과 | 일정/비용/위험 영향 | Migration Strategy |
| 3 | 목표 환경 |  | 공공 Cloud/민간 Cloud/Hybrid | 기관 정책 | CSP 선정 | Landing Zone |
| 4 | Container 요구 |  | Kubernetes/OpenShift/PaaS 여부 | 기술 요구사항 | Platform 설계 영향 | Container Platform |
| 5 | Managed Service 요구 |  | DB/Cache/Storage/MQ/Monitoring | 요구사항 | 운영 방식 변화 | Managed Service 설계 |
| 6 | 무중단 요구 |  | 무중단/최소중단/점검시간 가능 | SLA | 전환 방식 영향 | Cutover 전략 |
| 7 | 성능 요구 |  | TPS, 응답시간, 동시접속자 | SLA, 로그 | Sizing 영향 | 성능 기준 |
| 8 | 보안 요구 |  | 망분리, 암호화, 접근통제 | 보안정책 | 설계 제약 | Security Architecture |
| 9 | 운영 요구 |  | Monitoring, Alert, 자동복구 | 운영 요구사항 | 운영 체계 영향 | Ops 설계 |
| 10 | DevOps 요구 |  | CI/CD, 자동배포, Rollback | 개발 프로세스 | 자동화 수준 | Pipeline 설계 |
| 11 | Observability 요구 |  | Log/Metric/Trace/Dashboard | 운영 요구사항 | 장애 분석 수준 | Observability 설계 |
| 12 | 주요 제약사항 |  | 법/연계/License/기술부채 | 인터뷰, 계약 | 위험도 산정 | Risk 대응계획 |

## 1.13 네트워크 보안담당자 현황

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 담당자명 |  | 기관/운영/협력사 담당자 | 조직도 | 협의 채널 | R&R 정의 |
| 2 | 소속 |  | 부서, 업체 | 조직도 | 승인 주체 확인 | 의사결정 체계 |
| 3 | 역할 |  | 네트워크/보안/DNS/인증서 | 인터뷰 | 작업 범위 확인 | 작업 계획 |
| 4 | 연락처 |  | 전화, Email | 담당자 목록 | 긴급 대응 | 커뮤니케이션 계획 |
| 5 | 담당 범위 |  | Firewall, VPN, WAF, DNS 등 | 인터뷰 | 변경 요청 범위 | 변경관리 계획 |
| 6 | 승인 절차 |  | 방화벽, VPN, 보안성 검토 | 업무 절차서 | Lead Time 영향 | 전환 일정 Risk |
| 7 | 작업 가능 시간 |  | 평일/야간/주말/점검시간 | 운영 정책 | Cutover 영향 | 작업 Window |
| 8 | Cloud 전환 협의사항 |  | IP, 회선, 보안정책, 관제 | 회의록 | 전환 전 선행조건 | 사전 협의 과제 |

## 1.14 기존 CSP 현황조사

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | CSP 명 |  | NCP/KT/NHN/AWS/Azure 등 | 계약서, 콘솔 | 현재 Cloud 의존성 | Target CSP 비교 |
| 2 | 사용 서비스 |  | VM/DB/Storage/Kubernetes/LB 등 | 콘솔 Export | 서비스 대체성 | 서비스 매핑 |
| 3 | Region/Zone |  | 사용 위치 | 콘솔 | 데이터 위치/DR | Region 설계 |
| 4 | Account 구조 |  | Account/Project/Organization | 콘솔 | 권한 구조 영향 | Account Governance |
| 5 | Network 구조 |  | VPC/Subnet/Routing/NAT/VPN | 구성도 | 이전 영향 | Network 재설계 |
| 6 | 보안 구성 |  | IAM/SG/WAF/KMS | 콘솔 | 보안 정책 이관 | Security Baseline |
| 7 | 과금 현황 |  | 월 비용, 주요 비용 항목 | 청구서 | 비용 최적화 | Cost Model |
| 8 | 운영 방식 |  | Console/IaC/자동화 | 운영 인터뷰 | 운영 성숙도 | IaC 적용 여부 |
| 9 | 계약/SLA |  | 계약 형태, SLA | 계약서 | 서비스 수준 | SLA 설계 |
| 10 | Lock-in 요소 |  | 전용 API, Managed 기능 의존 | 구조 분석 | 이전 난이도 | 대체 설계 |

## 1.15 개인정보영향평가 대상여부

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 개인정보 처리 여부 |  | 처리/미처리 | 개인정보 처리방침 | 보안 수준 영향 | Privacy 설계 |
| 2 | 개인정보 항목 |  | 이름, 연락처, 주소, 계좌 등 | 테이블 정의서 | 암호화 대상 | Data Protection |
| 3 | 고유식별정보 |  | 주민번호, 여권번호 등 | 테이블 정의서 | 법적 요건 | 암호화/접근통제 |
| 4 | 민감정보 |  | 건강, 생체, 사상 등 | 업무 정의 | 고위험 판단 | 강화 보안 |
| 5 | 처리 규모 |  | 정보주체 수, 건수 | DB 통계 | 영향평가 대상 판단 | Risk 등급 |
| 6 | 외부 제공 여부 |  | 제공 대상, 항목 | 업무 문서 | 위탁/제공 관리 | 연계 보안 |
| 7 | 위탁 처리 여부 |  | Cloud, 운영, 유지보수 위탁 | 계약서 | 책임 범위 | 위탁관리 설계 |
| 8 | 암호화 적용 |  | 저장/전송 암호화 | 설정, 보안정책 | 보안 Gap | 암호화 설계 |
| 9 | 접근통제 |  | 권한, 접속기록, 감사로그 | 권한표 | 감사 대응 | IAM/Logging |
| 10 | 영향평가 대상 판단 |  | 대상/비대상/추가검토 | 법령, 기준 | 선행 절차 영향 | 개인정보영향평가 계획 |

## 1.16 시스템 중요도 등급

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud 전환 영향 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 업무 중요도 |  | 핵심/중요/일반 | 기관 기준 | 우선순위 영향 | 등급별 설계 |
| 2 | 장애 영향도 |  | 대국민/법정업무/내부업무 영향 | 장애 분석 | 가용성 수준 | HA/DR |
| 3 | 데이터 중요도 |  | 개인정보/행정정보/기밀정보 | 데이터 분류 | 보안 수준 | Data Security |
| 4 | RTO |  | 목표 복구 시간 | SLA | DR 수준 | 복구 설계 |
| 5 | RPO |  | 허용 데이터 손실 | SLA | 복제 방식 | Backup/Replication |
| 6 | 가용성 요구 |  | 99.5/99.9/99.99 등 | SLA | Multi-AZ 필요성 | Availability 설계 |
| 7 | 성능 중요도 |  | 피크 민감도 | 모니터링 | Scaling 요구 | Capacity 설계 |
| 8 | 보안 중요도 |  | 보안사고 영향 | 보안 등급 | 보안 통제 | Security Level |
| 9 | 중요도 등급 |  | 1/2/3등급 등 기관 기준 | 등급 산정표 | 설계 기준 결정 | 표준 Architecture 매핑 |

---

# 2. 응용시스템 현황조사

## 2.1 응용시스템 정의서

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud Native 검토 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 응용시스템 ID |  | 고유 식별자 | 시스템 목록 | 서비스 분리 기준 | Service ID |
| 2 | 응용시스템명 |  | 공식 명칭 | 업무 문서 | 대상 식별 | Naming |
| 3 | 시스템 목적 |  | 구축 목적, 업무 목표 | 제안서, 산출물 | 도메인 이해 | Domain 정의 |
| 4 | 업무 범위 |  | 처리하는 업무 영역 | 업무 정의서 | Bounded Context 후보 | 업무 Scope |
| 5 | 사용자 유형 |  | 국민/공무원/기관/관리자 | 권한표 | 접근 패턴 | IAM 설계 |
| 6 | 주요 기능 |  | 핵심 기능 목록 | 메뉴 구조, 기능 목록 | 기능 분할 기준 | 서비스 후보 |
| 7 | 서비스 채널 |  | Web/Mobile/API/Batch/Admin | 구성도 | Channel 분리 | Ingress/API 설계 |
| 8 | 업무 프로세스 |  | 주요 처리 흐름 | 업무 흐름도 | Event 후보 | Process 설계 |
| 9 | 데이터 처리 범위 |  | 입력/조회/승인/통계/연계 | 화면/API 정의 | 데이터 소유권 | Data 설계 |
| 10 | 운영 특성 |  | 상시/기간집중/야간 Batch | 운영 인터뷰 | Scaling/Batch 영향 | 운영 설계 |
| 11 | Microservice 후보 |  | 가능/일부/어려움 | 기능 분석 | 서비스 분리 가능성 | 분할 전략 |

## 2.2 응용시스템 관계서

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud Native 검토 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 관련 시스템 |  | 내부/외부 시스템명 | 구성도 | 의존성 판단 | Dependency Map |
| 2 | 구성 모듈 |  | Web/Admin/Batch/Interface/Report | 소스 구조 | 서비스 분할 후보 | Module 설계 |
| 3 | 모듈 간 관계 |  | 호출 방향, 데이터 흐름 | Sequence, 소스 | 결합도 판단 | API/Event 설계 |
| 4 | DB 관계 |  | Schema, Table, 공통 DB | ERD | DB 공유 여부 | Database 분리 전략 |
| 5 | 파일 관계 |  | 첨부, 업로드, 다운로드 경로 | 소스, 설정 | Stateless 영향 | Storage 설계 |
| 6 | 인증 관계 |  | SSO/인증서/자체 로그인 | 인증 구성도 | 인증 통합 영향 | IAM/Auth 설계 |
| 7 | 공통 모듈 |  | 공통코드, 권한, 알림, 로그 | 소스 구조 | Shared Library 위험 | 공통 서비스 설계 |
| 8 | 장애 전파 관계 |  | 장애 시 영향 모듈 | 장애 이력 | Resilience 필요성 | Circuit Breaker/Retry |
| 9 | 강결합 요소 |  | 직접 DB 호출, 파일 공유 등 | 소스 분석 | 분리 난이도 | Decoupling 과제 |

## 2.3 응용시스템 연계서

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud Native 검토 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 연계 ID |  | 고유 식별자 | 연계 목록 | 추적성 확보 | Interface ID |
| 2 | 연계명 |  | 업무 기준 명칭 | 연계 정의서 | 업무 맥락 | API/Event 명세 |
| 3 | 송신 시스템 |  | 송신 주체 | 연계 구성도 | 방향성 판단 | Producer 정의 |
| 4 | 수신 시스템 |  | 수신 주체 | 연계 구성도 | 방향성 판단 | Consumer 정의 |
| 5 | 연계 목적 |  | 조회/등록/승인/통계/동기화 | 업무 정의 | 동기/비동기 판단 | Pattern 선정 |
| 6 | 연계 방식 |  | REST/SOAP/File/DB Link/MQ/EAI | 소스, 설정 | 전환 난이도 | API Gateway/MQ |
| 7 | Endpoint |  | URL, IP, Port | 설정파일 | Cutover 영향 | Endpoint 관리 |
| 8 | 전문 형식 |  | JSON/XML/CSV/Fixed Length | 전문 정의서 | Schema 관리 | Contract 설계 |
| 9 | 연계 주기 |  | 실시간/일배치/월배치/수시 | 스케줄 | 부하 영향 | Scheduling 설계 |
| 10 | 인증 방식 |  | API Key/OAuth/인증서/IP 제한 | 보안 설정 | Secret 관리 | 인증 설계 |
| 11 | 오류 처리 |  | Retry/Queue/수동 재처리 | 운영 절차 | 복원력 수준 | Error Handling |
| 12 | SLA |  | 응답시간, 처리시간, 가용성 | SLA | 성능 설계 | Timeout/Retry 기준 |
| 13 | 전환 테스트 항목 |  | 방화벽, 인증, 전문, 성능 | 테스트 계획 | 검증 범위 | Integration Test |

## 2.4 응용기능분할서

| No | 대기능 | 중기능 | 소기능 | 기능 설명 | 사용자 | 사용 빈도 | 중요도 | 사용 데이터 | 연계 여부 | Batch 여부 | 분리 가능성 | 전환 우선순위 | Cloud Native 후보 | 비고 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 |  |  |  |  |  | 상/중/하 | 핵심/중요/일반 |  | 있음/없음 | 실시간/Batch | 가능/일부/어려움 | 1차/2차/제외 | API/Microservice/Event/Batch |  |
| 2 |  |  |  |  |  | 상/중/하 | 핵심/중요/일반 |  | 있음/없음 | 실시간/Batch | 가능/일부/어려움 | 1차/2차/제외 | API/Microservice/Event/Batch |  |
| 3 |  |  |  |  |  | 상/중/하 | 핵심/중요/일반 |  | 있음/없음 | 실시간/Batch | 가능/일부/어려움 | 1차/2차/제외 | API/Microservice/Event/Batch |  |

## 2.5 응용기능설계서

| No | 조사 항목 | 작성값 | 작성 기준 | 근거 자료 | Cloud Native 검토 | 상세설계 반영사항 |
|---|---|---|---|---|---|---|
| 1 | 기능 ID |  | 고유 식별자 | 기능 목록 | 추적성 | Function ID |
| 2 | 기능명 |  | 기능 이름 | 메뉴/화면/API | 서비스 후보 | 기능 명세 |
| 3 | 기능 설명 |  | 업무 처리 내용 | 업무 정의서 | 도메인 로직 파악 | 업무 로직 설계 |
| 4 | Actor |  | 사용자/외부시스템/Batch | Use Case | 호출 주체 | 권한/인증 설계 |
| 5 | 입력 정보 |  | 화면 입력/API Request/File | 화면/API 정의 | Validation | Request Schema |
| 6 | 출력 정보 |  | 화면/API Response/File | 화면/API 정의 | Contract | Response Schema |
| 7 | 처리 절차 |  | 단계별 업무 로직 | 소스, 설계서 | Transaction 경계 | Sequence 설계 |
| 8 | 업무 규칙 |  | 승인, 검증, 예외 조건 | 업무 규칙서 | Domain Rule | Rule 설계 |
| 9 | 데이터 처리 |  | Insert/Update/Delete/Select 대상 | CRUD 매트릭스 | 데이터 소유권 | Data Access 설계 |
| 10 | 오류 처리 |  | Validation/시스템/연계 오류 | 소스, 로그 | 복원력 | Error Code/Retry |
| 11 | 권한 조건 |  | Role, 접근제어 조건 | 권한표 | IAM 영향 | Authorization 설계 |
| 12 | 성능 조건 |  | 응답시간, 대량 처리 기준 | SLA | Scaling 영향 | Performance 기준 |
| 13 | 로그 요건 |  | 업무/감사/오류 로그 | 보안정책 | Observability | Logging 설계 |
| 14 | 상태 관리 |  | Stateless/Stateful, Session 사용 | 소스 분석 | Container 영향 | Session 개선 |
| 15 | 전환 설계 반영 |  | API화, Config 분리, Storage 전환 | 분석 결과 | Modernization 범위 | 상세설계 과제 |

---

# 3. 조사 완료 검토표

| No | 검토 항목 | 완료 여부 | 미완료 사유 | 후속 조치 |
|---|---|---|---|---|
| 1 | 전체 시스템 목록이 누락 없이 작성되었는가 |  |  |  |
| 2 | 서버, Storage, Network, Security 정보가 상호 일치하는가 |  |  |  |
| 3 | Application의 Session/File/Config/Log 구조가 확인되었는가 |  |  |  |
| 4 | 주요 Interface의 Endpoint, 인증, 오류 처리 방식이 확인되었는가 |  |  |  |
| 5 | DBMS의 용량, 종속 SQL, Procedure, DB Link가 확인되었는가 |  |  |  |
| 6 | 개인정보 처리 및 영향평가 대상 여부가 검토되었는가 |  |  |  |
| 7 | 시스템 중요도 등급과 RTO/RPO가 확인되었는가 |  |  |  |
| 8 | Cloud 전환 유형과 요구사항이 정리되었는가 |  |  |  |
| 9 | 전환 위험 요소와 상세설계 반영사항이 도출되었는가 |  |  |  |
| 10 | 추가 인터뷰 또는 자료 요청 항목이 정리되었는가 |  |  |  |

# 4. 추가 인터뷰 및 자료 요청 목록

| No | 요청 대상 | 요청 자료/질문 | 필요 사유 | 우선순위 | 요청일 | 회신일 | 상태 |
|---|---|---|---|---|---|---|---|
| 1 |  |  |  | 상/중/하 |  |  |  |
| 2 |  |  |  | 상/중/하 |  |  |  |
| 3 |  |  |  | 상/중/하 |  |  |  |

