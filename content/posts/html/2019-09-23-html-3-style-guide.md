---
title: HTML 정리 3 - HTML5 스타일 가이드/코딩 규칙
date: "2019-09-23T21:00:00+09:00"
template: "post"
draft: false
slug: "/posts/html/3-style-guide"
category: "HTML"
tags:
  - "HTML"
description: "올바른 코딩 스타일과 규칙을 알고 익숙해지는 것은 기본기를 튼튼히 다지는 것중 하나라고 생각된다."
socialImage: ""
---

## HTML5 Style Guide and Coding Conventions

미래에 XML reader 같은 프로그램이 HTML을 읽고 싶을 수 있기 때문에 XHTML에 가깝에 쓰는 것이 현명하다.

- `<!DOCTYPE html>` (소문자 가능)
- `element 이름`은 `소문자`
- `attribute 이름`은 `소문자`
- `attribute value`에 `""` 혹은 `''` 을 사용
- 모든 element를 닫자
- empty elements 도 닫자 `ex) <br />`
- 이미지에는 항상 `alt`, `width`, `height` 를 써주자
- space 를 덜쓰자 `ex) href="style.css"`
- 한 줄에 80자 이상쓰는 코드를 피하자
- 이유 없는 빈줄을 없애고, indentation 은 스페이스 두번으로 하자
- `html`,`head`,`body` 는 생략해도 되나 생략하지 말자
- viewport를 설정해주자
- 긴 주석은 아래처럼 표현하자
```html
<!-- 
  This is a long comment example. This is a long comment example.
  This is a long comment example. This is a long comment example.
-->
```
- style 에서 한 줄인 경우는 아래처럼
```html
p.intro {font-family: Verdana; font-size: 16em;}
```
- 여러줄인 경우는 아래처럼
```html
body {  
  background-color: lightgrey;
  font-family: "Arial Black", Helvetica, sans-serif;
  font-size: 16em;
  color: black;
}
```
- 파일이름은 소문자로 하자

---

### HTML 정리 시리즈
- [HTML 정리 1 - 훑어보기](/posts/html/1)
- [HTML 정리 2 - HTML5](/posts/html/2-html5)
- [HTML 정리 3 - HTML5 스타일 가이드/코딩 규칙](/posts/html/3-style-guide)
- [HTML 정리 (부록) - 태그](/posts/html/appendix-tag)
