# 첫 깃 블로그 생성하기 with jekyll

처음 깃블로그(gihub.io)를 생성하기 위해서는 아래와 같이 진행하면 된다.


#  Jekyll 블로그 생성하기
Ruby와 Jekyll 설치가 완료되었다면 이제 Jekyll 블로그를 생성할 차례다. 

Mac에서는 터미널, Windows에서는 명령 프롬프트를 실행한다. 이제 여기서 새로운 블로그를 생성하려면 아래와 같이 명령어를 입력하면 된다.
```plain
jekyll new [blog name]
```
`blog name` 에 입력한 이름으로 새로운 폴더가 생성되고 그 안에 블로그 파일이 들어가게 된다. 이제 새로운 블로그를 생성했으니 cd 명령어를 이용해 블로그 폴더로 접속해보자.
```plain
cd 블로그폴더이름
```
이제 이 블로그를 실행시켜서 테스트하려면 아래의 명령어를 입력하면 된다.
```plain
bundle exec jekyll serve
```
`bundle exec jekyll serve` 를 입력하면 Jekyll 서버가 내 컴퓨터에서 실행된다.

하지만 오류가 발생할때도 존재한다.

    `require': cannot load such file -- webrick (LoadError)
위 구문과 같은 오류가 발생할 경우 다음과 같이 해결할 수 있다.

    bundle add webrick
webrick 을 설치하고 다시 `bundle exec jekyll serve` 을 입력하면 Jekyll 서버가 내 컴퓨터에서 실행된다.

# jekyll 테마 입히기
필자 같은 경우는 minimal-mistakes 테마를 사용했다.
-   [minimal-mistakes theme 공식 홈페이지](https://mmistakes.github.io/minimal-mistakes/)
-   [minimal-mistakes 가이드](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)
-   [minimal-mistakes Github Link](https://github.com/mmistakes/minimal-mistakes)
```plain
git clone https://github.com/mmistakes/minimal-mistakes.git
```
`git clone` 을 통해서  repository를 다운 받았다면, 
필요 없는 파일을 모두 정리한다.
```plain
 .github
 test
 .editorconfig
 .gitarrtibutes
 .travis.yml
 CHANGELOG.md
 README.md
 screenshot.png
```
이상태에서 원격 서버에 올리게 되면 원격 서버에서는 보이지만, 로컬에서는 확인 할 수가 없게 된다.

현재의 repository 폴더에서 터미널을 열고 다음과 같이 입력한다.
```
gem install bundler
bundle exec jekyll serve
```
다음과 같이 입력하면, `Gemfile.lock` 파일이 생기게 된다.

그후 다음과 같이 입력해 로컬에서도 확인 할 수 있다.
```
bundle exec jekyll serve
```
http://127.0.0.1:4000 에서 로컬에서도 확인 할 수 있다.

# 기본 데이터 입력
- 수정 파일 : Repository 폴더 > _config.yml
```
minimal_mistakes_skin : "dark" # 전체적인 블로그의 색감을 정하는 값
locale : "ko-KR" # 블로그의 주요 언어 한국어로 보려고 ko-KR로 설정
title : "CheonYunHo's Blog" # 사이트 탭에서 보이는 이름
title_separator : "-"
name : "CheonYunHo" # 화면 하단 영역의 이름
url : "https://github.com/Cheongyunho" # 현재의 블로그 url

그외의 변경 사항은 다음에서 확인
https://github.com/Cheongyunho/Cheongyunho.github.io/blob/main/_config.yml
```

# favicon 설정
[realfavicongenerator](https://realfavicongenerator.net/)에 접속해서 원하는 사진을 넣는다.
![image](https://user-images.githubusercontent.com/45550607/102049292-f2031d80-3e23-11eb-9b6a-ab656118915d.png)
원하는 사진을 넣으면 위 사진과 같이 코드를 확인 할 수 있다. 
이 코드는 다음과 같은 위치에 적용한다.

- 수정 파일 : Repository 폴더 > _includes 폴더 > _head 폴더 > custom.html
```html
<!-- start custom head snippets -->

<!-- insert favicons. use https://realfavicongenerator.net/ -->
<link rel="apple-touch-icon" sizes="180x180" href="{{site.baseurl}}/assets/logo.ico/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="{{site.baseurl}}/assets/logo.ico/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="{{site.baseurl}}/assets/logo.ico/favicon-16x16.png">
<link rel="mask-icon" href="{{site.baseurl}}/assets/logo.ico/safari-pinned-tab.svg" color="#5bbad5">
<meta name="msapplication-TileColor" content="#da532c">
<meta name="theme-color" content="#ffffff">
<!-- end custom head snippets -->
```
다음과 같이 수정한다. 그럼 정상적으로 favicon이 설정된것을 확인 할 수 있다.