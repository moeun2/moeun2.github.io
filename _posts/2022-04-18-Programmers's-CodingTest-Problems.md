---
title: Programmers's CodingTest Problems
tags: [CodingTest, Programmers]
style: fill
color: info
description: I'm solving coding problems of "Programmers" and summarizing.
last_modified_at: 06 June 2022
---





# Hash

## 완주하지 못한 선수

⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python

```

</div>
</details>

## 전화번호 목록

⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python

```

</div>
</details>

## 위장

⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
def solution(clothes):
    answer = 1
    hash = {}
    for i in clothes:
        hash[i[1]] = hash.get(i[1], 0) + 1
    hashList = []
    for i in hash:
        hashList.append(hash.get(i)+1)
    for i in hashList:
        answer *= i
    return answer-1
```

</div>
</details>

## 베스트앨범

⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
def solution(genres, plays):
    answer = []
    dict = {}
    num_list = {}
    for a,b in zip(genres, enumerate(plays)):
        dict[a] = dict.get(a, [])+[b]
        num_list[a] = num_list.get(a,0) + b[1]
    num_list = sorted(list(num_list.items()), key=lambda x : x[1], reverse= True)

    for key in num_list:
        temp = dict[key[0]]
        temp = sorted(temp, key=lambda x: (x[1],-x[0]), reverse = True)
        answer+=temp[:2]

    result = []
    for a in answer:
        result.append(a[0])
    return result

```

</div>
</details>

# Stack / Queue

## 기능개발

⚡[문제링크](https://www.acmicpc.net/problem/10773)

<details>
<summary>View Code...</summary>
<div markdown="1">
```python
def solution(progresses, speeds):

    answer = []
    
    xList = []
    for i in range(len(progresses)):
        if((100-progresses[i]) % speeds[i]==0):
            x = int((100-progresses[i])/speeds[i])
        else:
            x = int((100-progresses[i])/speeds[i])+1
        xList.append(x)
    
    # print(xList)
    check = xList[0]
    checkNum = 1
    for i in range(1,len(xList)):
        if(xList[i] <= check):
            checkNum += 1
        else:
            answer.append(checkNum)
            checkNum = 1
            check = xList[i]
            
    answer.append(checkNum)
    return answer
```
</div>
</details>

## 프린터

⚡[문제링크](https://www.acmicpc.net/problem/10773)

<details>
<summary>View Code...</summary>
<div markdown="1">
​```python
def solution(priorities, location):
    answer = 0
    queue =  [(i,p) for i,p in enumerate(priorities)]
    while queue:
        cur = queue.pop(0)
        maxNum = max(queue, key = lambda x:x[1])
        
        if(cur[1] < maxNum[1]):
            queue.append(cur)
        else:
            answer += 1
            if(cur[0] == location):
                return answer
    return answer
```
</div>
</details>

## 다리를 지나는 트럭

⚡[문제링크](https://www.acmicpc.net/problem/10773)

<details>
<summary>View Code...</summary>
<div markdown="1">
```python
def solution(bridge_length, weight, truck_weights):
    answer = 0
    trucks_on_bridge = [0] * bridge_length
    while len(trucks_on_bridge):
        answer += 1
        trucks_on_bridge.pop(0)
        if truck_weights:
            if sum(trucks_on_bridge) + truck_weights[0] <= weight:
                trucks_on_bridge.append(truck_weights.pop(0))
            else:
                trucks_on_bridge.append(0)
    return answer
```
</div>
</details>

## 주식가격

⚡[문제링크](https://www.acmicpc.net/problem/10773)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python
from collections import deque

def solution(prices):
    queue = deque(prices)
    answer = []
    
    while queue:
        price = queue.popleft()
        sec = 0
        for q in queue:
            sec += 1
            if price > q:
                break 
        answer.append(sec)        
    return answer
```

</div>
</details>

# Greedy

## 체육복
⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42862)

<details>
<summary>View Code...</summary>
<div markdown="1">
```python
def solution(n, lost, reserve):

    # 교집합 제거
    _reserve = list(set(reserve) - set(lost))
    _lost = list(set(lost) - set(reserve))
    
    # 정렬
    _lost.sort()
    _reserve.sort()
    
    # 빌려줄 수 있다면 제거
    for i in _reserve:
        front = i-1
        back = i+1
        
        if(front in _lost):
            _lost.remove(front)
        elif(back in _lost):
            _lost.remove(back)
    
    # 전체 학생 수 - 체육복 못 빌린 학생 수
    return n - len(_lost)
```
</div>
</details>

## 조이스틱
⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">
​```python
def solution(name):
    answer = 0  
    name = "ABA"
    # JAAVVVVB
    alpha = [chr(ord('A')+x) for x in range(26)]
    idx = 0
    while(idx < len(name)):
        print(name[idx])
        
        if(name[idx]=='A'):
            answer -= 1
            notA = idx
            for i in range(idx, len(name)+1):
                if(name[i] != 'A'):
                    notA = i
                    break
            a = notA-idx+1
            b = len(name)-1-notA+1
            print(a,b)
            break
            if(a > b):
                idx = notA
                answer += b
                continue
            else:
                idx = notA
                answer += a
                continue
            
        
        x = ord(name[idx])-ord('A')
        y = ord('Z')-ord(name[idx])+1
        if(x < y):
            answer += x
            # print("    2",x,answer)
        else:
            answer += y
            # print("    3",y,answer)
        idx +=1
        answer += 1
    return answer-1
```
</div>
</details>

# Brute-Force
## 모의고사
⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">
```python
def solution(answers):
    answer = []
    a = [1,2,3,4,5]
    b = [2,1,2,3,2,4,2,5]
    c = [3,3,1,1,2,2,4,4,5,5]
    result = [0,0,0]

    for i in range(len(answers)):
        if a[i%5] == answers[i]:
            result[0] += 1
        if b[i%8] == answers[i]:
            result[1] += 1
        if c[i%10] == answers[i]:
            result[2] += 1
            
    for idx, r in enumerate(result):
        if r == max(result):
            answer.append(idx+1)


​    
​    return answer
```
</div>
</details>

## 소수 찾기
⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">
​```python

```
</div>
</details>

## 카펫
⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">
```python

```
</div>
</details>

# DFS/BFS

## 타겟 넘버

⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">

​```python

```

</div>
</details>

## 네트워크

⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python

```

</div>
</details>

## 단어 변환

⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python

```

</div>
</details>

## 여행경로

⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42860)

<details>
<summary>View Code...</summary>
<div markdown="1">

```python

```

</div>
</details>

---

# 동적계획법(Dynamic Programming)

## N으로 표현

source : [LEO](https://programmers.co.kr/questions/19805) | [grurumee92](https://gurumee92.tistory.com/164)

⚡[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42895)

<details>
<summary>View Code...</summary>
<div markdown="1">


```python

```

</div>
</details>



# 연습문제

## 124나라의 숫자

⚡[문제링크](https://school.programmers.co.kr/learn/courses/30/lessons/12899)

<details>
<summary>View Code...</summary>
<div markdown="1">



```python
def solution(n):
    answer = ''
    return answer
```

</div>
</details>

---

