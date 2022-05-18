---
title: BJ's CodingTest Problems
tags: [CodingTest, BJ]
style: fill
color: info
description: ⏰ last update 2022/05/18 <br/> I'm solving the 2+ coding problems of  "solved.ac" and summarizing. 
---

{% capture list_items %}
제로(Class 2+/Silver4 )
균형잡힌 세상(Class 2+/Silver 4)
이항 계수 1(Class 2+/Bronze 1)
최대공약수와 최소공배수(Class 2+/Silver 5)
요세푸스 문제 0(Class 2+/Silver4)
스택(Class 2+/Silver4)
{% endcapture %}
{% include elements/list.html title="Table of Contents" type="toc" %}


# 제로(Class 2+/Silver4 )

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



# 균형잡힌 세상(Class 2+/Silver 4)

⚡[문제링크](https://www.acmicpc.net/problem/10773)

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

# 이항 계수 1(Class 2+/Bronze 1)

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



# 최대공약수와 최소공배수(Class 2+/Silver 5)

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



# 요세푸스 문제 0(Class 2+/Silver4)

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



# 스택(Class 2+/Silver4)

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