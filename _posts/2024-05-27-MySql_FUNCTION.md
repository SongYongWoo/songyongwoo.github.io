---
layout: single
title:  "[My SQL] 함수"
categories : SQL
tag : [My SQL, function]
typora-root-url: ../
toc: true                     # 글 목차
author_profile : false        # 게시물에서 작성자 정보 노출 유무
sidebar :                     # 작성자 정보 노출 안 할시 사이드바 설정
    nav : "docs"
search : true  # false 지정시 해당 게시물 검색 불가
---
**[공지사항]** : 데이터베이스와 관련된 사용법 등을 정리하지만, 다른 데이터베이스 사용법과 크게 다르지 않다면 따로 언급을 하고 있지 않습니다. 사용법이 보이지 않는다면 다른 데이터베이스 포스트를 확인해주세요!!
{: .notice}

함수 : 특정 값을 넣을 경우 특정 값을 반환



### 숫자 함수

| 함수                       | 기능                                                         | 예시                                            | 결과                  |
| :------------------------- | :----------------------------------------------------------- | :---------------------------------------------- | :-------------------- |
| ROUND<br />(값, 자리수)    | 특정 자리에서 값을 반올림<br />자리수가 양수면 해당 자리수에서 까지 출력, 음수면 해당 자리 수에서 반올림<br />(-1은 1의 자리, -2는 10의 자리,,,) | ROUND(123.456, 2)<br />ROUND(123.456, -2)       | 123.46<br />100       |
| TRUNCATE<br />(값, 자리수) | 특정 자리에서 값을 버림                                      | TRUNCATE(123.456, 2)<br />TRUNCATE(123.456, -2) | 123.45<br /><br />100 |
| SIGN(값)                   | 값이 양수면 1, 음수면 -1, 0이면 0 반환                       | SIGN(-5)                                        | -1                    |
| FLOOR(값)                  | 작거나 같은 최대 정수 반환                                   | FLOOR(4.5)                                      | 4                     |
| CEIL(값)                   | 크거나 같은 최소 정수 반환                                   | CEIL(4.5)                                       | 5                     |
| MOD<br />(값1, 값2)        | 값1을 값2로 나누어 나머지 반환                               | MOD(9, 2)                                       | 1                     |
| POWER<br />(값1, 값2)      | 값1의 값2 거듭제곱                                           | POWER(4, 2)                                     | 16                    |
| SQRT(값)                   | 루트값 반환                                                  | SQRT(16)                                        | 4                     |
| ABS(값)                    | 절대값 반환                                                  | ABS(-2.6)                                       | 2.6                   |



### 문자 함수

| 함수                               | 기능                                                         | 예시                                                         | 결과                                                         |
| :--------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| CONCAT<br />(문자1, 문자2, .....)  | 문자 결합                                                    | CONCAT('a', 'b', 'c')                                        | abc                                                          |
| LOWER(문자)                        | 문자를 소문자로                                              | LOWER('ABC')                                                 | abc                                                          |
| UPPER(문자)                        | 문자를 대문자로                                              | UPPER('abc')                                                 | ABC                                                          |
| SUBSTR<br />(문자, m, n)           | 문자 중 m위치에서 n개의 문자 추출                            | SUBSTR('abcdefg', 2, 3)<br />SUBSTR('abcdefg', 2)<br />SUBSTR('abcdefg', -3, 3) | bcd<br />bcdefg<br />efg                                     |
| INSTR<br />(문자1, 문자2)          | 문자1에서 문자2의 위치 반환                                  | INSTR('abcdefg', 'c')                                        | 3                                                            |
| LTRIM(문자)                        | 왼쪽 공백 삭제                                               | LTRIM('  abcd')                                              | 'abcd'                                                       |
| RTRIM(문자)                        | 오른쪽 공백 삭제                                             | RTRIM('abcd   ')                                             | 'abcd'                                                       |
| TRIM(문자)                         | 왼쪽 혹은 오른쪽에 존재하는 공백, 특정 문자 제거<br />BOTH : 양쪽 삭제<br />LEADING : 왼쪽 삭제<br />TRAILING : 오른쪽 삭제 | 1. <br />TRIM('&nbsp;&nbsp;&nbsp;aabbaaccaa&nbsp;&nbsp;&nbsp;')<br />2.<br />TRIM(BOTH FROM <br />'&nbsp;&nbsp;&nbsp;aabbaaccaa&nbsp;&nbsp;&nbsp;')<br />3.<br />TRIM(BOTH 'a' FROM 'aabbaaccaa')<br />4.<br />TRIM(LEADING FROM<br /> '&nbsp;&nbsp;&nbsp;aabbaaccaa&nbsp;&nbsp;&nbsp;')<br />5.<br />TRIM(LEADING 'a' FROM 'aabbaaccaa')<br />6.<br />TRIM(TRAILING FROM<br />'&nbsp;&nbsp;&nbsp;aabbaaccaa&nbsp;&nbsp;&nbsp;')<br />7.<br />TRIM(TRAILING 'a' FROM 'aabbaaccaa') | 1.<br />'aabbaaccaa'<br /><br />2. <br />'aabbaaccaa'<br /><br />3. <br />'bbaacc'<br /><br />4.<br />'aabbaaccaa&nbsp;&nbsp;&nbsp;'<br /><br />5.<br />'bbaaccaa'<br /><br />6.<br />'&nbsp;&nbsp;&nbsp;aabbaaccaa'<br /><br />7.<br />'aabbaacc'&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |
| LPAD<br />(문자1, n, 문자2)        | 문자1이 n 자리수가 될때까지 왼쪽에 문자2 추가                | LPAD('abc', 5, '*')                                          | **abc                                                        |
| RPAD<br />(문자1, n, 문자2)        | 문자1이 n 자리수가 될때까지 오른쪽에 문자2 추가              | RPAD('abc', 5, '*')                                          | abc**                                                        |
| LENGTH(문자)                       | 문자 길이 반환                                               | LENGTH('abc')                                                | 3                                                            |
| REPLACE<br />(문자1, 문자2, 문자3) | 문자 1에서 문자 2를 찾아 문자 3으로 치환<br />문자3 생략 시 문자 2 삭제 | REPLACE('abba', 'ab', 'cd')                                  | cdba                                                         |

※ TRANSLATE : 오라클에서 문자를 바꿀 때 1대1 대응으로 바꾸게 하는 함수.

```sql
SELECT TRANSLATE('abba', 'ab', 'cd'); 
-- cddc(ab가 cd 가 아닌 a는 c, b는 d로 치환)
```

mysql에는 해당 함수가 없기에 대신 REPLACE를 반복함으로 대체 가능

```sql
SELECT REPLACE(REPLACE('abba', 'a', 'c'), 'b', 'd')
-- cddc
```



### 날짜 함수

| 함수                                                         | 기능                                                         | 예시                                          | 결과                |
| ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------------------- | ------------------- |
| NOW()                                                        | 현재 날짜와 시간을 출력                                      | NOW()                                         | 2024-05-28 10:43:30 |
| CURRENT_<br />TIMESTAMP()                                    | 현재 날짜와 시간을 출력                                      | CURRENT_TIMESTAMP()                           | 2024-05-28 10:43:30 |
| CURRENT_DATE()                                               | 현재 날짜 출력                                               | CURRENT_DATE()                                | 2024-05-28          |
| DATE_ADD<br />(날짜, interval 숫자 <br />(second\|minute\|hour\|<br />day\|month\|year)) | 날짜에 특정 숫자만큼 초, 분, 시간, 일, 월 ,년을 더함<br />숫자가 음수일 경우 뺌 | DATE_ADD<br />(NOW(), interval 3 year)        | 2027-05-28 10:43:30 |
| DATE_SUB<br />(날짜, interval 숫자 <br />(second\|minute\|hour\|<br />day\|month\|year)) | 날짜에 특정 숫자만큼 초, 분, 시간, 일, 월 ,년을 뺌<br />숫자가 음수일 경우 더함 | DATE_SUB<br />(NOW(), interval 3 year)        | 2021-05-28 10:43:30 |
| DATE_FORMAT<br />(날짜, 날짜 포멧)                           | 날짜의 형식을 지정한 포멧으로 변경                           | DATE_FORMAT<br />(CURRENT_DATE(), '%Y/%m/%d') | 2024/05/28          |
| STR_TO_DATE<br />(문자, 날짜 포멧)                           | 문자로 표시된 날짜를 날짜 데이터로 변경<br />문자로 표시된 날짜와 날짜 포멧은 동일해야함. | STR_TO_DATE<br />('20200528','%Y%m%d')        | 20200528            |
| DATEDIFF<br />(날짜1, 날짜2)                                 | 두 날짜 차이의 일 수를 계산<br />날짜1- 날짜2                | DATEDIFF<br />(CURRENT_DATE(),order_date)     | 3                   |

※ 날짜 포멧
포멧은 '&nbsp;&nbsp;&nbsp;&nbsp;'안에 입력 되어야 하며 대소문자를 구분.

| 포멧 | 설명            | 포멧 | 설명                   |
| ---- | --------------- | ---- | ---------------------- |
| %Y   | 네 자리수 연도  | %y   | 년도 뒤 두 자리만 표시 |
| %M   | 월을 영어 표시  | %m   | 두 자리수 월           |
| %D   | 일 뒤에 th 표시 | %d   | 두 자리수 일           |



### 논리 관련 함수

IFNULL(값1, 값2) : 값1이 NULL이면 값2 반환

```sql
select ifnull(null, 'null 입니다.') as '함수확인';
```

![image-20240528155921070](/images/2024-05-27-FUNCTION/image-20240528155921070.png)



case문

```sql
-- case문을 활용한 가격에 따른 등급 구분
select distinct menu, price,
		(case when price <= 3000 then '저가'                 
			when price >3000 and price <5000 then '중가'    
			else '고가' end) as price_grade
from order_list;
```

![image-20240528160123088](/images/2024-05-27-FUNCTION/image-20240528160123088.png)
