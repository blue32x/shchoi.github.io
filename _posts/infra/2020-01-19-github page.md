---
layout: post
title: 깃허브 페이지 만들기
categories: [infra]
---

깃허브 페이지 만들기
---

1.서론
---
기존에 [beatiful-jekyll](https://github.com/daattali/beautiful-jekyll)을 사용해서 운영하고 있던 github 페이지에
카테고리 별로 포스팅을 관리하고 싶은 욕구가 생겨서 시작.. but __jekyll pagenate v2는 github page에서 지원하지 않았다고 한다....__
이 작업을 하면서 사용하던 beatiful-jeyll의 _config.yml을 수정해서 로컬에서 잘 도는데 왜 deploy하면 포스팅한 글이 안나오는지에 대한 궁금증이 해결됨..
누군가는 나처럼 뻘 짓 안했으면 해서 포스팅을 함
 
2.설치 구성
---
- Jekyll (Jekyll & pagenate v2)
- travis (CI툴)


3.설치 
---
[jekyll 준비](http://jekyllrb-ko.github.io/docs/installation/#requirements)
- jekyll 설치 
```
루비가 설치 되어있어야한다. 자신의 ruby 버전을 체크해보자
$ ruby -v 
만약 없다면 위의 jekyll 준비 링크를 해 설치를 해주자.

$ gem install jekyll bundler #ruby gem을 관리해주는 gem

$ jekyll  new ./ --force   # git repogitory를 만들고 clone한 폴더 내부에서 실행한다. 
                           # --force를 붙이는 이유는 clone하면 내부에 파일이 있을 거라서 실행이 안될 것이기 때문
$ bundle exec jekyll serve #Gemfile.lock에 명시된 버전의 루비젬으로 사이트 생성
```
- jekyll theme 고르기 
```
아래 참조의 링크를 통해서 마음에 드는 지킬 테마를 다운로드 후 clone 한 repogitory에 적용한다.
```

- jekyll pagenate v2 적용

gemFile 의존성 추가
```
group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.6"
  gem "jekyll-paginate-v2", "~> 1.7"  #의존성 추가
end
```
_config.yml 수정
```
#jekyll paginate v2 설정 추가
pagination:
  enabled: true
  per_page: 5
  # limit: 0
  sort_field: "date"
  sort_reverse: true

plugins:
  - jekyll-feed
  - jekyll-paginate-v2    #추가

```

위의 과정까지 진행 후 push를 하게 되면 theme는 적용이 되나 포스팅한 게시물이 안나옴
```
jekyll-pagenate-v2 github에서 githubpage에서 공식적으로 support하고 있지 않는다고 되어있다.
```

- travis 연동
```
jekyll-pagenate-v2가 githubpage에서 support가 되지 않기 때문에 build가 제대로 되지 않는다.
jekyll-pagenate-v2를 어떻게 적용할 수 있을까 찾아보다가 travis를 통해서 해결한 케이스를 발견
repo1(깃허브 페이지의 _site를 얻기위한 레포지토리) 빌드 -> 빌드의 결과물 -> repo2(내 깃허브 페이지의 레포지토리)의 master에 push
-> deploy
이 과정을 간단하게 하기 위해서 travis라는 자동 빌드 배포 툴을 사용한다.
```
아래 참조에 있는 "pagenate를 적용하기 위한 travis 연동"을 보면 상세히 기술 되어 있다.


- 참조
    - [지킬가이드](http://jekyllrb-ko.github.io/docs/home/)
    - [지킬테마](http://jekyllthemes.org/)
    - [pagenate를 적용하기 위한 travis 연동](https://shlrur.github.io/develog/2019/01/01/jekyll-template-story-3/)