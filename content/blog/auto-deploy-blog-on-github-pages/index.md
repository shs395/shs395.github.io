---
emoji: 
title: github pages 로 gatsby 블로그 자동배포하기
date: "2021-11-22T00:00:00.002Z"
author: uzzam
description: "github pages를 이용한 push만 해도 자동배포되는 블로그 설정"
tags: 
categories: 블로그
---

과거에 쓰던 gatsby 테마는 내가 브랜치를 만들어서 거기에 블로그 파일을 만들어 관리하고
deploy 를 master 브랜치에 해서 배포가 되는 식으로 진행되었다.
너무 귀찮았고 귀찮으니 글 쓰기도 귀찮았다.  

마침 새로 적용한 leonids 테마에는 자동배포하는 workflow가 있었다.  
코드는 아래와 같다.

```yml
name: Gatsby Publish

on:
  push:
    branches:
      - master

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1
      - uses: enriikke/gatsby-gh-pages-action@v2
        with:
          access-token: ${{ secrets.ACCESS_TOKEN }}
          deploy-branch: gh-pages
          gatsby-args: --prefix-paths
```

아마 대부분의 gatsby blog 는 이러한 workflow 를 이용하거나 약간 수정하면 될 듯 싶다.  
[secrets.ACCESS_TOKEN 과 관련한 문제는 여기를 클릭하여 참고하면 좋다.](/git/secret-access-token/)

이 workflow가 하는 일은 master 브랜치에 push 되면 빌드해서 `gh-pages` 브랜치에 올려준다.  

깃헙 페이지의 작동방식은 정적 사이트가 있는 브랜치를 선택하면, 보여주는 것이다.  
우리가 빌드한 정적 사이트는 `gh-pages`라는 브랜치에 올라가 있으므로 보여줄 브랜치를 `gh-pages`로 선택하는 과정이 필요하다.
![deploy branch](/images/select-deploy-branch.png)

`Source` 에서 branch 를 `gh-pages` 로 바꿔주면 앞으로 push 할 때마다 자동으로 빌드되어서 `유저이름.github.io` 에서 확인할 수 있다.

Netlify에서도 gatsby 블로그 자동배포가 가능하다 -> [netlify 로 gatsby 블로그 자동배포하기](/blog/auto-deploy-blog-on-netlify/)