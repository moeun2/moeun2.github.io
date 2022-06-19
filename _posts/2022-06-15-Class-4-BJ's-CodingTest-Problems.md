---
title: Class4_BJ's CodingTest Problems
tags: [CodingTest, BJ]
style: fill
color: info
description: I'm solving the Class4 coding problems of  "solved.ac" and summarizing.
last_modified_at: 15 June 2022
---



---

# RGB

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 1620     | class3 | silver4 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/1620)

⚡ 해쉬문제, 리스트 deep copy 로 하면 시간초과

⚡ sys.stdin.readline의 경우 '\n'까지 들어가기 때문에 rstrip을 해줘야지 isdigit()이 먹는다.

<details>
<summary>View Code...</summary>
<div markdown="1">


```python
import sys

input = sys.stdin.readline
n, m = map(int, input().split())
poketmon = {}
for i in range(n):
    temp = input().rstrip()
    poketmon[temp.upper()] = i + 1
    poketmon[i + 1] = temp

for _ in range(m):
    question = input().rstrip()
    if question.isdigit():
        print(poketmon[int(question)])
    else:
        idx = poketmon[question.upper()]
        print(idx)
```

</div>
</details>