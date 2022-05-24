---
title: 카카오톡 QR코드로 송금가능한 QR코드 만들기
tags: [HowTo]
style: 
color: 
description: ⏰ last update 2022/05/24 <br/> How to decode and generate KakaoTalk QR code
---

{% capture list_items %}
Process
1. QRCode Decode
2. QRCode Analyze
3. QRCode Generate 
{% endcapture %}
{% include elements/list.html title="Table of Contents" type="toc" %}

# Process

![image](https://user-images.githubusercontent.com/40678696/169950104-5215de83-c050-4f76-8c7a-07910d29e074.png)

userA에게 userB가 5만원을 송금하고 싶을 때, 플랫폼이 결제 및 송금을 지원해줘야하는데 우리 플랫폼 같은 경우는 작은 프로젝트라 거기까지는 무리였다. 그래서 현재 거의 모든 사람들이 사용하는 카카오 시스템을 이용해서 송금을 구현하면 어떨까에서 시작된 방식이다.

(하지만 결국 [아임포트](https://github.com/iamport/iamport-manual) 라는 결제 플랫폼을 통해 구현했다.)

과정은 다음과 같다.

1. QRCode Decode : 카카오톡 송금 코드를 통한 decode
2. QRCode Analyze : 카카오톡 송금 코드 분석
3. QRCode Generate : 분석한 결과를 가지고 qr 코드 생성



# 1. QRCode Decode

```python
# Import Library
import cv2
# Name of the QR Code Image file
filename = "kakao.jpg"
# read the QRCODE image
image = cv2.imread(filename)
# initialize the cv2 QRCode detector
detector = cv2.QRCodeDetector()
# detect and decode
data, vertices_array, binary_qrcode = detector.detectAndDecode(image)
# if there is a QR code
# print the data
if vertices_array is not None:
  print("QRCode data:")
  print(data)
else:
  print("There was some error")
```



송금을 받기 원하는 사용자는 카카오톡의 송금코드를 저장하여 플랫폼에 업로드한다. 업로드된 파일은  `filename`에 들어간다.

위의 코드를 통해 QRCode data를 뽑아낼 수 있다.

QRCode data : https://qr.kakaopay.com/{uid}

QRCode data : https://qr.kakaopay.com/{uid}{encoded price data}

위 두가지의 형태의 데이터가 나올 것이다.

# 2. QRCode Analyze



카카오 송금 QR 코드는 두 가지 타입이 있기 때문이다.

1. 유저 아이디만 나타내는 QR코드
2. 유저 아이디와 함께 송금 금액이 임베딩 된 QR코드

1번 타입과 같은 경우는 앞의 decode를 통해서 유저 아이디를 알 수 있었다. 2번 타입과 같은 경우는 송금 금액이 인코딩 되어 있기 때문에 이를 알아내야한다. 

다음 [블로그](http://philosophical.one/posts/kakaopay-qrcode/)에서 방식을 분석할 수 있었다. QR코드 금액 필든느 19칸 왼쪽으로 시프트 한 값에 무언가를 더한 값이었고, 그 뒤에 붙은 데이터는 에러 체킹 코드 or 랜덤데이터 라고 분석할 수 있었다.

# 3. QRCode Generate 

분석한 결과를 가지고 5만원을 송금받길 원한는 유저의 QR코드를 만들어보면

```python
import qrcode
uid = {uid}

def kakaopay_qr(uid, amount):
    return 'kakaotalk://kakaopay/money/to/qr?qr_code={0}{1:x}'.format(uid, amount << 19)

qr = qrcode.QRCode(
    version=1,
  error_correction=qrcode.constants.ERROR_CORRECT_L,
    box_size=10,
    border=4,
)

qr.add_data(kakaopay_qr(uid, 50000)) 
qr.make(fit=True)
qr.make_image(fill_color='black', back_color='white')
```

QR 코드를 생성할 수 있다. 주피터 노트북을 통해 실행해보면

![image](https://user-images.githubusercontent.com/40678696/169953633-1bcc5f2b-bcf8-445f-8c03-dc4d1a577192.png)

다음과 같이 생성된 QR코드가 나온다.

![image](https://user-images.githubusercontent.com/40678696/169953902-92209d1a-71b7-4dd1-a295-07cd8fb0b5f0.png)

스캔해보면 다음과 같이 5만원을 송금할 수 있는 코드가 생성되었음을 확인할 수 있다.

# Reference

[Rubbish Philosopher Blog](http://philosophical.one/posts/kakaopay-qrcode/)