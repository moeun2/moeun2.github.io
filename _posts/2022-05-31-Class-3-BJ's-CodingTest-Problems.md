---
title: Class3_BJ's CodingTest Problems
tags: [CodingTest, BJ]
style: fill
color: info
description: I'm solving the Class3 coding problems of  "solved.ac" and summarizing.
last_modified_at: 19 June 2022
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

---

# 2×n 타일링

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 11726    | class3 | silver3 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/1074)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
n = int(input())
dp = [0 for _ in range(n+1)]
dp[0] = 1
dp[1] = 1
for i in range(2,n+1):
    dp[i] = dp[i-1]+dp[i-2]
print(dp[-1] % 10007)
```

</div>
</details>

---

# 나는야 포켓몬 마스터 이다솜

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

---

# 집합

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 11723    | class3 | silver5 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/11723)

<details>
<summary>View Code...</summary>
<div markdown="1">



```python
import sys

input = sys.stdin.readline
m = int(input().rstrip())
all = [str(x) for x in range(1,21)]
s = set()
for _ in range(m):
    op = input().split()

    if op[0] == 'add':
        s.add(op[1])
    elif op[0] == 'remove':
        s.discard(op[1])
    elif op[0] == "check":
        if op[1] in s:
            print(1)
        else:
            print(0)
    elif op[0] == 'toggle':
        if op[1] in s:
            s.discard(op[1])
        else:
            s.add(op[1])
    elif op[0] == 'all':
        s.clear()
        s = set(all)
    elif op[0] == 'empty':
        s.clear()

```

</div>
</details>

---

# 파도반 수열

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 9461     | class3 | silver3 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/9461)

⚡ DP, 규칙만 알면 풀 수 있언던 문제

<details>
<summary>View Code...</summary>
<div markdown="1">


```python
import sys

input = sys.stdin.readline
t = int(input().rstrip())
p = [0] * 100
p[0] = 1
p[1] = 1
p[2] = 1
start = 3
for _ in range(t):
    n = int(input().rstrip())
    for i in range(start, n):
        p[i] = p[i-2] + p[i-3]
    print(p[n-1])

```

</div>
</details>

---

# 2×n 타일링 2

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 11727    | class3 | silver3 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/11727)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
import sys

input = sys.stdin.readline
n = int(input())
dp = [0 for _ in range(n+1)]
dp[0] = 1
dp[1] = 1
for i in range(2,n+1):
    dp[i] = dp[i-1]+dp[i-2]*2
print(dp[-1] % 10007)
```

</div>
</details>

---

# 잃어버린 괄호

| 문제번호 | class  | level   | language |
| -------- | :----: | ------- | -------- |
| 1541     | class3 | silver3 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/1541)

⚡ 쉽게 생각했다고 생각했는데 너무 어렵게 접근했던 문제. 

<details>
<summary>View My Code...</summary>
<div markdown="1">
```python
import sys
import re
input = sys.stdin.readline
operations = input().rstrip()
operations = re.split('([+|-])', operations)

stack = []
isMinus = False
for op in operations[:-1]:
    if op == '-':
        if not isMinus:
            stack.append("-(")
            isMinus = True
        else:
            stack.append(")-(")
        continue
    if op == '+':
        stack.append(op)
    else:
        stack.append(str(int(op)))
if isMinus:
    stack.append(str(int(operations[-1]))+")")
else:
    stack.append(str(int(operations[-1])))

print(eval(''.join(stack)))
```

</div>
</details>

<details>
<summary>View Other Code...</summary>
<div markdown="1">


```python
input = sys.stdin.readline
arr = input().split('-')
s = 0

for i in arr[0].split('+'):
    s += int(i)
for i in arr[1:]:
    for j in i.split('+'):
        s -= int(j)

print(s)
```

</div>
</details>