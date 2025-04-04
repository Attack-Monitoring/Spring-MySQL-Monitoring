<img src="https://capsule-render.vercel.app/api?type=waving&color=41ab5d&height=300&section=header&text=Spring-MySQL-Monitoring-System&fontSize=50&fontColor=FFFFFF&animation=fadeIn&width=1200" width="1200" />


# 🚩 프로젝트 개요


<br>
<br>

|<img src="https://github.com/DoomchitYJ.png" width="220" />|<img src="https://github.com/wns5120.png" width="220" />|<img src="https://github.com/EOTAEGYU.png" width="220" />|<img src="https://github.com/letsgojh0810.png" width="220" />|
|:-:|:-:|:-:|:-:|
|박영진<br/>[@DoomchitYJ](https://github.com/DoomchitYJ)|유호준<br/>[@wns5120](https://github.com/wns5120)|어태규<br/>[@EOTAEGYU](https://github.com/EOTAEGYU)|한정현<br/>[@letsgojh0810](https://github.com/letsgojh0810)|

<br>

# 📊 리눅스 서버 모니터링 시스템 구축 & 부하 테스트 프로젝트

## 📝 개요

이 프로젝트는 리눅스 환경에서 Prometheus와 Grafana를 활용하여 시스템 및 데이터베이스 상태를 **실시간 모니터링**하고, Spring 애플리케이션 및 MySQL에 **부하 테스트(Stress Test)**를 수행하여 모니터링 환경의 유효성을 검증하는 데 목적이 있습니다.

---

## 🛠️ 구성 요소

| 구성 요소         | 설명                                                                 |
|------------------|----------------------------------------------------------------------|
| 🐧 Linux Server   | 모니터링 대상 서버                                                   |
| 📦 Prometheus    | 시계열 데이터 수집 도구                                               |
| 📈 Grafana       | 시각화 대시보드 도구                                                  |
| 🧩 Node Exporter | CPU, 메모리, 디스크 등 서버 리소스 지표 수집                          |
| 🐬 MySQL Exporter| MySQL 데이터베이스 모니터링 지표 수집                                  |
| 🌱 Spring App    | 테스트 대상 애플리케이션                                               |

---

## 🔧 설치 및 설정 과정

### 1. Prometheus 설치 및 설정
- Prometheus 설치
- `prometheus.yml` 파일 설정 (Node Exporter, MySQL Exporter 타겟 추가)

### 2. Grafana 설치 및 대시보드 구성
- Grafana 설치 및 실행
- Prometheus 데이터 소스로 등록
- 시스템 및 MySQL 모니터링 대시보드 구성

### 3. Exporter 설치
- **Node Exporter**: 서버의 리소스 상태 수집
- **MySQL Exporter**: MySQL 상태 및 성능 데이터 수집

---

## 🚀 부하 테스트

### 🌐 Spring 애플리케이션 부하 테스트
- Spring Boot 애플리케이션 서버에 배포
- `Apache Benchmark (ab)` 또는 `JMeter` 등 부하 도구 사용
- 부하 발생 중 Grafana로 실시간 리소스 변화 확인

### 🐬 MySQL 부하 테스트
- 대량의 INSERT/SELECT 쿼리를 반복 실행
- 쿼리 처리량, 연결 수, InnoDB 상태 등 모니터링

---

## 📸 주요 대시보드 스크린샷 (예시)

> 필요 시 여기에 Grafana 대시보드의 캡처 이미지를 추가하세요.

---


## ✅ 결과 및 기대 효과

- 서버 리소스 및 DB 상태를 실시간으로 시각화하여 **운영 가시성 향상**
- 부하 테스트를 통한 문제 상황 조기 파악
- 안정적인 모니터링 환경 기반의 성능 튜닝 및 대응 체계 마련

## 📌 기타

- 모니터링 환경은 Docker 없이 직접 설치 방식으로 구성됨
- Grafana 대시보드는 필요한 경우 JSON 형태로 공유 가능

