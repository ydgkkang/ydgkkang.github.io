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

*		SELECT @rn:=@rn+1 AS RANK
                  ,t1.SEARCH_WORD
        FROM
        (SELECT
                X.RANK ,
                X.SEARCH_WORD
        FROM DUMMY X
        WHERE 1=1
        GROUP BY X.SEARCH_WORD
        LIMIT 0, 10) t1, (SELECT @rn:=0) t2;

**Input/Output**

* [time limit] 4000ms (py)
* [input] integer mo (A non-negative integer).
* **Constraints:** `0 ≤ mo ≤ 15`.
* **[output] string**

A `3`-letter abbreviation of month number `mo` or `"invalid month"` if the month doesn't exist.

Here are abbreviations of all months:

**My Solution:**

```python
def getMonthName(mo):
    months = {
        1: "Jan", 2: "Feb", 3: "Mar", 4:"Apr", 
        5: "May", 6: "Jun", 7: "Jul", 8:"Aug", 
        9: "Sep", 10: "Oct", 11: "Nov", 12: "Dec"
    }
    if mo in months.keys():
        return months.get(mo)
    return "invalid month"
```

**Result Tests**:

```python
>>> getMonthName(1)
"Jan"
>>> getMonthName(0)
"invalid month"
>>>
```
