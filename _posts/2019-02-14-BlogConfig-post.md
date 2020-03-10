---
title:  "블로그의 기본 동작과 설정."
excerpt: "Jekyll, YFM"

categories:
  - Blog
tags:
  - Blog 
  - YFM
  - jekyll
last_modified_at: 2019-04-14T08:06:00-07:00
---

> https://devinlife.com/howto/  매우 친절하고 자세히 설명되어 있는 참조 블로그 링크입니다. 

* 본 포스트에 사용되는 Github.io 블로그인 jekyll이 어떻게 동작하는지 정리하는 포스트 입니다.
* jekyll이 해석하는 YFM(YAML Front Matter) 

  * markdown 파일의 최상단에 위치하며 3개의 하이픈으로 시작과 끝을 표시합니다.
* YAML은 오픈 소스 프로젝트에서 많이 사용하는 구조화된 데이터형식
  * 글의 제목, 날짜, 카테고리, 태그, 레이아웃 등을 정의할 수 있습니다.
* YFM은 페이지 내부에서의 변수 역할을 한다. (page.title)
  

#### _config.yml

* 지킬에서 특별한 의미를 갖는 파일, 지킬 동작에 대한 설정 내용을 모두 담고있습니다..
* _post 파일이나 기타 다른파일들은 변경 사항이 생기면 지킬 서비스 중에도 해당 내용이 반영된다. 하지만 _config.yml 파일 만큼은 지킬 서비스를 중단하고 다시 사이트 빌드를 해야한다. 여러 환경설정과 변수들이 저장되어 있는데 사이트가 빌드 될때 한번만 읽어들이기 떄문.



#### navigation.yml

* _data 에 있는 navigation.yml 파일은 블로그의 메뉴를 구성한다 
* 여기서 주의해야할 부분은 " " 공백 (띄어쓰기) 도 정확히 맞춰야한다 .
  * 이부분을 간과 하면 _config.yml이 빌드가 되지 않는다.



#### 포스트를 올리고자 한다면 ...

1. Gitio repo를 수정한다고해도 블로그에 바로 적용 되지 않는 경우가 많습니다. 또한 수정내용을 일일이 repo에 커밋해서 올리는 번거로움을 피하기 위해 Ruby를 사용 할 수 있습니다 .

   * Ruby 사용 또한  [https://devinlife.com/howto%20github%20pages/github-prepare/](https://devinlife.com/howto github pages/github-prepare/)  참조 링크에 우분투 환경으로 자세히 설명 되어있습니다.
   * 윈도우 환경도 마찬가지로 start command with ruby 를 통해서 동일하게 수행할수 있습니다 .
   * 서버 실행은 아래 명령어를 입력합니다.

   ``` shell
   $bundle exec jekyll serve
   # http://127.0.0.1:4000/ 을 주소창에 입력해서 서버에 접속합니다.
   ```

2. 현재 저의 포스트는 크게 Blog , TIL, Categories, About으로 나늬어 져있습니다. 이중 페이지인 About은 제외하고

   1. Blog 에 올리고자 하면 "/root/_posts" 에 글을 올립니다.
   2. TIL에 올리고자 한다면 "/root/_pages" 에 글을 올립니다.
   3. Categories는 YFM에서 설정한 대로 자동 생성 됩니다.
   
3. **이미지 추가**

   1. 그림 파일을 repo의 특정 위치에 등록하고 주소를 기재해줍니다. 지킬은 사이트를 만들때, assets 폴더 밑의 파일들을 리소스를 활용합니다. 따라서 블로그에 그림 파일을 등록할때 보통 /assets/images 폴더를 만들고 이 폴더에 그림 파일을 저장하게 됩니다.



#### 블로그 관련 미세 팁들

* 문서내부 라인 이동
  * 간혹 인터넷 글에서 문서에 특정 라인으로 이동하는 링크들이 있습니다. markdown 문서상에서 구현 방법입니다.

    ```
    [보여지는 텍스트](#이동할위치의텍스트)
    ```

  * 이 때 #이동할위치의텍스트 는 모두 소문자만 가능하며 띄어쓰기는 -로 구분해야합니다 . 

  ```
  ex)
  [Hellow로 이동하기](#hello-world)
  ~본문~
  #Hello World
  ```



