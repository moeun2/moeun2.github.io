---
title: Process and Thread
tags: []
style: 
color: 
description: this is the example of the post file
---

source : [rebro](https://rebro.kr/172)

프로세스  : 컴퓨터에서 실행되고 있는 프로그램
스레드 : 프로세스 내 작업의 흐름

프로그램이 메모리에 올라가면
프로세스가 되는 인스턴스화가 일어나고
운영체제의 CPU 스케줄러에 따라 
CPU가 프로세스를 실행한다.



# 프로세스 상태

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FnBn7F%2FbtrexdmdCyf%2FMDWTBDpGkyzzvz2FEY2qP0%2Fimg.png)




1. New : 프로세스가 처음 생성된 상태
2. Ready : 프로세스가 CPU에 할당되기를 기다리는 상태 (메모리 등 다른 조건을 모두 만족하고)
3. Running : 프로세스가 할당되어 CPU를 잡고 명령을 수행 중인 상태
4. Waiting : 프로세스가 어떠한 이벤트가 발생하기를 기다리는 상태. CPU를 할당해도 당장 명령을 수행할 수 없는 상태.
5. Terminated : 프로세스가 실행을 마쳤을 때. 아직 완전히 프로세스가 제거되진 않은 상태.




