---
layout: single
title:  "[My SQL] 정렬과 제한"
categories : SQL
tag : [My SQL, order by, limit, offset]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---
**[공지사항]** : 데이터베이스와 관련된 사용법 등을 정리하지만, 다른 데이터베이스 사용법과 크게 다르지 않다면 따로 언급을 하고 있지 않습니다. 사용법이 보이지 않는다면 다른 데이터베이스 포스트를 확인해주세요!!
{: .notice}

order by : 출력 데이터 정렬

```sql
select 컬럼명
from 테이블명
order by 컬럼명 [asc|desc]; 
-- asc : 오름차순, 기본 값
-- desc : 내림차순

-- 중복된 값이 존재할 경우
select ol.order_date, ol.menu, ol.sales_qty
from order_list ol
order by order_date, menu, sales_qty desc;
/* order_date에서 중복된 값이 존재할 경우
   menu, sales_qty 순으로 정렬 */

||

-- 윗 코드와 같은 결과값
select ol.order_date, ol.menu, ol.sales_qty
from order_list ol
order by 1, 2, 3 desc;
-- 순서대로 1은 order_date, 2는 menu, 3은 sales_qty를 지정
```

![image-20240509233637676](/images/2024-05-09-ORDER_BY/image-20240509233637676.png)

![image-20240509233655181](/images/2024-05-09-ORDER_BY/image-20240509233655181.png)

![image-20240509233731981](/images/2024-05-09-ORDER_BY/image-20240509233731981.png)

![image-20240509233747112](/images/2024-05-09-ORDER_BY/image-20240509233747112.png)



limit : 출력 row 수 제한

```sql
select ol.order_date, ol.menu, ol.sales_qty
from order_list ol
order by order_date, menu, sales_qty desc
limit 3 ; -- 상위 3개 데이터 출력
```

![image-20240509234125881](/images/2024-05-09-ORDER_BY/image-20240509234125881.png)

![image-20240509234138471](/images/2024-05-09-ORDER_BY/image-20240509234138471.png)



offset : 상위 row를 제외하고 출력 결정, limit와 같이 쓰임

```sql
select ol.order_date, ol.menu, ol.sales_qty
from order_list ol
order by order_date, menu, sales_qty desc
limit 3
offset 2; -- 상위 2개 행을 제외한 후 출력
```

![image-20240509234534585](/images/2024-05-09-ORDER_BY/image-20240509234534585.png)

![image-20240509234549466](/images/2024-05-09-ORDER_BY/image-20240509234549466.png)

 