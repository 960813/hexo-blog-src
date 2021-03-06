---
title: "[자율 공부방] 학습(작업) 내용 공유 - 07"
toc: false
tags: [영남이공대학교, 자율 공부방]
categories:
  - Daily
  - SelfStudy
date: 2020-09-10 23:51:00
thumbnail: /images/post_include/daily_self-study/title.gif
---
> 영남이공대학교 자율 공부 모임에 공유할 목적으로 작성하는 포스트입니다.  
> 학습 내용에 대한 구체적인 사항은 별도 포스트에서 다룰 예정입니다.
> 개인적으로 학습하며 기록하고 있기 때문에 <font color='red'>잘못된 내용</font>이 있을 수 있습니다. 잘못된 내용이 있다면 댓글로 알려주세요.  

# 개요
* 날짜: 2020년 09월 10일 목요일
* 내용: 교과목 운영체제 강의를 듣고 관련 내용을 정리하며 학습했습니다. 그리고 영이공 LMS 서포터 업데이트를 진행했습니다. 

# 교과 학습 - 운영체제
## 운영체제의 정의
> 운영체제는 아래와 같은 서비스를 제공하는 소프트웨어이다.
* 사용자와 하드웨어 사이의 중간 매개체로 응용 프로그램의 실행을 제어
* 자원을 할당 및 관리
* 입출력 제어 및 데이터 관리

## 운영체제의 역할
* 하드웨어 및 사용자, 응용 프로그램, 시스템 프로그램 사이에서 인터페이스를 제공
* 프로세서, 메모리, 입출력장치, 통신장치 등 컴퓨터 자원을 효과적으로 활용하려고 조정/관리
* 메일 전송, 파일 시스템 검사, 서버 작업 등 높은 수준의 서비스를 처리하는 응용 프로그램을 제어
* 다양한 사용자에게 컴퓨터 시스템을 보호하려고 입출력을 제어하며 데이터를 관리

## 운영체제 발전의 목적
* 편리성: 사용자에게 편리한 환경 제공
* 효율성: 시스템 성능 향상
* 제어 서비스 향상
    * 시스템 확장, 효율적 운영을 위해 새로운 기능의 효과적인 개발을 허용하는 방법으로 발전
    * 입출력장치의 동작 관리 및 제어, 시스템 오류 예방 등으로 컴퓨터 자원을 여러 사용자에게 효율적으로 할당하고 관리할 수 있도록 제어 서비스를 발전
   
## 시스템 성능 평가 기준 
1. 처리량
2. 지연/응답 시간(Turn Around Time)
3. 신뢰도
4. 사용 가능도(가동률)

## 운영체제의 주요 기능
### 부팅 서비스
> Booting / Bootstrapping
* 컴퓨터 하드웨어 관리, 프로그램을 실행할 수 있도록 컴퓨터에 시동
* 운영체제를 메인 메모리에 적재하는 과정
    1. 컴퓨터 작동 시작, ROM에 저장된 부트 로더 실행
    2. 부트 로더는 하드디스크의 부트 섹터에 저장된 운영체제(커널)을 RAM에 적재
    3. 초기화, 특정 응용 프로그램 시작

### 사용자 인터페이스(UI) 제공
* CLI
* 메뉴 인터페이스: 메뉴 버튼으로 상호작용(아이패드, ATM 등)
* GUI

### 시스템 서비스
* 자원 할당, 계정 관리, 보호와 보안 등

### 시스템 호출(System Call)
* 실행 중인 프로그램과 운영체제 간의 인터페이스, API 라고도 함
* 사용자 프로그램은 시스템 호출을 통해 운영체제의 기능을 제공 받음

## 운영체제의 자원관리 기능
### 메모리 관리
* 메인 메모리 관리: 프로세서가 직접 주소로 지정할 수 있는 유일한 메모리
* 메모리 관리의 기능
    1. 메모리의 어느 부분을 사용하고, 누가 사용하는지 점검
    2. 메모리에 저장할 프로세스 결정
    3. 메모리를 할당하고 회수하는 방법 결정

* 보조기억장치 관리: 메인 메모리는 공간이 제한되어 데이터와 프로그램을 계속 저장할 수 없어 보조기억장치 이용
* 보조기억장치 관리의 기능
    1. 빈 여유 공간 관리
    2. 새로운 파일 작성 시 저장 장소 할당
    3. 메모리 접근 요청 스케줄링
    4. 파일 생성/삭제

### 프로세스 관리
* 프로세스와 스레드 스케줄링
* 사용자 프로세스와 시스템 프로세스 생성/제거
* 프로세스 중지, 재수행
* 프로세스 동기화 방법 제공
* 프로세스 통신 방법 제공
* 교착 상태(deadlock)을 방지하는 방법 제공

### 주변장치(입출력장치) 관리
* 운영체제는 특수 프로그램인 장치 드라이버를 사용하여 입출력장치와 상호작용
    > 장치 드라이버는 특정 하드웨어 장치와 통신할 수 있는 인터페이스를 제공하므로 특정 하드웨어에 종속
* 주변장치 (입출력장치) 관리를 위한 운영체제의 기능
    1. 임시 저장(buffer-caching) 시스템 기능 제공
    2. 일반 장치용 드라이버 인터페이스 제공
    3. 특정 장치 드라이버 제공

### 파일(데이터) 관리
* 입출력 파일의 위치, 저장, 검색 관리 의미
* 파일 관리를 위한 운영체제의 기능
    1. 파일 생성, 삭제
    2. 디렉터리 생성, 삭제
    3. 보조기억장치의 파일 mapping
    4. 안전한(비휘발성) 저장장치에 파일 저장

### 시스템 관리
...

## 운영체제의 유형
### 다중 프로그래밍 시스템(Multi Programming System)
* 프로세스가 다른 작업 수행 시 입출력 작업 불가능하여 프로세서와 메인 메모리의 활용도가 떨어지는 일괄 처리 시스템의 큰 문제를 해결
* 프로세서가 유휴 상태일 때 실행 중인 둘 이상의 작업이 프로세서를 전환(인터리빙)하여 사용할 수 있도록 동작

### 시분할 시스템(Time Sharing System)
... Something

### 다중 프로그래밍 시스템과 시분할 시스템의 특징
* 메모리에 어떤 프로그램을 적재하므로 메모리 관리 필요
* 어떤 프로그램을 먼저 실행할지 결정하는 스케줄링 개념 필요
* 다중 프로그래밍 시스템의 목표: 프로세서 사용 최대화
* 시분할 시스템의 목표: 응답시간 최소화

## 다중 처리 시스템(Multi Processing System)
* 여러 프로세서가 시스템 버스, 클록, 메모리와 주변장치 등 공유
* 빠르고 프로세서 하나가 고장 나도 다른 프로세서를 사용하여 작업 계속 => 신뢰성 높음
* 프로세서 간의 연결, 상호작용, 역할 분담 등을 고려해야 함

## 실시간 처리 시스템(real time processing system)
* 반응시간은 프로세서에 이미 고정
* 고정 시간 제약을 잘 정의하지 않으면 시스템 실패
* 무기 제어, 발전소 제어, 철도 자동 제어, 미사일 자동 조준 등이 이에 해당

## 분산 처리 시스템(distributed processing system)
* 시스템마다 독립적인 운영체제와 메모리로 운영, 필요시 통신하는 시스템
* 데이터를 여러 위치에서 처리/저장, 여러 사용자가 공유

# 영이공 LMS 서포터 업데이트
## 주요 기능
1. 학습하지 않은 강의와 과제를 한눈에 볼 수 있게 목록 제공
2. (예정) 강의 영상 다운로드 - 이미 개발은 완료했고, 수요가 있다면 추가할 계획
3. (예정) LMS 시작 시 인트로 소리 음소거 

## 작동 예시
[https://youtu.be/WT8yMJMobjo](https://youtu.be/WT8yMJMobjo)

## 설치 방법
1. 다운 로드: [Chrome 웹 스토어](http://bit.ly/ync-lms-supporter) / Chrome 웹 스토어 '영이공 LMS 서포터' 검색
2. 아이콘 확인 & 클릭
  
    ![](https://github.com/960813/ync-lms-supporter/raw/master/_data/05.png)