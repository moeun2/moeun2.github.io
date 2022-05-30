---
title: Algorithm
tags: [Algorithm]
style: 
color: 
description: I studied the algorithms and summarized them.
---



# 유클리드 알고리즘(Euclidean Algorithm)

> 2개의 자연수의 최대 공약수(GCD)를 구하는 알고리즘

## 관련 문제

- [최대공약수와 최소공배수](https://moeun2.github.io/blog/BJ's-CodingTest-Problems#:~:text=View%20Code...-,%EC%B5%9C%EB%8C%80%EA%B3%B5%EC%95%BD%EC%88%98%EC%99%80%20%EC%B5%9C%EC%86%8C%EA%B3%B5%EB%B0%B0%EC%88%98,-%E2%9A%A1)

## 방법

1. 두 개의 자연수 a, b에서 a가 b보다 크다고 가정한다 (a>b)
2. a를 b로 나눈 나머지를 r이라고 했을 때 (a % b = r)
3. r이 0이면 b가 최대공약수 
4. r이 0이 아니라면 a에 b값을 다시 넣고 r을 b에 대입한 후 다시 반복

{% include elements/highlight.html text="ex) GCD(24,16) -> GCD(16,8) -> GCD(8,0) : 최대공약수 = 8" %}

## 구현(재귀)
```python
def GCD(a, b){
    if(b == 0){
        return a;
    }else{
        return gcd(b, a%b);
    }
}
```

## 최대공약수를 이용하여 최소공배수 구하기
```python
def LCM(a, b)
{
    return a * b / GCD(a,b);
}
```

