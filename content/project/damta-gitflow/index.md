---
emoji: 
title: 담타에 github flow 적용하기
date: "2022-08-08T00:00:00.000Z"
author: uzzam
description: 
tags: 
categories: 프로젝트 Git
---

## 도입배경
위젯 기능을 개발 중 master 브랜치에서 작업하다가 날려먹기도 하고 기능개발을 위한 브랜치를 만들어서 작업하다가 삭제한 적도 있다. master 브랜치에서만 작업하는 것은 현재 배포되고 있는 버전에 개발을 하기 때문에 불편,불안했고 새로운 기능을 만들다가 취소하거나, 만드는 중에 다른 기능을 추가하고 싶을 때 새로운 브랜치를 만들어서 개발하는 것에 비해 불편했다. 브랜치를 만들어서 작업하는게 확실히 편하구나 느껴서 Git branch 전략들을 찾아보고 `담타` 앱에 적용해보았다. 또한 추후 협업을 위한 연습과정이라는 점도 있다.

## github flow를 선택한 이유

유명한 git branch 전략으로는 `gitflow`, `github flow`, `gitlab flow`, `trunk based development` 등이 있다.   
자세한 설명은 워낙 좋은 글이 많으니 간단한 특성과 선택한 / 선택하지 않은 이유로 설명하려 한다.

### gitflow
![gitflow](/images/gitflow.png)
처음에는 gitflow 전략을 사용하려고 했다.  
gitflow는 위 사진으로 쉽게 설명이 되는데 항상 유지하는 **master**, **develop** 와 필요에 따라 생성, 삭제하는 **feature**, **release**, **hotfix** 총 5개의 브랜치로 구성된다. 뭔가 정석적인 느낌이 드는게 마음에 쏙 들었지만 프로젝트 규모도 크지 않고 거창한 QA 과정도 없는 프로젝트에서 release 브랜치까지 만드는 것은 사치이며 hotfix 브랜치 또한 쓸 일이 거의 없을 것 같았다.
> **Gitflow is a legacy Git workflow** that was originally a disruptive and novel strategy for managing Git branches. Gitflow has fallen in popularity in favor of trunk-based workflows, which are now considered best practices for modern continuous software development and DevOps practices. Gitflow also can be challenging to use with CI/CD. **This post details Gitflow for historical purposes.**  
> 출처 : https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

결정적으로 위 문단을 읽고 다른 전략을 생각해보게 되었다. (gitflow is legacy..)  
위 문단에서 `trunk-based development` 가 좋다고 하니 알아보았다.

### trunk-based development  
![tbd](/images/trunkbased.png)
기존의 기능별로 브랜치를 나눠서 하는 전략들은 분기가 된지 오래된 브랜치가 생기게 되어 병합시에 골치아플 수 있다. trunk-based는 모두가 공유하는 하나의 trunk(master 브랜치)가 있고 개발자들은 매일매일 코드를 trunk에 병합한다. 이 때 페어프로그래밍이나 풀리퀘스트, 빌드 자동화를 통해 trunk에 병합하게 된다. CI/CD 중요해짐에 따라 CI/CD의 전제조건이라고 할 수 있는 `trunk-based가 현재 가장 대세인 것 같다.`  
대세를 사용해보는 것이 좋아보였지만 개인적으로 이 프로젝트에는 github flow가 더 맞을 것 같다고 생각했다.

### github flow
![githubflow](/images/githubflow.png)
gitflow의 창시자 `Vincent Driessen`의 [gitflow 원문](https://nvie.com/posts/a-successful-git-branching-model/)에 가보면 2020년 3월 5일, github flow 같은 것을 채택하라고 업데이트 했다. [github 공식문서](https://docs.github.com/en/get-started/quickstart/github-flow)에서도 확인 가능하다.  
간단한 설명으로는
1. 브랜치를 만든다 (하는 일을 이름으로)
2. 브랜치에서 변경 -> 커밋 -> 푸시한다.
3. Pull Request 생성한다.
4. 리뷰하고 merge 한다.
5. merge 되었다면 브랜치를 삭제한다.

### 선택 이유
github flow가 gitflow에 비해 workflow가 간단하고 앱이 긴 호흡으로 개발되지 않기 때문에 낫다고 생각했다. 
trunk-based를 선택하지 않은 이유는 아직 앱에 CI / CD 환경도 갖춰지지 않았고, 1인 개발이라 혼자서 여러 기능을 동시에 구현하게 되는데 이 때 여러 기능을 trunk에 조금씩 업데이트 하는 것이 오히려 일의 복잡도를 늘릴 것 같았다.  
**그래서 후에 병합이 복잡해지더라도 개인적으로 생각하기에 여러 기능을 동시에 개발하고 버리기 용이한 github flow 를 선택하게 되었다.**

## 적용하기
오랜 염원이였던 리팩토링을 진행해보며 [github 공식문서](https://docs.github.com/en/get-started/quickstart/github-flow)를 참고하여 github flow 를 적용해보려고 한다.

### 브랜치 생성, 이동
```bash
git branch refactor/main.dart
git checkout refactor/main.dart 
```
main.dart 파일을 리팩토링 할 예정이기 때문에 의도가 잘 드러나게 브랜치를 만들어준다.

### 수정 후 커밋
커밋 룰을 적용하여 
```bash
git commit -m "refactor: 리팩토링 main.dart"
``` 
의 커밋 메시지로 커밋

### 원격지로 푸시
github flow 에서는 원격지 브랜치에 수시로 push 해주어야 한다고 한다.
```bash
git push --set-upstream origin refactor/main.dart
```
원격지에 브랜치가 올라간 것을 확인할 수 있다.  
이제 내가 하고 있는 일을 다른 사람이 확인할 수 있고, 로컬에서 데이터가 날아가도 문제없다.
![branch](/images/branch.png)  

### Pull Request 생성
![pullrequest](/images/pullrequest.png)  
원격지에 브랜치를 올리게 되면 위와 같이 나온다.

--- 

![pullrequest2](/images/pullrequest2.png)  
글을 잠시 멈춘채로 오랜시간이 지난 후에 들어가보니 이렇게 나온다.  
파란 글씨 `1 commit ahead`를 눌러준다.

---

![compare](/images/compare.png)  
이런 식으로 변화를 비교하고 pull request를 생성할 수 있다.

---

![pullrequest3](/images/pullrequest3.png)  
적절한 메시지를 남겨 pull request를 만들어준다.  
추후에 pull request 형식을 적용하여 깔끔한? pr 메시지를 만들어보려고 한다.  
오른쪽 Reviewers는 말그래도 코드 리뷰하는 사람, assignees 는 코드와 관련있는 사람이라고 한다.  ([참고](https://stackoverflow.com/questions/41087206/on-github-whats-the-difference-between-reviewer-and-assignee))
Lables, Projects, Milestone 등의 기능은 다음 글에 적용하려고 한다.

---

### 리뷰 후 브랜치 병합
![pullrequest4](/images/pullrequest4.png)  
PR을 생성하면 충돌이 있는지 자동으로 검사해준다.  
댓글도 달아보고 `merge pull request` 버튼을 눌러준다.

---

### 브랜치 삭제
![pullrequest5](/images/pullrequest5.png)  
브랜치가 병합이 완료되었다면 브랜치를 삭제해주면 된다.

#### Github 홈페이지에서 삭제
위 사진에서 `Delete branch` 버튼을 누르면 원격지에서는 삭제된다.  
하지만 삭제되었음에도 `git branch -al` 을 통해 확인해보면 남아있는 경우가 있다.  
이 때는 아래 명령어를 통해 해결가능하다.

```bash
git fetch --all --prune
```
 
로컬에서는 아래의 명령어로 삭제 가능하다.

```bash
git branch -d <브랜치 이름>
```

#### 로컬에서 삭제 후 푸시

```bash
# 로컬에서 삭제
git branch -d <브랜치 이름>

# 원격지에서 삭제
git push origin -d <브랜치 이름>

```

--- 

### 완료
![commit](/images/commit.png)  
브랜치에서 작업한 내용이 merge 커밋과 함께 정상적으로 반영되었다.

![gitlog](/images/gitlog.png)  
터미널에서도 이렇게 그래프가 분기되었다가 병합된 모습을 확인할 수 있다.

---

## 마치며
사실 github flow 는 우리에게 너무 익숙하다.  
흔히 브랜치를 따서 작업하고 PR 날리고 코드리뷰하고 테스트하고 병합하는 이런 과정들이 가장 유명하고 널리 쓰인다고 생각한다.  
근데 그게 github flow 라는 이름을 가진 것일 줄을 몰랐다..  
사실 gitflow를 적용하려고 시작한 것이었기 때문에...  
다음은 좀 더 체계적으로 프로젝트를 관리하는 법과 CI/CD에 관한 글을 쓸 예정이다.

## 도움이 된 글
[Git Branching Strategies vs. Trunk-Based Development](https://launchdarkly.com/blog/git-branching-strategies-vs-trunk-based-development/)  
[우린 Git-flow를 사용하고 있어요 - 우아한 형제들 기술블로그](https://techblog.woowahan.com/2553/)  
[[GIT] ⚡️ github flow / git flow 📈 브랜치 전략 - 👨‍💻 Dev Scroll](https://inpa.tistory.com/entry/GIT-%E2%9A%A1%EF%B8%8F-github-flow-git-flow-%F0%9F%93%88-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EC%A0%84%EB%9E%B5#Git_flow_%ED%9D%90%EB%A6%84)



```toc

```