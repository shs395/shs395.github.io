---
title: HTML 정리 (부록) - 태그
date: "2019-09-23T21:00:01+09:00"
template: "post"
draft: false
slug: "/posts/html/appendix-tag"
category: "HTML"
tags:
  - "HTML"
description: "모든 태그를 외우지는 못해도 무슨 태그가 있는지는 알아야 필요할 때 쓸 수 있을 것 같아서 정리해보았다."
socialImage: ""
---

### 태그 정리

tag(태그) : `<a>`  
element(요소): `<a href="shs395.github.io">element content</a>`  
attribute(속성): `href`

#### Basic HTML
```html
<!DOCTYPE html> html 문서라는 것을 알려줌
<html> html 문서의 시작과 끝 {lang}
<head> 메타데이터(html 문서에 관련한 정보)를 담음, 생략가능
 - title, style, base, link, meta, script, noscript
<title> 문서의 제목을 알려줌 (툴바에 뜸)
<body> html 문서의 볼 수 있는 부분 
<h1>~<h6> 제목 (문서 구조를 보여주기 위해 제목을 쓰는 것이 중요)
<p> 단락
<br> 한줄 띄기==line break
<hr> 수평선
<!-- --> 주석
```

### Formatting
```html
<abbr> 약어 표시, 브라우저에게 유용한 정보 줄 수 있음
<address> document나 article 의 글쓴이의 연락처 정보
<b> 굵게
<bdi> 텍스트의 방향성을 모를 때 사용 (왼쪽으로 읽을지, 오른쪽으로 읽을지 자동처리) 
<bdo> 텍스트의 방향을 설정해 줌 (dir="rtl or ltr") right to left / left to right
<blockquote> 인용하는 섹션표시
<cite> 작품의 제목 (책, 노래, 영화 등)
<code> 컴퓨터 코드 표시
<del> 선으로 지워줌
<dfn> 단어의 뜻
<em> 중요한 것 (이탤릭으로 보임)
<i> 이탤릭(누워있는것)
<ins> 추가된 것
<kbd> 키보드 인풋
<mark> 형광펜표시
<meter> 게이지 표시를 해줌 value="0.6" / value="2" min="0" max="10"
<pre> 띄어쓰기 같은 형식을 그대로 쓰게 해줌
<progress> 프로그레스 바에 표시해줌 value="22" max="100"
<q> 짧은 인용
<rp> ruby 태그가 안될 때를 대비하여 작성
<rt> 문자의 설명이나 발음
<ruby> 문자 및 단어에 대한 루비 주석
<s> 더 이상 맞거나 정확하지 않은 단어에 씀 <del> 태그 대신 사용하면 안됨
<samp> 컴퓨터 프로그램의 샘플 출력
<small> 작게
<strong> 중요한 것 (굵게 보임)
<sub> 아래첨자 (Subscript text)
<sup> 위첨자 (Superscript text)
<template> template 태그 안에 있는 내용은 사용자에게 안보임, js 이용해서 쓰자
<time> 시간
<u> 밑줄 (stylistically different from normal text, such as misspelled words or proper nouns in Chinese.)
<var> 변수
<wbr> 단어가 길 때, 해당 지점에서 개행될 수 있도록 함
```

### Forms and Input
```html
<form> user input을 위한 form을 만들어줌
<input> 될 수 있는 타입(button, checkbox, color, date , datetime-local , email , file, hidden, image, month , number , password, radio, range , reset, search, submit, tel, text, time , url, week) 그 밖에 많은 속성들 있음
<textarea> 여러 줄의 input
<button> 버튼
<select> drop-down list
<optgroup> option 의 그룹
<option> select(drop-down list)의 항목
<label> input 태그의 이름
<fieldset> form에서 관련되어 있는 것 끼리 묶어줌
<legend> fieldset 을 위해 네모박스 만들어줌
<datalist> drop-down + input
<output> 값을 계산해서 나타내줌
```

### Frames
```html
<iframe> inline frame을 만들어줌 , 다른 html 문서를 안에 넣을 때
```

### Images
```html
<img> 이미지 넣을 때, src,alt는 필수 / a 태그 안에 img 넣으면 클릭해서 링크로
<map> 이미지에서 클릭 가능한 구역을 정해줌
<area> map태그 안에서 구역 정할 때 쓰임
<canvas> script 이용해서 graphic 그림
<figcaption> figure 태그와 함께 쓸 때 그림 설명으로 
<figure> self-contained content
<picture> 여러개의 이미지를 화면에 따라 다르게 표현할 수 있게 하는 그룹(source 사용) / bandwith or format support
<svg> svg graphic 을 위한 container
```

### Audio/Video
```html
<audio> 소리를 들려줌 mp3,wav,ogg
<source> video,audio,picutre 의 항목들 (여러개 표현 가능하게)
<track> 자막,캡션 파일 쓸 때 사용
<video> 비디오 보여줌 mp4 추천, WebM,Ogg 가능
```

### Links
```html
<a> 하이퍼링크, 다른 페이지로 감
<link> 다른 문서나 외부 자원에 연결시켜줌 / css 파일 쓸 때 씀
<nav> navigation link의 블록을 만들어줌
```

### Lists
```html
<ul> 순서없는 리스트
<ol> 순서있는 리스트
<li> 리스트의 아이템
<dl> definition list 용어를 설명하는 목록 , ul 과 ol처럼 감싸줌
<dt> definition term 용어의 제목
<dd> definition description 용어 설명
```

### Tables
```html
<table> 표(table)을 정의함
<caption> table의 제목 넣을 때 씀
<th> 헤더, 중요한 항목(ex 맨 위)
<tr> table row 옆으로 한 줄
<td> 항목들
<thead> table의 header content (css 쓸 때 유용)
<tbody> table의 body content (css 쓸 때 유용)
<tfoot> table의 footer content (css 쓸 때 유용)
<col> column의 property를 정해줌
<colgroup> col을 묶어줌
```

### Styles and Semantics
```html
<style> 문서 내에서 css 사용가능하게 해줌
<div> division 이나 section 을 나눠줌
<span> inline-elments로 묶어줌
<header> introductory content or navigation link set / heading elements
<footer> copyright,contact,sitemap 등등
<main> 문서의 main content
<section> 섹션을 나눠줌
<article> article 섹션, 독립적으로 구성된 글
<aside> 주요 내용과 직접적 연관이 없는 분리된 내용
<details> 펼치기 기능 (view/hide)
<dialog> dialog 박스(alert 박스 같은 것)나 창을 띄워줌
<summary> detail 태그를 쓸 때 보이는 부분
<data> 기계가 읽도록 하는 것
```

### Meta Info
```html
<head> 메타데이터(html 문서에 관련한 정보)를 담음, 생략가능
 - title, style, base, link, meta, script, noscript
<meta> metadata 는 데이터에 대한 정보
<base> base URL/target 설정을 가능하게 함 (img, p 쓸 때 등)
```

### Programming
```html
<script> client-side에서 쓰게 해줌
<noscript> script 태그가 안될 때 보여줌
<embed> external application or interactive content(plug-in)를 담을 때 씀
<object>  multimedia (like audio, video, Java applets, ActiveX, PDF, and Flash)넣을 때 사용
<param> object 로 들어온 pulgin 의 parameter 설정 
```

---

### HTML 정리 시리즈
- [HTML 정리 1 - 훑어보기](/posts/html/1)
- [HTML 정리 2 - HTML5](/posts/html/2-html5)
- [HTML 정리 3 - HTML5 스타일 가이드/코딩 규칙](/posts/html/3-style-guide)
- [HTML 정리 (부록) - 태그](/posts/html/appendix-tag)