---
title: VM(구름IDE, Google Cloud Platform 등)에서 Gatsby를 이용하는 경우에 localhost에 접속하기
date: "2019-09-14T00:00:00.001Z"
description: "Gatsby 사용시 VM localhost 개발환경으로 접속하기"
categories: [blog]
comments: true
---



gatsby 블로그를 만들면서 처음으로 만났던 문제는 VM의 localhost에 접속을 해서 내 블로그가 잘 만들어지고 있는지 확인을 못한다는 사실이었다. ~~그래서 배포를 통한 확인만이 답인가?~~ 라는 바보같은 생각을 할 때쯤 구글링으로 답을 발견했다.  
참고 : [jekyll를 이용한 GitHub Pages에 블로그 만들기 #1](https://geeklab.tistory.com/61?category=251056)

그 후에야 아래와 같이 공식홈페이지에 써있던 내용인 것을 알았다.

If you are using VM setup like vagrant and/or would like to listen on your local IP address, run gatsby develop -- --host=0.0.0.0. Now, the development server listens on both ‘localhost’ and your local IP.  

--host=0.0.0.0() 명령을 통해 development server를 모든 ip에서 접근 가능하도록 하는 것이다.
그러니까 VM 내의 development server 가 고립된 집이고 내부에서밖에 집을 이용할 수 없었다면, 위 명령어를 통해 0.0.0.0 ~ 255.255.255.255 에서 올 수 있는 길을 열어 주는 것이다. 그리고 포트(8000)는 문으로 생각하면 좋다. 
지금 사용하고 있는 컴퓨터(모든 ip) => VM(8000번 문) => VM의 localhost 로 접속하는 격이다.

### 그러므로 우선적으로 development server를 열어주자

```
gatsby develop -H 0.0.0.0
혹은
gatsby develop --host 0.0.0.0
```

### 구름IDE (goormIDE)에서 들어가보기

구름IDE는 자체적으로 이 부분을 만들어주었다.  
상단 메뉴 프로젝트 -> 실행 URL과 포트를 눌러보면 다음과 같은 창이 뜬다.  

![구름 IDE 실행 URL과 포트](/media/gatsby-blog/url-port.PNG)  

1. 원하는 도메인 주소를 등록  
1. 포트는 8000으로 설정 (development server가 8000번 포트가 열려있기 때문이다. 원하는 포트에 따라 값을 바꾸자)  
1. 등록 클릭  
1. 사진에는 보이지않지만 아래에 적용 클릭  

후에 해당 주소로 접속시에 들어갈 수 있다.  
처음에는 헷갈려서 https://설정한이름.run.goorm.io:8000 으로 접속했으나 이미 포트 설정까지 완료된 주소이므로 그냥 주소(https://설정한이름.run.goorm.io)만 입력해서 들어가면 된다.

### GCP (Google Cloud Platform)에서 들어가보기

google cloud platform 같은 경우에는 먼저 gcp 자체의 방화벽 설정을 해주어야한다.  

![방화벽 규칙 들어가기](/media/gatsby-blog/firewall.PNG)  

VPC 네트워크 -> 방화벽 규칙에 들어가준다.

![방화벽 규칙 만들기](/media/gatsby-blog/make-firewall.PNG)  

방화벽 규칙 만들기 클릭 후   
트래픽 방향 : 수신  
대상 : 네트워크의 모든 인스턴스  
소스IP범위 : 0.0.0.0/0  
프로토콜 및 포트: 지정된 프로토콜 및 포트 - tcp 체크 후 8000 작성  
만들기  

![GCP VM인스턴스의 외부 IP주소 확인법](/media/gatsby-blog/gcp-ip.PNG)  

google cloud platform 같은 경우에는 다음과 같이 VM의 외부 ip주소가 있을 것이다.  
http://외부IP주소:8000 으로 접속하면 된다.  
<u>(**주의할 점: https 가 아닌 http 로 접속하자.**)</u>

### 마무리

이제 https://설정한이름.run.goorm.io 혹은 http://외부IP주소:8000 에 들어가서 VM의 http://localhost:8000 에 올라가 있는 블로그를 확인할 수 있을 것이다.

구름IDE 와 google cloud platform 에서 해보았는데 aws등과 같은 다른 곳도 비슷한 원리로 작동될 것이다. 또한 gastby가 아닌 jekyll이나 다른 프레임워크에서도 비슷한 원리로 작동될 듯 싶다.
