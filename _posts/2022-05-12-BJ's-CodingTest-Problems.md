---
title: BJ's CodingTest Problems
tags: [CodingTest, BJ]
style: fill
color: info
description: ⏰ last update 2022/05/13 <br/> I'm solving the 2+ coding problems of  "solved.ac" and summarizing. 
---

{% capture list_items %}
제로
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



# 균형잡힌 세상

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