---
title: github branch로 gatsby 블로그 파일 관리하기
date: "2019-09-15T00:00:00.000Z"
description: "Github branch를 이용하여 blog 파일들을 관리하자"
categories: [blog]
comments: true
---

[앞선 글 (빠르게 Gatsby + Github pages 로 블로그 만들기)](/blog/make-gatsby-blog/)에서 보았듯이  

```bash
npm run deploy (배포하기)
(== gatsby build && gh-pages -d public -b master)
```  

github pages에 배포를 할 때 빌드된 파일이 master branch에 올라가기 때문에 빌드되기 전 블로그를 작성하는 파일은 master branch에서 버전관리가 어렵다.  

> 그렇다면?  

새로운 브랜치를 만들어서 master 브랜치에는 빌드된 블로그만, 새로운 브랜치에서는 빌드되기 전 파일들만 관리하면 한 repository에서 두 가지 버전을 관리할 수 있게 되겠다.

```bash
git branch develop (develop 브랜치 생성)
git checkout develop (develop 브랜치로 전환)
git add ./
git commit -m "commit"
git push -u origin develop
```

-u 명령어는 뒤에 입력된 값을 기억시켜준다.  
즉 다음 git push 명령어는 git push origin develop 와 같다.

이제 `npm run deploy` 로 배포하고 `git push` 로 develop branch에 올릴 수 있게 되었다.