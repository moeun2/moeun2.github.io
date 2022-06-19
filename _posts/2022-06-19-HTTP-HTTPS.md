---
title: HTTP와 HTTPS의 차이
tags: [Network]
style: 
color: 
description: HTTP Vs. HTTPS
---



# ❗️HTTP란

> 웹 상에서 정보를 주고 받을 수 있는 프로토콜

- HTTP는 하이퍼텍스트 전송 프로토콜(HyperText Transfer Protocol)이다.
- 초기에는 하이퍼미디어 문서를 전송했지만, 최근에는 Plain Text, JSON, XML등 다양한 형태의 정보 전송 가능하다.
- HTTP는 월드 와이드 웹(WWW)에 내재된 프로토콜이다.
- HTTP는 인터넷에서 데이터를 주고 받을 수 있는 프로토콜이다.
- 웹 페이지를 방문할 때마다 컴퓨터는 HTTP(Hypertext Transfer Protocol)를 사용하여 인터넷 어딘가에 있는 다른 컴퓨터에서 해당 페이지를 다운로드한다.



# ❗️HTTP의 특징

1. 클라이언트 서버 구조
2. 무상태 프로토콜(Stateless)
3. 비 연결성(Connectionless)
4. HTTP 메세지 (블로그에 포함 안됨)
5. 단순함, 확장 가능 (블로그에 포함 안됨)

# 👉프로토콜(Protocol)이란

> 프로토콜은 데이터를 송수신하기 위한 규칙(약속) 이라는 의미

- 컴퓨터 네트워크(관계망)에서 데이터를 주고받을 때, 이러한 규칙에 맞춰 개발함으로써 서로 정보를 교환할 수 있게 된 것이다.
- 컴퓨터 네트워크에서 데이터를 보내고 받는 성격에 따라 프로토콜이 만들어졌다.
- 웹 문서를 주고 받을 때는 HTTP를 사용해야하고 파일을 주고 받을 때는 FTP, 메일은 SMTP, POP 등 전송 계층과 유형에 따라 다양하게 만들어져있다.

# ❗️HTTPS 이란
> HTTP 프로토콜에 보안 기능(SSL)을 추가한 것

HTTPS는 'Hypertext Transfer Protocol **Over Secure Socke Layer**'의 약자로 'SSL위에 HTTP를 얹음'이라는 의미이다. 다시 말해서 HTTP라는 데이터 전송기능에 SSL이라는 보안 기능을 얹은 **보안을 강화한 전송 기능**이다.


# 👉SSL이란?
{% include elements/figure.html image="https://user-images.githubusercontent.com/40678696/174469677-373e70fe-caa7-41cb-a75c-1840649b7341.png" caption="©skinfosec" %}
SSL은 Secure Socket Layer로 정보를 암호화시킨다. 이 때, 공개키와 개인키 두 가지를 이용한다.
HTTPS는 SSL위에 HTTP프로토콜을 얹어 HTTP통신을 한다.

# ❗️HTTP - HTTPS 차이란
<br>
HTTP 동작 순서 : TCP → HTTP

<br>
HTTPS 동작 순서 : TCP → SSL → HTTP

 **문서 전송시 암호화 처리 유무에 따라 HTTP와 HTTPS로 나누어진다.**

<br> **모든 사이트가 HTTPS로 하지 않는 이유는, 암호화 과정으로 인한 속도 저하가 발생하기 때문이다.**

# 👉HTTPS 장점
1. 보안이 강화됨
2. SEO 품질이 높아짐