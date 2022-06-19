---
title: OpenVidu 설치 및 AWS에 배포하는 방법
tags: [Server]
style: 
color: 
description:  How to Deploy OpenVidu CE on AWS
last_modified_at: 19 June 2022
---



🏞️ Env : AWS Ubuntu



# Openvidu 명령어


- start openvidu : ./openvidu start
- sopt openvidu : ./openvidu stop
- Restart OpenVidu : ./openvidu restart

- show logs of openvidu : ./openvidu logs
- Show logs of Kurento Media Server : ./openvidu kms-logs
- Show actual installed version of OpenVidu and basic information about the deployment : ./openvidu version
- Generate a report with useful information of the OpenVidu deployment. This report includes: system information, containers running, logs and configuration files : ./openvidu report
- nginx log : sudo docker-compose logs nginx
- openvidu logs : sudo docker-compose logs openvidu-server
- List commands : ./openvidu help


# Docker 설치

```java
$ sudo apt-get update

$ sudo apt-get install \\
	apt-transport-https \\
	ca-certificates \\
	curl \\
	gnupg \\
	lsb-release
	
$ sudo -fsSL <https://download.docker.com/linux/ubuntu/gpg> | sudo gpg --dearmor -o
/usr/share/keyrings/docker-archive-keyring.gpg

$ echo \\
	"deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg]
	<https://download.docker.com/linux/ubuntu> \\
	$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
	
$ sudo apt-get update

$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

# Docker Compose 설치

```java
$ sudo curl -L "<https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$>(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

$ sudo chmod +x /usr/local/bin/docker-compose
```

# OpenVidu 설치

1. Openvidu에서 사용하는 포트 서버에 설정

```java
$ sudo su
ufw allow ssh
ufw allow 80/tcp
ufw allow 443/tcp
ufw allow 3478/tcp
ufw allow 3478/udp
ufw allow 40000:57000/tcp
ufw allow 40000:57000/udp
ufw allow 57001:65535/tcp
ufw allow 57001:65535/udp

+ 내가 원하는 port allow 
ufw enable
```

2. Openvidu 설치

```java
$ cd /opt  

$ sudo curl <https://s3-eu-west-1.amazonaws.com/aws.openvidu.io/install_openvidu_latest.sh> | sudo bash
```

주의 : openvidu 재설치시, /opt/openvidu 폴더 삭제해주고 curl 명령어 사용하기

3. 설정파일 수정

```java
$ cd /openvidu
$ vim .env
```

- 설정파일(env) 파일 내용

```java
DOMAIN_OR_PUBLIC_IP=<DOMAIN_OR_PUBLIC_IP>
OPENVIDU_SECRET= <seceretkey>
CERTIFICATE_TYPE=letsencrypt
LETSENCRYPT_EMAIL=<YourEmail>
HTTP_PORT=<HTTP_PORT>
HTTPS_PORT=<HTTPS_PORT> 
```

4. openvidu 서버 실행

```java
$ sudo ./openvidu start
```

5. 동작확인

```java
https://<DOMAIN_OR_PUBLIC_IP>:<HTTPS_PORT> 
https://<DOMAIN_OR_PUBLIC_IP>:<HTTPS_PORT>/dashboard/
↑ 위의 dashboard id : OPENVIDUAPP | pw : env에서 정의했던 seceretkey
해당 포트를 사용하여 openvidu server통신을 진행하면 된다(단, frontend, backend에 둘다 id와 pw, url을 넣어줘야함)
```

- 성공 시 나오는 페이지

![openvidu-image](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/78add06f-70b3-4cd6-bf57-67c3c4283b9e/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220619%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220619T080010Z&X-Amz-Expires=86400&X-Amz-Signature=627af3876802312f3dc1419113cc0b6ab4f1cea5dadccf890b7b334c0e4d38a1&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

# 404 NOT FOUND ERROR

문제상황 : 서버 nginx 사용 + .env 포트 번호를 내가 원하는 포트 번호로 바꿈 + letsencrypt 사용

해결방법 : letsencrypt를 사용시에는 nginx를 끄고 `HTTP:80`, `HTTPS:443`으로 맞춰서 openvidu server를 돌려줘야한다. 그러면 encrypt key를 받게되고 이제부터는 port번호를 바꿔도 된다. 즉, 처음에는 http,https port번호를 꼭 맞춰줘야한다

1. Nginx 서버 끄기

```java
$ sudo systemctl stop nginx
```

1. openvidu certificates 삭제하기

```java
$ sudo rm -rf /opt/openvidu/certificates/*
```

1. openvidu restart

```java
$ ./openvidu restart
```