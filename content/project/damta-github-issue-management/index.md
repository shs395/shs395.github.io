---
emoji: 
title: 담타 프로젝트 관리하기 2-1 - Github으로 이슈 관리
date: "2022-10-07T00:00:00.001Z"
author: uzzam
description: 
tags: 
categories: 프로젝트-담타
---

## 들어가며
이 글은 [https://github.com/cheese10yun/github-project-management](https://github.com/cheese10yun/github-project-management) 을 많이 참고하여 담타에 프로젝트에 적용한 글이다.  

## Issue
새로 추가하거나 개선할 기능, 버그 등 프로젝트와 관련된 모든 것이 이슈다.   
리포지토리의 이슈탭에 가면 해결 / 미해결된 이슈들을 볼 수 있다.   
   
![issue1](/images/issue1.png)
  
New issue 버튼을 누르면 다음과 같은 화면이 나오고 새로운 이슈를 만들 수 있다.

![issue2](/images/issue2.png)

제목, 내용, Assignees, Labels, Projects, Milestone으로 구성되어 있다.  
`Assignees` : 책임자, 담당자를 뜻하고 10명까지 할당할 수 있다.  
`Labels` : 이슈의 종류를 표현할 수 있다. 기본으로 bug, enhancement 등 9가지가 있고 수정 가능하다.  
`Projects` : 프로젝트를 추가할 수 있다.  
`Milestone` : 사전적 의미는 '중요한[획기적인] 단계[사건]' 이라고 한다. 중요한 단계를 나타내는 것인데, 예를 들어 후에 출시할 버전이 1.0.7, 1.0.8 등등 있다고 했을 때 이슈의 마일스톤을 1.0.7로 지정해주면 1.0.7 버전을 출시하기 전에 어떤 것을 해야하는지 쉽게 확인 가능하다.

### Issue template
repository -> setting -> general -> issues 밑에 set up templates  
이슈를 발행할 때 템플릿을 미리 만들어 놓는다면 더 깔끔하고, 누가 작성하더라도 알아보기 쉬운 이슈를 생성할 수 있다. 이는 팀원이 많은 개발팀이나, 오픈소스 프로젝트에서 아주 효과적일 것 같다. 하지만 나의 경우에는 굳이 사용할 필요 없는 것 같아서 쓰지 않기로 했다.

## Issue 생성하기
앱을 마지막으로 업데이트하고 5달 정도 지났고, 여러개의 개선해야 할 점이나 버그 등이 생겼다.  
현재 생성될 이슈(이슈 종류 : 내용)는 다음과 같다.  
- 새로운 기능 : 위젯 기능 추가
- 새로운 기능 : 애플워치 컴플리케이션
- 새로운 기능 : 데이터 백업 기능
- 새로운 기능 : 로그인 기능 + 커뮤니티
- 버그 : 달력 화면에 들어가서 기존에 기록해둔 기록을 수정하고 앱 종료 후 다시 들어가면 수정 안되어 있음
- 리팩토링 : 리팩토링
- 개선사항 : flutter 3.3.3 버전 마이그레이션  

이 중 다음 버전인 1.0.7 버전에 넣어야 하는 것은 'flutter 3.3.3 버전 마이그레이션'과 '위젯 기능 추가'이다.  
나머지 기능은 차차 할 계획이 있거나, 일단 아이디어 단계이다.
이럴 때 필요한 것이 milestone이라고 볼 수 있다.  
  
![milestone1](/images/milestone1.png)  
패기롭게 일주일 뒤인 10월 7일을 due date로 하는 1.0.7 이라는 제목의 마일스톤을 만들어준다.  

![makeissue](/images/makeissue.png)  
flutter 버전을 업그레이드 해야하는 해당 이슈를 예로 들면   
   
`Assignees` : 혼자 만드는 앱,, 담당자는 나 밖에 없다.     
`Labels` : 이슈의 종류는 enhancement (new feature or request) 이다.  
`Projects` : '담타'라는 프로젝트를 추가했다. 후에 설명할 예정이다.  
`Milestone` : 위에서 만든 1.0.7 마일스톤을 사용했다.  
  
이런 식으로 아래와 같이 나머지 이슈를 발행해준다.

![issuelist](/images/issuelist.png)  
![milestone2](/images/milestone2.png)  
  
마일스톤의 경우 해당 마일스톤에 들어가면 몇 퍼센트 완료되었는지, 해당 마일스톤에 해당하는 이슈들이 무엇이 있는지를 쉽게 볼 수 있다.  

### 프로젝트
![project](/images/project.png) 
프로젝트는 깃헙에서 테이블 or 칸반보드 형식으로 프로젝트를 관리할 수 있는 기능이다.  
보드 형식으로 만들면 기본적으로 Todo, In Progress, Done 세 가지가 생긴다.  
이 외에도 원하는 보드를 추가해서 사용하면 된다.  
프로젝트를 선택해서 이슈를 추가해주면 위와 같이 No Status에 들어가고 드래그드랍으로 옮겨주면 된다. 

## 커밋 / 브랜치 네이밍 컨벤션
이슈에는 고유 넘버가 있다.  
브랜치를 만들거나 커밋을 할 때 이슈 넘버를 이용해주면 해당 브랜치 / 커밋이 어떤 이슈로 인해 진행되었는지 알 수 있어서 편하다.  
그렇다면 어떤 식으로 추가해주면 좋을까?  
예시로 헤이딜러에서는 지라를 이용하는데 아래와 같은 방식으로 한다고 한다.
[(출처 : 헤이딜러에서는 어떻게 일하나요?)](https://medium.com/prnd/%ED%97%A4%EC%9D%B4%EB%94%9C%EB%9F%AC%EC%97%90%EC%84%9C%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%9D%BC%ED%95%98%EB%82%98%EC%9A%94-1fa02b4361b5)
```
Branch: feature/HDA-123-aaa-bbb
Commit: HDA-123 커밋내용
```
그 밖에 리액트, 뷰, 비트코인 등 유명한 리포지토리들을 참고해보았는데 조금씩 달랐다.  
컨벤션에 정답이 있는 것은 아니므로 나만의 컨벤션을 만들어보았다.
```
# 하이픈(-) 으로 구분해주기
Branch: feature/이슈번호-내용 
Commit: feat: 커밋내용 (#이슈번호)
```

## 개발하기
![issue3](/images/issue3.png)  
2번째 이슈인 flutter 버전 업그레이드를 진행해보려고 한다.  

### 브랜치 생성
위에 설정한 컨벤션으로 브랜치를 만들어준다.

```bash
git checkout -b feature/2-flutter-version-migration
```

### 작업하기
버전 업그레이드 과정은 다른 글로 작성했다.  
위에서 정한 커밋 컨벤션으로 작성하였다.  
[flutter 버전 업그레이드 후기(2.10.4 -> 3.3.4)](/flutter/version-upgrade/)

### 커밋으로 이슈 닫기
![closeissue](/images/closeissue.png)
이렇게 close, closes, closed, fix, fixes, fixed, resolve, resolves, resolved 키워드 뒤에 이슈 번호를 붙이면 해당 커밋이 머지될 때 이슈가 닫힌다.

### Pull Request 생성 후 병합
Pull request 후 master 브랜치에 병합해주면 이슈가 닫히면서 끝나게 된다.  
아래와 같이 브랜치에서 작업한 커밋들이 전부 생기고 merge 커밋을 끝으로 이슈는 끝난다.  
![commit](/images/commit.png)

### 프로젝트 칸반 보드
칸반 보드에서 닫힌 이슈는 자동으로 Done 목록으로 들어간다
![projectdone](/images/projectdone.png)

### master 브랜치 병합시 유의할 점
master 브랜치에 작업하던 내용 등이 있어 pull 오류가 생길 때
```bash
git stash
git pull
```

## 나가며
이렇게 이슈들을 등록하고 이슈에 대해 개발하고 닫는 한 사이클을 직접 해보았다.  
사실 1인 개발에서는 이런 과정보다 문서화가 더 중요한 것 같다.  
다음에는 Jira로 이슈 관리를 해보고, github wiki / confluence 를 통해 문서화를 진행할 예정이다.


## 좋았던 글
[이슈란 무엇인가?](https://www.lesstif.com/jira/이슈란-무엇인가%3F-18220116.html)  
[티켓 주도 개발 (ticket-driven development)을 도입하기](https://velog.io/@aajaeyoung/ticket-driven-development)

```toc

```