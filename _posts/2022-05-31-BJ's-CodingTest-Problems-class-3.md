---
title: Class3_BJ's CodingTest Problems
tags: [CodingTest, BJ]
style: fill
color: info
description: I'm solving the Class3 coding problems of  "solved.ac" and summarizing.
last_modified_at: 10 June 2022
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

<details>
<summary>참고하면 좋을 코드</summary>
<div markdown="1">

```python
# @musemagic
import sys
input= sys.stdin.readline

def find_parent(parent, x):
if parent[x] != x:
parent[x] = find_parent(parent, parent[x])
return parent[x]

def union_parent(parent, a, b):
a = find_parent(parent, a)
b = find_parent(parent, b)
if a < b:
parent[b] = a
else:
parent[a] = b

v, e = map(int, input().split())
parent = [0] \* (v+1)

for i in range(1, v+1):
parent[i] = i

for i in range(e):
a, b = map(int, input().split())
union_parent(parent, a, b)

ans = set()
for i in range(1, v+1):
ans.add(find_parent(parent, i))

print(len(ans))

````


</div>
</details>


---

# 최소힙

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 1927    | class3 | silver2 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/1927)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
import heapq
import sys

input = sys.stdin.readline
n = int(input())
hq = []
for _ in range(n):
    temp = int(input())
    if temp == 0:
        if hq:
            print(heapq.heappop(hq))
        else:
            print(0)
    else:
        heapq.heappush(hq, temp)
````

</div>
</details>

---

# 최대힙

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 11279    | class3 | silver2 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/11279)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
import heapq
import sys

input = sys.stdin.readline
n = int(input())
hq = []
for _ in range(n):
    temp = int(input())
    if temp == 0:
        if hq:
            print(heapq.heappop(hq)[1])
        else:
            print(0)
    else:
        heapq.heappush(hq, (-temp,temp))


```

</div>
</details>

---

# 듣보잡

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 1764     | class3 | silver4 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/1764)

<details>
<summary>View Code...</summary>
<div markdown="1">


```python
import sys

input = sys.stdin.readline

n, m = map(int, input().split())
n_people = [input().strip() for _ in range(n)]
m_people = [input().strip() for _ in range(m)]
nm_people = list(set(n_people) & set(m_people))
nm_people.sort()
print(len(nm_people))
for i in nm_people:
    print(i)

```

</div>
</details>

---

# Z

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 1074     | class3 | silver1 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/1074)

<details>
<summary>View Code...</summary>
<div markdown="1">



```python
import sys

input = sys.stdin.readline

n, m = map(int, input().split())
n_people = [input().strip() for _ in range(n)]
m_people = [input().strip() for _ in range(m)]
nm_people = list(set(n_people) & set(m_people))
nm_people.sort()
print(len(nm_people))
for i in nm_people:
    print(i)

```

</div>
</details>



---

# 색종이 만들기

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 2630     | class3 | silver2 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/1074)

<details>
<summary>View Code...</summary>
<div markdown="1">




```python
import sys

N = int(sys.stdin.readline())
paper = [list(map(int, sys.stdin.readline().split())) for _ in range(N)] 

result = []

def solution(x, y, N) :
  color = paper[x][y]
  for i in range(x, x+N) :
    for j in range(y, y+N) :
      if color != paper[i][j] :
        solution(x, y, N//2)
        solution(x, y+N//2, N//2)
        solution(x+N//2, y, N//2)
        solution(x+N//2, y+N//2, N//2)
        return
  if color == 0 :
    result.append(0)
  else :
    result.append(1)


solution(0,0,N)
print(result.count(0))
print(result.count(1))
```

</div>
</details>