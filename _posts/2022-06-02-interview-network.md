---
title: Interview_Network
tags: [CS, Network]
style: fill
color: warning
description: this is the example of the post file
last_modified_at: 02 June 2022
---

source : [gyoogle](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Interview/Interview%20List.md#%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC)

# Q1. OSI 7계층을 설명하시오

<details>
<summary>View Answer...</summary>
<div markdown="1">
> {% include elements/highlight.html text="OSI 7계층이란, 통신 접속에서 완료까지의 과정을 7단계로 정의한 국제 통신 표준 규약" %}

물리 : 전송하는데 필요한 기능을 제공 ( 통신 케이블, 허브 )

데이터링크 : 송/수신 확인. MAC 주소를 가지고 통신함 ( 브릿지, 스위치 )

네트워크 : 패킷을 네트워크 간의 IP를 통해 데이터 전달 ( 라우팅 )

전송 : 두 host 시스템으로부터 발생하는 데이터 흐름 제공

세션 : 통신 시스템 사용자간의 연결을 유지 및 설정함

표현 : 세션 계층 간의 주고받는 인터페이스를 일관성있게 제공

응용 : 사용자가 네트워크에 접근할 수 있도록 서비스 제공

</div>
</details>

# Q2. TCP/IP 프로토콜을 스택 4계층으로 짓고 설명하시오

<details>
<summary>View Answer...</summary>
<div markdown="1">

- LINK 계층
- IP 계층
- TCP/UDP (전송) 계층
- 애플리케이션 계층

</div>
</details>

---

# Q3. TCP란?

> 서버와 클라이언트의 함수 호출 순서가 중요하다
>
> **서버** : socket() 생성 → bind() 소켓 주소할당 → listen() 연결요청 대기상태 → accept() 연결허용 → read/write() 데이터 송수신 → close() 연결종료
>
> **클라이언트** : socket() 생성 → connect() 연결요청 → read/write() 데이터 송수신 → close() 연결종료
>
> ##### 둘의 차이는?
>
> 클라이언트 소켓을 생성한 후, 서버로 연결을 요청하는 과정에서 차이가 존재한다.
>
> 서버는 listen() 호출 이후부터 연결요청 대기 큐를 만들어 놓고, 그 이후에 클라이언트가 연결 요청을 할 수 있다. 이때 서버가 바로 accept()를 호출할 수 있는데, 연결되기 전까지 호출된 위치에서 블로킹 상태에 놓이게 된다.
>
> 이처럼 연결지향적인 TCP는 신뢰성 있는 데이터 전송이 가능함 (3-way handshaking)
>
> 흐름제어와 혼잡제어를 지원해서 데이터 순서를 보장해줌
>
> - 흐름제어 : 송신 측과 수신 측의 데이터 처리 속도 차이를 조절해주는 것
> - 혼잡 제어 : 네트워크 내의 패킷 수가 넘치게 증가하지 않도록 방지하는 것
>
> 정확성 높은 전송을 하기 위해 속도가 느린 단점이 있고, 주로 웹 HTTP 통신, 이메일, 파일 전송에 사용됨