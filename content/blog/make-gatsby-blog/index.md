---
emoji: 
title: 빠르게 Gatsby + Github pages 로 블로그 만들기
date: "2019-09-14T00:00:00.000Z"
author: uzzam
description: "Gatsby 와 Github pages 로 빠르게 블로그를 만들고 배포해보자"
tags: 
categories: 블로그
---
 
### 이 글을 보면 좋은 사람들

- 영어로 된 공식홈페이지를 읽기 귀찮은 분
- 빠르고 간결하게 gatsby 블로그를 만들어서 github pages에 배포하고 싶으신 분

### 개발환경  

구름IDE 무료 버전 (Ubuntu 14.04 LTS) - 군대라는 장소적 제약 때문에..
  
### gatsby 선정이유
  
~~과거에 jekyll 을 이용한 github 블로그를 만들다가 ruby 가 너무 익숙치 않아서 포기하고(수정을 못하겠다..) 인터넷 검색 중에 gatsby 를 알게 되었다. gatsby는 React(요즘 핫해서,,)로 이루어져 있고 비교적 최신 것이며 star 도 많이 받았기 때문에 선택했다. 게다가 jekyll 블로그 관련 포스팅이 gatsby 관련 포스팅에 비해 2배 많았던 것도 한몫했다.~~  

<u>**다른 프레임워크들보다 모든 부분에서 좋댄다**</u>  
(참고 :https://www.gatsbyjs.org/features/jamstack/gatsby-vs-jekyll-vs-hugo/)  

다른 언어가 익숙하다면 jekyll,hugo,hexo 등의 다른 프레임워크를 찾아보는 것도 좋다. 


### 시작하기

#### 설치되어 있어햐 하는 것  

node / npm / git / ~~homebrew~~ (설치 안해도 무관)
 
#### gatsby 설치

```bash
npm install -g gatsby-cli
```

#### 테마 골라서 설치하기

https://www.gatsbyjs.org/starters/?v=2 에서 원하는 테마 찾아보기  
가장 별이 많은 기본 테마로 해보았다.

```bash
gatsby new (원하는 폴더 이름) https://github.com/gatsbyjs/gatsby-starter-blog
cd (원하는 폴더 이름)
gatsby develop
```

까지하면 http://localhost:8000 에서 블로그를 확인할 수 있다!  

**그런데 VM(구름IDE, Google Cloud Platform 등)을 이용하는 경우에 localhost에 어떻게 접속하지? =>** [여기에서 확인](/blog/access-vm-localhost/)

### 글 작성하기

content/blog/gatsby-blog/index.md

```
---
title: 빠르게 Gatsby + Github pages 로 블로그 만들기
date: "2019-09-14T16:00:00+09:00"
description: Gatsby 와 Github pages 로 빠르게 블로그를 만들고 배포해보자
---

### 이 글을 보면 좋은 사람들
(생략)

```

### 블로그 정보 수정하기

gatsby-config.js - 블로그와 관련한 설정을 하는 파일  
블로그 이름 등등을 바꿔주자

```
siteMetadata: {
    title: `블로그 이름`,
    author: `작성자`,
    description: `블로그 설명`,
    siteUrl: `블로그 주소`,
    social: {
    },
```

### github pages 배포

gh-pages package 설치

```bash
npm install gh-pages --save-dev
```

#### 배포하려는 github repository 이름이 username.github.io 가 아닌 경우  

gatsby-config.js

```javascript
module.exports = {
  pathPrefix: "/respository이름",
}
```

package.json

```json
{
  "scripts": {
    "deploy": "gatsby build --prefix-paths && gh-pages -d public"
  }
}
```

#### 배포하려는 github repository 이름이 username.github.io 인 경우  

gatsby-config.js 수정 X  
package.json

```json
{
  "scripts": {
    "deploy": "gatsby build && gh-pages -d public -b master"
  }
}
```

### 배포하기!

```bash
npm run deploy
```

**<u>username.github.io</u> 혹은 <u>username.github.io/repo이름</u> 에서 확인 가능하다.**

