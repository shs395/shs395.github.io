---
title: "[Git] github actions(workflow) secrets 사용법"
date: "2021-11-22T00:00:00.001Z"
description: "workflow 에 있는 ${{secrets}} 문제 해결"
categories: [git]
comments: true
---

gatsby 블로그를 만드는데 아래 코드의 ${{ secrets.ACCESS_TOKEN }} 때문에 자동 배포가 안됐었다.

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

아래와 같은 방법으로 해결이 가능하다.

### 1.access token 생성하기
- 깃허브 페이지에서 오른쪽 상단의 프로필 클릭 -> `settings` -> `Developer settings` -> `Personal access tokens` 에 들어간다
  - 원래 키가 있다면, 그 키 값을 이용하면 된다.
  - 키가 없다면 `generate new token`을 통해 새로운 토큰을 만들어주면 된다.  
    token 이름, 만료일자, scope 를 설정해준다. scope는 repo만 체크해줘도 위 코드는 잘 작동한다.

### 2.레퍼지토리의 secrets에 추가하기
![secrets1](/media/git/secrets1.png)
- 적용을 원하는 레퍼지토리의 `settings` -> `Secrets` -> `New repository secret` 을 클릭한다.
![secrets2](/media/git/secrets2.png)
- 위 코드에서는 access-token이 ACCESS_TOKEN 이라는 이름으로 필요하니 그에 맞춰서 `Name` 에 써준다.
- `Value` 에는 아까 발급받았던 토큰의 값을 써주고 `Add secret`을 누른다.

