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

- LINK 계층

- IP 계층

- TCP/UDP (전송) 계층

- 애플리케이션 계층
