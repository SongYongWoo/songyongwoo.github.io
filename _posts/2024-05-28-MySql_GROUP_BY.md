---
layout: single
title:  "[My SQL] Group by와 집계함수"
categories : SQL
tag : [My SQL, Group by, '집계함수']
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---
**[공지사항]** : 데이터베이스와 관련된 사용법 등을 정리하지만, 다른 데이터베이스 사용법과 크게 다르지 않다면 따로 언급을 하고 있지 않습니다. 사용법이 보이지 않는다면 다른 데이터베이스 포스트를 확인해주세요!!
{: .notice}

### 집계함수

| 집계함수      | 기능               |
| ------------- | ------------------ |
| SUM(컬럼명)   | 컬럼의 총합을 반환 |
| AVG(컬럼명)   | 컬럼의 평균을 반환 |
| MAX(컬럼명)   | 컬럼의 최댓값 반환 |
| MIN(컬럼명)   | 컬럼의 최솟값 반환 |
| COUNT(컬럼명) | 컬럼의 수 반환     |

※ null은 집계함수 사용시, 무시하고 함수 사용

### GROUP BY

특정 컬럼으로 그룹핑. 이를 이용하여 특정 그룹별 집계함수 사용이 가능함.

```sql
select menu,
	sum(sales_qty) as '판매수량',
	avg(sales_qty) as '평균 판매 수량',
	max(sales_qty) as '최대 판매량',
	min(sales_qty) as '최소 판매량',
	count(sales_qty) as '판매횟수'
from order_list
group by menu             -- 메뉴 별로 그룹핑
order by 2 desc;          -- 판매 수량 내림차순으로 정렬
```

![image-20240528165057557](/images/2024-05-28-GROUPBY/image-20240528165057557.png)

```sql
-- 두 컬럼을 동시에 그룹핑
select menu,order_date,
	sum(sales_qty) as '판매수량'
from order_list ol
group by menu, order_date      -- 메뉴와 주문 날짜별로 그룹핑
order by menu, order_date asc;
```

![image-20240528165203437](/images/2024-05-28-GROUPBY/image-20240528165203437.png)

```sql
-- 집계함수를 조건으로 사용하기
-- 판매량의 합이 3 이상인 날짜별 메뉴만 출력
-- 잘못된 경우
select menu,order_date,
	sum(sales_qty) as '판매수량'
from order_list ol
where sum(sales_qty) >= 3     -- where절에는 집계함수 사용 불가
group by menu, order_date 
order by menu, order_date asc;
↓
-- 수정
select menu,order_date,
	sum(sales_qty) as '판매수량'
from order_list ol
group by menu, order_date 
having sum(sales_qty) >= 3   -- having절 사용
order by menu, order_date asc;

/*
sql문 작동순서
from-> where-> group by-> having-> select-> order by
where절은 group by 이전에 작동되므로, 
group by에서 그룹핑한 집계함수를 인지하지 못함.
*/
```
