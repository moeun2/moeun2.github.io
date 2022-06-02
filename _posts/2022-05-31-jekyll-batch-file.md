---
title: Jekyll 서버 실행시키는 batch 파일 만드는 방법
tags: [Jekyll]
style: border
color: primary
description: How to create a batch file that runs the Jekyll Ruby server
last_modified_at: 31 May 2022
---

{{hello}}

source : [wlrmworm](https://wormwlrm.github.io/2018/08/13/How-to-make-a-batch-file-to-run-Jekyll-server.html)

# 들어가며

Jekyll 블로그가 적응하면 포스트 올리기도 쉽고, 관리하기도 편한데 문제는 깃허브에 올리기 전에 로컬 서버를 가동할 때마다 Ruby를 켜서 내 블로그 폴더에 들어와서 bundle exec jekyll serve를 쳐야한다. 너무 귀찮아서 방법을 찾아봤고 source에 표시된 블로그에서 방법을 찾았다.

# Batch 파일 만들기

1. 새로 만들기 - 텍스트 문서
   ![image](https://user-images.githubusercontent.com/40678696/171024667-537b6994-27e4-4614-9b32-28839e2d1fc5.png)

2. 메모장에 batch file 내용 작성

```
cd C:\Ruby31-x64\bin # 각자의 환경이 다를 수 있다. C 드라이브 안에서 Ruby가 저장되어 있는 곳을 찾아보자
call setrbvars.cmd # 프로그램 실행
cd [jekyll blog 폴더의 Root] # ex ) C:\Users\Desktop\github\moeun2.github.io
bundle exec jekyll serve # jekyll server 실행
```

3. 저장하고 실행
   ![image](https://user-images.githubusercontent.com/40678696/171025322-cca02022-cba8-4cc7-a37e-fc74e974cb0e.png)

파일 형식을 **.bat**로 저장하고 인코딩을 **ANSI**로 저장하고 서버를 실행시키고 싶을 때 이 파일을 누르면 실행된다.
