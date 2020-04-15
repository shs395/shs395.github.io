### 블로그 관리에 필요한 것들
#### 배포  
- npm run deploy (커밋 내용 : Updates)
- (== gatsby build && gh-pages -d public -b master)
- npm run deploym "원하는 커밋내용" (따로 만든 명령어)  

#### 검사
- gatsby develop 
- gatsbt develop -H 0.0.0.0
http://localhost:8000 에서 확인 가능

#### 블로그 파일 관리  
- https://shs395.github.io/posts/gatsby-blog/manage-blog-file  

#### 파일 날짜 및 시간
- 년-월-일T21:00:00+09:00 (항상 21시로 한다.)
- 하루에 쓴 글이 여러개일 경우 1분씩 추가한다.

#### 파일 이름
- 년-월-일-폴더이름(소주제)-파일이름.md (kebap case 사용)

#### posts 파일 설명
- title: 글제목
- date: 년-월-일T21:00:00+09:00
- template: "post" 
  - (page일 경우 page)
- draft: false 
  - (true -> deploy 해도 안보임)
- slug: "/posts/gatsby-blog/access-vm-localhost"
  - /posts/폴더이름(소주제)/날짜이후 파일이름
- category: "Gatsby"
  - 복수 가능
- tags:
  - "Gatsby"
- (category와 tag 는 약간 다른 개념)
- description: 제목 아래 나오는 글 설명
- socialImage: ""

#### 구조
- content/pages -> 블로그의 메뉴 같은 느낌
- content/posts -> 쓴 글
- config.js -> 블로그 관련 설정 (블로그 이름 등)
- package.json -> npm run script 만들 때 사용 / 까먹었을 때 참고
- src/components/Layout/Layout.js -> helmet 태그 안에 구글 서치콘솔 html 태그 넣어주기
- ~~gatsby/pagination/create-posts-pages.js -> 12번째 줄 category: { ne: "TWIL" } 를 통해 TWIL 이 Articles 에서 안보이게 해줌~~
- ~~src/templates/index-template.js -> 53번째 줄 category: { ne: "TWIL" } 를 통해 TWIL 이 Articles 에서 안보이게 해줌~~
- src/templates/index-template.js -> 53번째 줄 tags: { ne: "Hidden" } 를 통해 Hidden 태그를 갖고 있는 글이 Articles 에서 안보이게 해줌 **(2020.04.15 수정)**

#### 테마  
- https://github.com/alxshelepenok/gatsby-starter-lumen


