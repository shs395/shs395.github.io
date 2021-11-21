---
title: netlify 로 gatsby 블로그 자동배포하기
date: "2021-11-22T00:00:00.004Z"
description: "netlify를 이용한 push만 해도 자동배포되는 블로그 설정"
categories: [blog]
comments: true
---
github pages로도 자동배포가 가능하고, 커스텀 도메인도 적용가능한데 netlify를 쓰는 이유는 뭘까 찾아봤다.  
![vs](/media/blog/auto-deploy-blog-on-netlify/vs.png)
[netlify 홈페이지](https://www.netlify.com/github-pages-vs-netlify/)에서 보니 훨씬 좋다고 한다.  
빌드시간이 월 300분이긴하지만, 블로그를 한 달에 300분 이상 빌드할 일도 없고 무료이니 안 쓸 이유가 없다.  
게다가 netlify에서 자동배포하는 것은 훨씬 더 쉽다.  

## 1. git에서 import 하기
![site](/media/blog/auto-deploy-blog-on-netlify/site.png)
import from git 클릭 후 github 와 연동하면 repository를 선택할 수 있다.  
원하는 repository 를 선택하면 아래와 같은 설정 창이 나온다.  

## 2. 사이트 세팅 (build command, publish directory 설정)
![setting](/media/blog/auto-deploy-blog-on-netlify/setting.png)
- Branch to deploy -> master  
- Build command -> npm run build  
- Publish directory -> public  
후에 Deploy site 버튼을 눌러주면 build 후에 deploy 된다.  
또 앞으로 master branch에 push하면 자동으로 빌드되어서 배포된다.  
굉장히 쉽고 간결하다.  

![address](/media/blog/auto-deploy-blog-on-netlify/address.png)
빌드 후에는 netlify.app으로 끝나는 주소가 나오는데 그곳으로 접속하면 배포된 사이트를 볼 수 있다.  
또한 `Domain settings` 버튼을 클릭하면 아래와 같이 `Edit site name` 을 통해 netlify.app 앞부분을 자기가 원하는 형태로 바꿀 수도 있다!!
![customdomain](/media/blog/auto-deploy-blog-on-netlify/customdomain.png)


Github pages에서도 gatsby 블로그 자동배포가 가능하다 -> [github pages 로 gatsby 블로그 자동배포하기](/blog/auto-deploy-blog-on-github-pages/)