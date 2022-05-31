---
2title: Class3_BJ's CodingTest Problems
tags: [CodingTest, BJ]
style: fill
color: info
description: I'm solving the Class3 coding problems of  "solved.ac" and summarizing.
---

{{ page.last_modified_at | date: '%Y:%B:%A:%d:%S:%R' }}

# 제로

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 2579     | class3 | silver3 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/2579)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
n = int(input())
stairs = [ int(input()) for _ in range(n)]
dp = [0 for _ in range(n+1)]

if n == 1:
    print(stairs[0])
else:
    dp[1] = stairs[0]
    dp[2] = stairs[0]+stairs[1]

    for i in range(3, n+1):
        dp[i] = max(dp[i-3]+stairs[i-2]+stairs[i-1], dp[i-2]+stairs[i-1])

    print(dp[n])
```

</div>
</details>

---
