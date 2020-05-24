---
layout: post
title:  "[Oracle] DataBase Log"
subtitle:   "DataBase Log"
categories: dev
tags: rdbms
comments: true


---

## 

## 데이터베이스 백업

#### 물리 백업

핫 백업

 - 데이터파일 복사

   파일 카피라고 봐도 무방

 - RMAN 백업

   - Incremental backup

     이전과 비교해서 변경된 사항만 백업

   - Cumulative backup

​	

콜드 백업

- 오라클 서비스를 중지 후 백업(속도는 빠름)



#### 논리백업

- 특정 테이블만 백업(물리 백업은 특정 테이블 선택 불가능)
- export/import
- datapump(10g 이상 지원)
  - 고속 백업
  - 기존 툴과 호환 불가

ex) 

``` sql
exp userid=hr/hr file='./hr.dump'
```





#### 데이터베이스 복원

1. DB 생성
2. TableSpace 생성
3. 계정 생성및 테이블 스페이스 접근 권한 추가
4. import

``` sql
imp userid=hr/hr file='./hr.dump'
```

