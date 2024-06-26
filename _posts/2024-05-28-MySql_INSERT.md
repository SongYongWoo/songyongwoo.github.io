---
layout: single
title:  "[My SQL] Insert, Update, Delete"
categories : SQL
tag : [My SQL, Insert, Update, Delete]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가 
---
**[공지사항]** : 데이터베이스와 관련된 사용법 등을 정리하지만, 다른 데이터베이스 사용법과 크게 다르지 않다면 따로 언급을 하고 있지 않습니다. 사용법이 보이지 않는다면 다른 데이터베이스 포스트를 확인해주세요!!
{: .notice}

### INSERT

INSERT : 테이블에 데이터 삽입

```sql
insert into 테이블(컬럼1, 컬럼2, 컬럼3) value (값1, 값2, 값3)

-- 모든 컬럼에 값을 넣는 경우
insert into 테이블 value (값1, 값2, 값3) 

insert into topic (title, description, created, author, profile) 
	values('MySQL', 'MySql is ...', now(), 'Song', 'developer');
```

![image-20240528215134483](/images/2024-05-28-INSERT/image-20240528215134483.png)



### UPDATE

UPDATE : 테이블 값 수정

```sql
update 테이블명 set 컬럼 = 속성 값 (where 조건식);
-- WHERE이 없을 경우 지정한 컬럼의 모든 값이 변경

update topic
set author = 'egoing'  -- author 값을 egoing로 수정
where id = 1;          -- id 값이 1인 경우만
```

![image-20240528221219828](/images/2024-05-28-INSERT/image-20240528221219828.png)



### DELETE

DELETE : 데이터 삭제

```sql
delete from 테이블명 (where 조건식);
-- where이 없을 경우 테이블 내 모든 데이터 삭제

delete from topic where id = 5;
```

![image-20240529103629761](/images/2024-05-28-INSERT/image-20240529103629761.png)



