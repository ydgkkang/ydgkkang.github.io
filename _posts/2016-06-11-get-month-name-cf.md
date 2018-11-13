---
layout: post
title:  "MYSQL GROUP BY ROWNUM (행번호 지정)"
date:   2018-11-13 09:43:45 +0700
categories: [mysql, RDBMS]
---

Mysql Rownum 카운팅주기.  
일반적으로 group by 가 없는 SQL에서 @rownum:=@rownum+1 하면 되지만,
그룹별 카운팅시 엉뚱한 숫자가 출력되는 경우가 발생



**Example:**

```		
SELECT @rn:=@rn+1 AS RANK
          ,t1.SEARCH_WORD
FROM
(SELECT
        X.RANK ,
        X.SEARCH_WORD
FROM DUMMY X
WHERE 1=1
GROUP BY X.SEARCH_WORD
LIMIT 0, 10) t1, (SELECT @rn:=0) t2;  
```
