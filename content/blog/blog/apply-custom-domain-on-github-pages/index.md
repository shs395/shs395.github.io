---
title: github pages 에서 커스텀 도메인 이용하기
date: "2021-11-22T00:00:00.003Z"
description: "porkbun에서 구매한 도메인을 github pages에 연결하기"
categories: [blog]
comments: true
---

`유저이름.github.io` 레퍼지토리에 올리는 사이트는 `유저이름.github.io` 라는 깔끔한 주소의 사이트에 배포된다.  
하지만 이 주소보다 개인만의 도메인을 사용하고 싶은 때가 올 수 있다.  
[나는 porkbun이라는 업체에서 도메인을 구매했다](/blog/buy-domain/)

물론 github pages에서 커스텀 도메인을 연결시킬 수 있고 방법은 아래와 같다.  
이 글에서는 porkbun 사이트 기준이나, 대부분의 도메인 사이트들에서 하는 일은 비슷하다.  

## 1.ssl 인증서 받기 
porkbun에서는 무료로 ssl 인증서를 발급해준다.
![detail](/media/blog/apply-custom-domain-on-github-pages/details.png)
porkbun에서 domain management에 가면 자신의 도메인이 나오고 details 를 눌러 다양한 정보들을 확인할 수 있다.
![ssl](/media/blog/apply-custom-domain-on-github-pages/ssl.png)  
그 중 ssl 부분에서 edit 을 눌러주면 ssl을 발급해주고 시간이 어느 정도 소요될 수 있다. 

## 2.DNS records 추가하기
![dnsrecords](/media/blog/apply-custom-domain-on-github-pages/dnsrecords.png)  
dns records 부분에서 edit 을 눌러주면 추가할 수 있는데
![record](/media/blog/apply-custom-domain-on-github-pages/record.png)  
`type : A`, `host : @` 로 하고 `answer`에는 `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`  
총 4개의 값을 각각 입력하여 아래와 같은 결과가 나오게 한다.
![dns](/media/blog/apply-custom-domain-on-github-pages/records.png)

## 3.github에서 설정 마무리하기
![githubpages](/media/blog/apply-custom-domain-on-github-pages/githubpages.png)  
레퍼지토리에서 Settings -> Pages에 들어가서 custom domain 부분에 자신의 도메인을 입력하고 save 를 눌러준다.  
잘 적용되면 도메인 옆에 녹색 체크표시가 나오고, 위에 `Your site is publised at 도메인` 이 나온다.

Netlify에서도 커스텀 도메인이 적용가능하다 -> [netlify 에서 커스텀 도메인 이용하기](/blog/apply-custom-domain-on-netlify/)