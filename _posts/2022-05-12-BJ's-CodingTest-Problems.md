---
title: BJ's CodingTest Problems
tags: [CodingTest, BJ]
style: fill
color: info
description: ⏰ last update 2022/05/24 <br/> I'm solving the 2+ coding problems of  "solved.ac" and summarizing. 
---

{% capture list_items %}
제로
균형잡힌 세상
이항 계수 1
최대공약수와 최소공배수
요세푸스 문제 0
스택
프린터 큐
괄호
부녀회장이 될테야
덱
달팽이는 올라가고 싶다
덩치
{% endcapture %}
{% include elements/list.html title="Table of Contents" type="toc" %}


# 제로


| 문제번호  | class  | level   | language |
| ----- | :----: | ------- | -------- |
| 10773 | class2 | silver4 | python   |

⚡[문제링크](https://www.acmicpc.net/problem/10773)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
k = int(input())
numbers = []
for i in range(k):
    number = int(input())
    if number != 0:
        numbers.append(number)
    else:
        numbers.pop(-1)
    print(numbers)
answer = sum(numbers)
print(answer)
```
</div>
</details>

---

# 균형잡힌 세상

| 문제번호 | class | level|language|
|--- | :---: | :--- :| --- :|
|4949 | class2 | silver4 | python

⚡[문제링크](https://www.acmicpc.net/problem/4949)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
while True :
    a = input()
    stack = []

    if a == "." :
        break

    for i in a :
        if i == '[' or i == '(' :
            stack.append(i)
        elif i == ']' :
            if len(stack) != 0 and stack[-1] == '[' :
                stack.pop() # 맞으면 지워서 stack을 비워줌 0 = yes
            else : 
                stack.append(']')
                break
        elif i == ')' :
            if len(stack) != 0 and stack[-1] == '(' :
                stack.pop()
            else :
                stack.append(')')
                break
    if len(stack) == 0 :
        print('yes')
    else :
        print('no')
```

</div>

</details>

# 이항 계수 1


| 문제번호 | class | level|language|
|--- | :---: | :--- :| --- :|
|11050 | class2 | bronze1 | python



⚡[문제링크](https://www.acmicpc.net/problem/11050)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
import math
n,k = map(int, input().split())
if(k < 0):
    print(0)
elif k <= n:
    print(int(math.factorial(n) / (math.factorial(k) * math.factorial(n-k))))
else:
    print(0)
```

</div>
</details>

---

# 최대공약수와 최소공배수

| 문제번호 | class | level|language|
|--- | :---: | :--- :| --- :|
|2609 | class2 | silver5 | python

⚡[문제링크](https://www.acmicpc.net/problem/2609)

⚡[유클리드 알고리즘](https://moeun2.github.io/blog/Algorithm#:~:text=유클리드-알고리즘(Euclidean-Algorithm))

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
def gcd(a, b):
    if b == 0:
        return a
    else:
        return gcd(b, a % b)


def lcd(a, b):
    return (a * b) / gcd(a, b)


a, b = map(int, input().split())
print(int(gcd(a, b)))
print(int(lcd(a, b)))

```

</div>
</details>

---

# 요세푸스 문제 0

| 문제번호 | class | level|language|
|--- | :---: | :--- :| --- :|
|11866 | class2 | silver4 | python



⚡[문제링크](https://www.acmicpc.net/problem/11866)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
n, k = map(int, input().split())
list = [x for x in range(1,n+1)]
idx = k-1
answer =[]
while list:
    idx = idx % len(list)
    answer.append(str(list.pop(idx)))
    idx += (k-1)

print('<'+', '.join(answer)+'>')
```

</div>
</details>

---

# 스택

| 문제번호 | class | level|language|
|--- | :---: | :--- :| --- :|
|10828 | class2 | silver4 | python

⚡[문제링크](https://www.acmicpc.net/problem/10828)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
import sys
input = sys.stdin.readline
n = int(input())
list = []
for i in range(n):
    command = input().rstrip()
    num = 0
    if(len(command) > 5):
        a,b = command.split(" ")
        command = a
        num = b

    if command == 'push':
        list.append(num)
    elif command == 'pop':
        if list:
            print(list.pop())
        else:
            print(-1)
    elif command == "size":
        print(len(list))
    elif command == "empty":
        if list:
            print(0)
        else:
            print(1)
    elif command == "top":
        if list:
            print(list[-1])
        else:
            print(-1)
```

</div>
</details>

---

# 프린터 큐


| 문제번호 | class | level|language|
|--- | :---: | :--- :| --- :|
|1966 | class2 | silver3 | python



⚡[문제링크](https://www.acmicpc.net/problem/1966)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
t = int(input())  # 테스트케이스 수
for i in range(t):
    n, m = map(int, input().split())  # 문서의 개수 / 몇 번째로 인쇄되었는지 궁금한 문서
    documents = []
    num = list(map(int, input().split()))

    for j in enumerate(num):
        documents.append(j)

    order = 0
    while documents:
        maxTemp = max(documents, key=lambda x: x[1])

        if maxTemp[1] > documents[0][1]:
            documents.append(documents.pop(0))
        elif maxTemp[0] == documents[0][0]:
            temp = documents.pop(0)
            order += 1
            if temp[0] == m:
                break

    print(order)
```

</div>
</details>

---

# 괄호


| 문제번호 | class | level|language|
|--- | :---: | :--- :| --- :|
|9012 | class2 | silver4 | python

⚡[문제링크](https://www.acmicpc.net/problem/9012)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
### 내가 푼 방식
test = int(input())
for te in range(test):
    ps = input()
    stack = []
    for i in ps:
        # print(stack)
        if i == '(':
            stack.append(i)
        else:
            if stack:
                t = stack.pop()
                if t == '(' :
                    continue
                else:
                    stack.append(i)
            else:
                stack.append(i)
                break

    if not stack:
        print("YES")
    else:
        print("NO")

### 이런 방식도 있드라...! 이게 효율성이 더 높다
from sys import stdin

n = int(input())
for _ in range(n):
    str_ = stdin.readline().strip()
    stack = 0
    for chr_ in str_:
        if chr_ == '(':
            stack += 1
        else:
            stack -= 1
            if stack < 0:
                break
    if stack == 0:
        print('YES')
    else:
        print('NO')
```

</div>
</details>



# 부녀회장이 될테야

| 문제번호 | class | level|language|
|--- | :---: | :--- :| --- :|
|2775 | class2 | Bronze1 | python

⚡[문제링크](https://www.acmicpc.net/problem/2775)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
Test = int(input())
for test in range(Test):
    k = int(input())
    n = int(input())
    list_zero = [x for x in range(1, 15)]
    for i in range(k):
        list_k = [sum(list_zero[:x]) for x in range(1, 15)]
        list_zero = list_k
    print(list_k[n-1])
    # print(list_k)
```

</div>
</details>

# 덱

| 문제번호  | class  |  level  | language |   solved   |
| :---: | :----: | :-----: | :------: | :--------: |
| 10866 | class2 | Silver4 |  python  | 2022-05-21 |

⚡[문제링크](https://www.acmicpc.net/problem/10866)

⚡[deque?](https://docs.python.org/ko/3/library/collections.html#collections.deque)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
from collections import deque
import sys
input = sys.stdin.readline
d = deque()
n = int(input())
for i in range(n):
    deq = input().split()
    if deq[0] == 'push_front':
        d.appendleft(deq[1])
    elif deq[0] == 'push_back':
        d.append(deq[1])
    elif deq[0] == 'pop_front':
        if not d:
            print(-1)
        else:
            print(d.popleft())
    elif deq[0] == 'pop_back':
        if not d:
            print(-1)
        else:
            print(d.pop())
    elif deq[0] == 'size':
        print(len(d))
    elif deq[0] == "empty":
        if not d:
            print(1)
        else:
            print(0)
    elif deq[0] == 'front':
        if not d:
            print(-1)
        else:
            print(d[0])
    elif deq[0] == 'back':
        if not d:
            print(-1)
        else:
            print(d[-1])
```

</div>
</details>



# 좌표 정렬하기

| 문제번호  | class  |  level  | language |   solved   |
| :---: | :----: | :-----: | :------: | :--------: |
| 11650 | class2 | Silver5 |  python  | 2022-05-21 |

⚡[문제링크](https://www.acmicpc.net/problem/11650)

⚡python은 최대한 한 줄에 코드를 작성하자! 한줄씩 읽기 때문에 길게쓰면 쓸수록 시간이 걸린다!

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
n = int(input())
list_N = [list(map(int, input().split())) for _ in range(n)]
for x in sorted(list_N, key=lambda x: (x[0], x[1])):
    print(x[0], x[1])
```

</div>
</details>



# 달팽이는 올라가고 싶다

| 문제번호 | class  |  level  | language |   solved   |
| :--: | :----: | :-----: | :------: | :--------: |
| 2869 | class2 | Bronze1 |  python  | 2022-05-22 |

⚡[문제링크](https://www.acmicpc.net/problem/2869)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
import math
a,b,v = map(int,input().split())
x = (v-b) / (a-b)
x = math.ceil(x)

print(int(x))
```

</div>
</details>

# 덩치

| 문제번호 | class  |  level  | language |   solved   |
| :--: | :----: | :-----: | :------: | :--------: |
| 7568 | class2 | Silver5 |  python  | 2022-05-24 |

⚡[문제링크](https://www.acmicpc.net/problem/7568)

⚡2개의 조건으로 정렬해서 푼다면, 앞에 있다고 해도 뒤에 있는 항목이 앞에 있는 모든 항목보다 작다고 장담할 수 없음. 브루트포스로 풀었음.

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
n = int(input())
person = [list(map(int,input().split())) for i in range(n)]
result = ''
for i in range(n):
    cnt = 1
    for j in range(n):
        if(person[j][0]>person[i][0] and person[j][1]>person[i][1]):
            cnt += 1
    result += ' ' + str(cnt)
print(result.strip())
```

</div>
</details>