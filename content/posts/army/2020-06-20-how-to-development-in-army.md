---
title: 군대 사지방에서 개발하는 방법들
date: "2020-06-20T21:00:00+09:00"
template: "post"
draft: false
slug: "/posts/army/how-to-development-in-army"
category: "사지방"
tags:
  - "군대"
  - "사지방" 
  - "싸지방"
description: "Cloud IDE 최고!"
socialImage: ""
---

사지방 컴퓨터의 운영체제가 하모니카OS가 아닌 win7인 경우에 해당하는 내용들이다.

## 하모니카를 쓴다면? 

[군대 사지방 하모니카 OS 200% 활용하기](https://white-hacker.tistory.com/entry/%EA%B5%B0%EB%8C%80-%EC%82%AC%EC%A7%80%EB%B0%A9-%ED%95%98%EB%AA%A8%EB%8B%88%EC%B9%B4-OS-200-%ED%99%9C%EC%9A%A9%ED%95%98%EA%B8%B0)  
[하모니카 자유게시판](https://hamonikr.org/Free_Board)

참고해보면 좋을 것 같다.

---

## 사지방 컴퓨터
사지방 컴퓨터는 불편하다.  
2시간이 되면 로그아웃되고 껐다 켜면 다운받은 파일이 사라진다.  
우클릭도 안되고 cmd도 켜기 힘들다.  
그래도 누군가가 다 좋은 방법을 알아놨더라.

### PowerShell 이용하기
왼쪽 아래 윈도우 버튼을 누르고 검색창에 powershell을 검색해서 'Windows PowerShell' 이라는 걸 열어준다.
CMD는 검색해도 나오지 않아서 주로 PowerShell 명령어를 사용한다.

### 로그아웃 안되게 하기
![logoff](/media/army/logoff.PNG)  
`logoff` 명령어를 통해 로그오프하면 두시간 이상 사용해도 꺼지지 않는다.

### 다운받은 파일 안 사라지게 하기
![ddrive](/media/army/ddrive.PNG)  
`ii d:` 명령어를 입력하면 D 드라이브가 열린다. C 드라이브는 컴퓨터를 껐다 켜면 초기화되기 때문에 계속 쓰고 싶은 파일이 있다면 D 드라이브에 넣어놓으면 된다.

### CMD 열기
![cmd](/media/army/cmd.PNG)  
`cmd` 명령어를 입력하면 powershell 창이 cmd 창으로 바뀐다. (모양은 같음)  
`exit` 명령어를 통해 다시 powershell로 돌아갈 수 있다.

### 파일 이름 변경하기
우클릭이 막혀있긴 하지만 쓸 일이 그렇게 많지는 않다.
개인적으로 파일 이름을 변경해야 할 때 우클릭을 찾았는데 파일 이름 변경은 `F2`키로 쉽게 가능하다


## 개발환경
크게 세 가지로 나누어진다. 
- Cloud IDE 사용하기(추천)
- Virtual Machine 사용하기
- 컴퓨터에 텍스트 에디터 등의 프로그램을 설치해서 쓰기(비추천)

### Cloud IDE 사용하기(추천)
Cloud IDE는 많다.  
한국어를 지원하는 [구름IDE](https://ide.goorm.io/), VSCode와 쏙 빼닮은 [Gitpod](https://www.gitpod.io/), [CodeAnyWhere](https://codeanywhere.com/) 등등 심지어 [MacOS를 쓸 수 있게 해주는 곳 (macincloud)](https://www.macincloud.com/)도 있다.
이 중에서 자신이 원하는 곳을 쓰면 된다. **하지만 나는 개인적으로 구름IDE를 추천한다.** 영어로 된 IDE는 뭔가 기가 빨리고 생산성이 저하되는 느낌이다..

#### 장점
- 굉장히 편함
- cloud 기반이기 때문에 어디서든 작업의 연속성을 가질 수 있음
- **사지방에서 이용하기에는 최고라고 생각함**

#### 단점
- 잘 모르겠음

### Cloud Virtual Machine 사용하기
GCP(Google Cloud Platform) 이나 AWS(Amazon Web Service)를 이용해서 가상머신을 하나 생성해서 쓰면 된다. 처음 회원가입을 하면 GCP는 1년 동안 쓸 수 있는 크레딧을, AWS는 1년 동안 무료로 사용할 수 있는 것들을 제공해 준다.  

#### 장점
- 구름IDE에서는 18,000원을 결제해야 사용할 수 있는 항상 켜두기 기능을 무료로도 사용할 수 있기 때문에 작은 서버가 필요할 때 이용할 수 있음
- cloud 기반이기 때문에 어디서든 작업의 연속성을 가질 수 있음

#### 단점
- GUI가 아닌 CLI이다. GUI가 되게끔 설치할 수도 있겠지만 번거롭고 복잡하다.
- Vim 을 잘 다루지 않는 한 텍스트 에디터보다 개발 속도가 현저히 느리다.

### 프로그램 직접 설치하기 (비추천)
자기가 평소에 즐겨 쓰던 프로그램이 있을 것이다. Visual Studio Code, 아톰, sublime text 등 원하는 것을 골라서 `D 드라이브`에 설치해서 쓰면 된다. 주의할 점으로는 **32bit로 설치해야 한다는 것**이다. 

#### 장점
 - 잘 모르겠음
 
#### 단점
 - 작업의 연속성이 없음, 해당 컴퓨터에서밖에 사용이 안됨

## 기타 추천 사이트
 - [사이버 지식 정보방(사지방) 개발 환경](https://neurowhai.tistory.com/192)  
(사지방에서 쓰기 좋은 사이트들을 정리해 준 블로그가 있는데 참고하기 좋다.) 




출처 & 참고 : [사지방에서 프로그래밍 공부하기 1탄 (기본적인 팁)](https://self-developing-developer.tistory.com/21) 
