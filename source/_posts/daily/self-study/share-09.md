---
title: "[자율 공부방] 학습(작업) 내용 공유 - 09"
toc: false
tags: [영남이공대학교, 자율 공부방]
categories:
  - Daily
  - SelfStudy
date: 2020-09-12 22:51:00
thumbnail: /images/post_include/daily_self-study/title.gif
---
> 영남이공대학교 자율 공부 모임에 공유할 목적으로 작성하는 포스트입니다.  
> 학습 내용에 대한 구체적인 사항은 별도 포스트에서 다룰 예정입니다.
> 개인적으로 학습하며 기록하고 있기 때문에 <font color='red'>잘못된 내용</font>이 있을 수 있습니다. 잘못된 내용이 있다면 댓글로 알려주세요.  

# 개요
* 날짜: 2020년 09월 12일 토요일
* 내용: JPA 학습을 하고, 웹·앱 프로젝트 개발 모임을 홍보했습니다.

# JPA
## 값 타입과 불변객체
> 값 타입은 복잡한 객체 세상을 조금이라도 단순화하려고 만든 개념이다. 따라서 값 타입은 단순하고 안전하게 다룰 수 있어야 한다.

### 값 타입 공유 참조
* 임베디드 타입 같은 값 타입을 여러 엔티티에서 공유하면 위험함.
* side effect 발생

### 값 타입 복사
* 값 타입의 실제 인스턴스인 값을 공유하는 것은 위험
* 대신 값(인스턴스)를 복사해서 사용

### 객체 타입의 한계
* 항상 값을 복사해서 사용하면 공유 참조로 인해 발생하는 부작용을 피할 수 있다.
* 문제는 임베디드 타입처럼 직접 정의한 값 타입은 자바의 기본 타입이 아니라 객체 타입이다.
* 자바 기본 타입에 값을 대입하면 값을 복사한다.
* 객체 타입은 참조 값을 직접 대입하는 것을 막을 방법이 없다.
* 객체의 공유 참조는 피할 수 없다.

### 극복 방법
> 불변이라는 작은 으로 부작용이라는 큰 재앙을 막을 수 있다.
* 객체 타입을 수정할 수 없게 만들어 부작용을 원천 차단
* 값 타입을 불변 객체(immutable object)로 설계
* 불변 객체: 생성 시점 이후 절대 값을 변경할 수 없는 객체
* 생성자로만 값을 설정하고 수정자(Setter)를 만들지 않으면 됨)
* 참고: Integer, String은 자바가 제공하는 대표적인 불변 객체

### 값 타입의 비교
* 동일성(identity) 비교: 인스턴스의 참조 값을 비교, == 사용
* 동등성(equivalence) 비교: 인스턴스의 값을 비교, equals() 사용
* 값 타입은 a.equals(b)를 사용해서 동등성 비교를 해야 함
* 값 타입의 equals() 메소드를 적절하게 재정의(주로 모든 필드 사용)

## 값 타입 컬렉션
* 값 타입을 하나 이상 저장할 때 사용
* @ElementCollection, @CollectionTable 사용
* 데이터베이스는 컬렉션을 같은 테이블에 저장할 수 없다.
* 컬렉션을 저장하기 위한 별도의 테이블이 필요함
* 참고: 값 타입 컬렉션은 영속성 전이(Cascade) + 고아 객체 제거 기능을 필수로 가진다고 볼 수 있다.

### 제약사항
* 값 타입은 엔티티와 다르게 식별자 개념이 없다.
* 값을 변경하면 추적이 어렵다.
* 값 타입 컬렉션에 변경 사항이 발생하면, 주인 엔티티와 연관딘 모든 데이터를 삭제하고, 값 타입 컬렉션에 있는 현재 값을 모두 다시 저장한다.
* 값 타입 컬렉션을 매핑하는 테이블은 모든 컬럼을 묶어서 기본키를 구성해야 함: null 입력 X, 중복 저장 X

### 대안
* 실무에서는 상황에 따라 값 타입 컬렉션 대신에 일대다 관계를 고려
* 일대다 관계를 위한 엔티티를 만들고, 여기에서 값 타입을 사용
* 영속성 전이(Cascade) + 고아 객체 제거를 사용해서 값 타입 컬렉션 처럼 사용
* EX) AddressValueType -> AddressEntity

### 언제 사용하는가?
* 구조가 정말 간단한 경우.
* 추적이 필요하지 않고, 수정하는 경우가 없을 때

## 마무리
### 엔티티 타입의 특징
* 식별자 O
* 생명 주기 관리
* 공유

### 값 타입의 특징
* 식별자 X
* 생명 주기를 엔티티에 의존
* 공유하지 않는 것이 안전(복사해서 사용)
* 불변 객체로 만드는 것이 안전

### 정리
* 값 타입은 정말 값 타입이라 판단될 때만 사용
* 엔티티와 값 타입을 혼동해서 엔티티를 값 타입으로 만들면 안됨
* 식별자가 필요하고, 지속해서 값을 추적, 변경해야 한다면 그것은 값 타입이 아닌 엔티티

## JPA의 다양한 쿼리 질의 방법
### JPQL
* JPA는 SQL을 추상화한 JPQL이라는 객체 지향 쿼리 언어 제공
* SQL과 문법 유사, SELECT, FROM, WHERE, GROUP BY, HAVING, JOIN 지원(ANSI SQL)
* JPQL은 엔티티 객체를 대상으로 쿼리
* SQL은 데이터베이스 테이블을 대상으로 쿼리
* SQL을 추상화해서 특정 데이터베이스 SQL에 의존되지 않음

### JPA Criteria
* 문자가 아닌 자바코드로 JPQL을 작성할 수 있음
* JPQL 빌더 역할
* JPA 공식 기능
* 단점: 너무 복잡하고 실용성이 없다.
* Criteria 대신 QueryDSL 사용 권장

### QueryDSL
* 문자가 아닌 자바코드로 JPQL을 작성
* JPQL 빌더 역할
* 컴파일 시점에 문법 오류를 찾을 수 있음
* 동적쿼리 작성이 편리함
* 단순하고 쉬움
* 실무 사용 권장

### 네이티브 SQL
* JPA가 제공하는 SQL을 직접 사용하는 기능
* JPQL로 해결할 수 없는 특정 데이터베이스에 의존적인 기능
    > EX) 오라클 CONNECT BY, 특정 DB만 사용하는 SQL 힌트 

### JDBC 직접 사용, SpringJdbcTemplate 등
* JPA를 사용하면서 JDBC 커넥션을 직접 사용하거나, SpringJdbcTemplate, MyBatis 등을 함께 사용 가능
* 단, 영속성 컨텍스트를 직절한 시점에 강제로 플러시 필요
    > EX) JPA를 우회해서 SQL을 실행하기 직전에 영속성 컨텍스트 수동 플러시

# 웹·앱 프로젝트 개발 모임 홍보
* 현재 인원: 8명
* 영남이공대학교 에브리타임 홍보 진행: 1명 참가 희망