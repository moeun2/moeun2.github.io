---
title: Jekyll 블로그 목차 만들기
tags: [Jekyll]
style: border
color: primary
description: ⏰ last update 2022/05/26 <br/> 
---

source : [jekyll-toc](https://github.com/allejo/jekyll-toc)

# 목차 만들기 (전)

![image](https://user-images.githubusercontent.com/40678696/170313566-a7886f5d-699a-4896-8178-356130259c0c.png)
이런 형태로 만들었어야 했다. 이것도 현재 사용하고 있는 테마에서 지원해줘서 괜찮긴 했는데, 하나 하나 리스트에 넣어야하는 불편함과 헤딩의 계층대로 나누어볼 수 없는 불편함이 있어 자동으로 목차를 생성해주는 것을 찾았다.

# 목차 만들기 (후)

![image](https://user-images.githubusercontent.com/40678696/170309537-784382e0-4633-4aa7-b40d-3c8420ac7009.png)

헤딩의 계층대로 나누어지며, 직접 쓰는 것이 아니라 jekyll-toc이 알아서 헤딩을 분석해서 넣어준다.

# 만드는 방법

1. [toc.html](https://github.com/allejo/jekyll-toc/blob/master/_includes/toc.html) 파일을 다운로드 한다.

2. `_includes` 폴더에 다운로드 받은 toc.html 파일을 넣는다.

3. `_layouts/post.html`안의 `{{content}}` 위에 `{% include toc.html html=content %}`을 붙혀넣는다.

   {% include elements/figure.html image="https://user-images.githubusercontent.com/40678696/170311539-bff1a1df-7283-4442-8269-138db2f238c6.png" caption="_layouts/post.html 적용 전" %}

   ​

   {% include elements/figure.html image="https://user-images.githubusercontent.com/40678696/170311610-bd493f42-8846-4b2c-8542-ccd8d4c9cc5e.png" caption="_layouts/post.html 적용 후" %}

