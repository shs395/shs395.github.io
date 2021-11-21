---
title: "[Git] 스테이징(git add) 안했을 때 지워지거나 수정된 파일 되돌리는 법"
date: "2020-04-15T00:00:00.000Z"
description: ""
categories: [git]
comments: true
---

Git의 주요 명령어는 add, commit, push 다.  
우리가 작업하는 공간은 워킹트리다(working tree)  
```git add``` 명령어는 추적되고 있지 않은 파일을 추적하거나 추적되고 있는 파일 중 변경된 파일을 스테이징한다. 커밋할 것을 정하는 것인데 워킹트리에서 스테이지로 임시로 올려준다고 생각하면 편하다.  
```git commit``` 명령어는 스테이징된 파일들을 기록해서 남기는 것이다. 임시 저장된 파일을 임시가 아닌 진짜로 기록한다고 생각하면 된다.

```git add```를 하지 않은(스테이징하지 않은) 수정되거나 삭제된 파일의 git 상태를 조회해보면 (```git status```) 아래와 같이 나올 것이다.

```bash
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)
  
  modified: 파일이름
  deleted: 파일이름
```

쉘에 답이 나온다.  
```(use "git checkout -- <file>..." to discard changes in working directory)```  
워킹 디렉토리에서 변경된 것을 버리려면 checkout을 해주면 된다.  
워킹 디렉토리에 있다는 것 == 스테이징되지 않은 파일이기 때문에
```git checkout -- 파일이름``` 을 통해서 지워진 파일을 복구하거나 원 상태로 돌릴 수 있다.  

쓸 일이 그렇게 많거나 어려운 내용은 아니지만 분명 누군가는 찾을 내용이기 때문에 올린다.  

**특히 파일을 실수로 지웠을 때** 유용하게 쓰인다.
