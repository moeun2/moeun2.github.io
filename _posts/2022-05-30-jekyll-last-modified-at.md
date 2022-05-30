---
title: jekyll 깃허브 블로그에 파일의 마지막 수정 날짜 자동으로 넣는 방법
tags: [Jekyll]
style: border
color: primary
description: How to automatically put the last_modified_at in the jekyll GitHub blog
---


# 전/후 비교
{% include elements/figure.html image="https://user-images.githubusercontent.com/40678696/171017380-8884ac70-ab8f-4a1d-8716-0ed926f2352e.png" caption="전" %}
전에는 last update를 수동으로 써주고 있었다.
{% include elements/figure.html image="https://user-images.githubusercontent.com/40678696/171017635-3fcf22ee-1040-4773-a5ff-64582882c7a5.png" caption="후" %}
후에는 자동으로 깃허브 커밋내역을 읽어서 마지막 수정날짜를 수정해준 모습이다.

# Last Modified At Plugin 사용법
source : [jekyll-last-modified-at plugin](https://github.com/gjtorikian/jekyll-last-modified-at)
## Setting Up

1. Gemfile 내용 추가
```
group :jekyll_plugins do
  gem "jekyll-last-modified-at"
end
```

2. _config.yml 파일에 내용 추가


   ```

   plugins:

     - jekyll-last-modified-at

   # Optional. The default date format, used if none is specified in the tag.

   last-modified-at:

   ​    date-format: '%d-%b-%y' #(like "04-Jan-14").

   ```

## Usage


1. layout 안에 넣는 기본방법
```
{% last_modified_at %}
```
2. 1번에 Date format 적용 시킨 방법
```
{% last_modified_at %Y:%B:%A:%d:%S:%R %}
```
3. jekyll object 메소드 호출을 통한 방법
```
{{ page.last_modified_at }}
```
4. 3번에 Dateformat 적용 시킨 방법
```
{{ page.last_modified_at | date: '%Y:%B:%A:%d:%S:%R' }}
```
5. 내가 사용한 방법

  나는 post file의 페이지 안이 아니라 post file을 모아서 볼 수 있는 카드 레이아웃에서 나오길 바랬다. 그래서 원하는 레이아웃 안에다가 아래의 이미지 대로 넣어줬다. 
  {% include elements/figure.html image="https://user-images.githubusercontent.com/40678696/171019435-54f6b6dd-3246-4ec8-936b-1bba8564faec.png" caption="원하는 레이아웃 안에 넣어준 모습" %}

