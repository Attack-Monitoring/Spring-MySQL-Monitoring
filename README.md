<img src="https://capsule-render.vercel.app/api?type=waving&color=41ab5d&height=300&section=header&text=Spring-MySQL-Monitoring-System&fontSize=50&fontColor=FFFFFF&animation=fadeIn&width=1200" width="1200" />

## 📚 목차

- [🎈 팀원 소개](#-팀원-소개)
- [📊 리눅스 서버 모니터링 시스템 구축 & 부하 테스트 프로젝트](#-리눅스-서버-모니터링-시스템-구축--부하-테스트-프로젝트)
  - [📝 개요](#-개요)
  - [🔧 기술 스택](#-기술-스택)
  - [🛠️ 구성 요소](#-구성-요소)
  - [🔧 설치 및 설정 과정](#-설치-및-설정-과정)
  - [🚀 부하 테스트](#-부하-테스트)
  - [📸 주요 대시보드 스크린샷 (예시)](#-주요-대시보드-스크린샷-예시)
  - [✅ 결과 및 기대 효과](#-결과-및-기대-효과)
  - [📌 기타](#-기타)



# 🎈 팀원 소개

|<img src="https://github.com/DoomchitYJ.png" width="220" />|<img src="https://github.com/wns5120.png" width="220" />|<img src="https://github.com/EOTAEGYU.png" width="220" />|<img src="https://github.com/letsgojh0810.png" width="220" />|
|:-:|:-:|:-:|:-:|
|박영진<br/>[@DoomchitYJ](https://github.com/DoomchitYJ)|유호준<br/>[@wns5120](https://github.com/wns5120)|어태규<br/>[@EOTAEGYU](https://github.com/EOTAEGYU)|한정현<br/>[@letsgojh0810](https://github.com/letsgojh0810)|

<br>

# 📊 리눅스 서버 모니터링 시스템 구축 & 부하 테스트 프로젝트


## 📝 개요

이 프로젝트는 리눅스 환경에서 Prometheus와 Grafana를 활용하여 시스템 및 데이터베이스 상태를 **실시간 모니터링**하고, Spring 애플리케이션 및 MySQL에 **부하 테스트(Stress Test)**를 수행하여 모니터링 환경의 유효성을 검증하는 데 목적이 있습니다.

<br> 

## 🔧 기술 스택 

<img src="https://img.shields.io/badge/ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"><img src="https://img.shields.io/badge/prometheus-000000?style=for-the-badge&logo=prometheus&logoColor=orange">
<img src="https://img.shields.io/badge/grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white">
<img src="https://img.shields.io/badge/node--exporter-85EA2D?style=for-the-badge">
<img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white">
<img src="https://img.shields.io/badge/springboot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white">
<img src="https://img.shields.io/badge/stress%20test-FF0000?style=for-the-badge">

<br>

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


```sql
DELIMITER $$

CREATE PROCEDURE generate_test_data()
BEGIN
  DECLARE i INT DEFAULT 1; -- 반복을 위한 변수 i 선언
  WHILE i <= 10000 DO
    INSERT INTO test_data (name, email, age, created_at)
    VALUES (
      CONCAT('user', i),                     -- 이름: user1 ~ user10000
      CONCAT('user', i, '@example.com'),    -- 이메일: user1@example.com ~ ...
      FLOOR(18 + (RAND() * 50)),            -- 나이: 18 ~ 67 사이 랜덤
      NOW()                                 -- 현재 시간 입력
    );
    SET i = i + 1; -- i 값을 1씩 증가
  END WHILE;
END$$

DELIMITER ;

```


---

## 📸 주요 대시보드 스크린샷


![image](https://github.com/user-attachments/assets/9826b614-7359-4ee6-9578-2c4b5227423a)

📊 MySQL Questions 모니터링

 이 그래프는 **MySQL Questions**(쿼리 실행 수)를 모니터링

<br>

![image](https://github.com/user-attachments/assets/12132637-8b11-4f67-ac5a-2383f0379262)

📡 MySQL 네트워크 트래픽

이 그래프는 **MySQL의 네트워크 입출력 트래픽**을 모니터링

<br>


![image](https://github.com/user-attachments/assets/70a184ba-6789-45be-8ea2-16a2c5789e7b)


🔎 MySQL Select 유형 분석

이 그래프는 **MySQL에서 실행된 SELECT 쿼리 유형**을 모니터링하는 지표입니다.

---


## ✅ 결과 및 기대 효과

- 서버 리소스 및 DB 상태를 실시간으로 시각화하여 **운영 가시성 향상**
- 부하 테스트를 통한 문제 상황 조기 파악
- 안정적인 모니터링 환경 기반의 성능 튜닝 및 대응 체계 마련

## 📌 기타

- 모니터링 환경은 Docker 없이 직접 설치 방식으로 구성됨
- Grafana 대시보드는 필요한 경우 JSON 형태로 공유 가능

