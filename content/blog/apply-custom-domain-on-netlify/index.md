---
emoji: 
title: netlify 에서 커스텀 도메인 이용하기
date: "2021-11-22T00:00:00.005Z"
author: uzzam
description: "porkbun에서 구매한 도메인을 netlify에 연결하기"
tags: 
categories: 블로그
---

[나는 porkbun이라는 업체에서 도메인을 구매했다](/blog/buy-domain/)

netlify에서 커스텀 도메인을 연결시킬 수 있고 방법은 아래와 같다.  
이 글에서는 porkbun 사이트 기준이나, 대부분의 도메인 사이트들에서 하는 일은 비슷하다.  

## 1. Domain Settings 에 들어간다.
![1](/images/1.png)

## 2. Add custom domain 클릭
![2](/images/2.png)

## 3. 적용을 원하는 자신의 도메인을 넣고 verify
![3](/images/3.png)

## 4. Options -> Go to DNS panel
![4](/images/4.png)

## 5. Name servers 의 항목들을 복사한다.
![5](/images/5.png)

## 6. porkbun 에서 authoritative nameservers 를 위의 netlify 에서 복사한 name server 로 바꿔준다.
타 도메인 사이트에서도 네임서버를 바꿔주면 된다.
![6](/images/6.png)

아래와 같이 바꿔주면 된다  
![7](/images/7.png)

적용이 완료되면 아래와 같이 `check DNS configuration` 대신 `Nelify DNS`이 뜬다.
![8](/images/8.png)


Github pages에서도 커스텀 도메인이 적용가능하다 -> [github pages 에서 커스텀 도메인 이용하기](/blog/apply-custom-domain-on-github-pages/)

```toc

```