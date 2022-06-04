---
title: Class3_BJ's CodingTest Problems
tags: [CodingTest, BJ]
style: fill
color: info
description: I'm solving the Class3 coding problems of  "solved.ac" and summarizing.
last_modified_at: 04 June 2022
---

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

# 동전 0

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 11047    | class3 | silver3 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/11047)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
n, k = map(int, input().split())
coins = [int(input()) for _ in range(n)]
coins = sorted(list(filter(lambda x: x <= k, coins)), reverse=True)
answer = 0

for i in coins:
    answer += k // i
    k %= i

print(answer)
```

</div>
</details>

---

# 연결 요소의 개수

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 11724    | class3 | silver2 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/11724)

<details>
<summary>알아야 할 것</summary>
<div markdown="1">
1. 방향 없는 그래프

양방향 그래프라는 말이다.

u -> v / v->u

2. 간선 정보가 없는 노드도 연결 요소로 포함한다.

   ```
   # example
   6 2
   3 4
   4 2
   # answer : 4
   # why : 2-3-4 는 연결된 상태이므로 1개 + 1,5,6 도 단일노드로 존재하므로 답은 1개가 아니라 4개이다.
   ```

   2번째 조건을 몰라서 계속 틀렸다...

</div>
</details>

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
import sys

input = sys.stdin.readline
n, m = map(int, input().split())
dict = {}
for _ in range(m):
    temp = list(map(int, input().split()))
    dict[temp[0]] = dict.get(temp[0], []) + [temp[1]]
    dict[temp[1]] = dict.get(temp[1], []) + [temp[0]]
visited = [False for _ in range(n + 1)]
answer = 0
for i in dict:
    if not visited[i]:
        queue = dict.get(i)
        visited[i] = True
        while queue:
            node = queue.pop()

            if not visited[node]:
                visited[node] = True
                queue += dict.get(node)
        answer += 1
for i in range(1, n + 1):
    if not visited[i]:
        answer += 1
print(answer)

```

</div>
</details>

<details>
<summary>반례</summary>
<div markdown="1">
 
```python
4 2
1 4
4 1
# answer : 3
```
```python
6 2
1 3
2 3
# answer : 4
```

</div>
</details>
