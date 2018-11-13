---
layout: post
title:  "자주 사용하는 git Command 정리"
date:   2019-11-13 13:39:03 +0700
categories: [python, codefights]
---

git command 리스트 / 충돌 / 병합 / 폐기 / 제거 .

**Example**

* For `n = 1010`, the output should be `numberOfEvenDigits(n) = 2`.
* For `n = 123`, the output should be `numberOfEvenDigits(n) = 1`.

**Input/Output**

* [time limit] 4000ms (py)
* [input] integer n (A positive integer).

**_Constraints:_**

* 1 ≤ n ≤ 106.

* **[output] integer**

**My Solution:**

```python
def numberOfEvenDigits(n):
    return len(filter(lambda m: m.isdigit() and int(m) % 2 == 0, str(n)))
```
