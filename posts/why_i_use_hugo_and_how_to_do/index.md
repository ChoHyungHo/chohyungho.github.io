# 블로그를 시작하다


<br />

이전부터 블로그는 하고 싶었다. 그냥 생각만 하고 눈팅만 하고 다녔다. 그러다가 Github Page라는 것을 알게 되었다.

>  오~ 이거 괜찮은데? 돈도 안들고?

그래서 조금 알아보니 Jekyll이란 것이 유명하단다.~~(도움을 많이 받으려면 대세를 따라야 한다...)~~ 그래서 시도했었다. 

처음에는 좋았다. 그런데 내 마음대로 이것저것 만지려니 생각보다 복잡하고 손이 많이 가게 되었다. 게다가 생성하고 확인하려면 Github에 올려야만 확인이 가능했다. 그래서 알아보니 또 뭔가를 설치해야 한다고 했다. 그래서 ~~빠르게~~ 포기. 그리고는 잊고 있었다.

그러다 요즘 기술적인 것들을 찾으려하면 열에 서넛은 Gihub Page 더라. 그래서 다시 한번 도전했다. 이번에는 Jekyll은 바로 제끼고 다른 것을 알아봤다. 요즘 Hugo가 뜬다더라. 슥 보니 일단 설정은 그래도 ~~Jekyll 보다는~~ 간단한 편이다. 그래서 시도해봤다.

## Hugo

### Hugo란?

Hugo를 인터넷에서 찾으면 아래처럼 나온다. 

> [Hugo](https://ko.wikipedia.org/wiki/%ED%9C%B4%EA%B3%A0_(%EC%86%8C%ED%94%84%ED%8A%B8%EC%9B%A8%EC%96%B4))는 [Go](https://ko.wikipedia.org/wiki/Go_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4))라는 언어로 개발된 [정적 사이트](https://ko.wikipedia.org/wiki/%EC%A0%95%EC%A0%81_%EC%9B%B9_%ED%8E%98%EC%9D%B4%EC%A7%80) 생성기이다. 

쉽게 말하자만 내가 적은 글(markdown)을 HTML 문서로 변환해주는 프로그램이라는 소리다. 

<br /><br />

※ 참고로 대괄호 [ ] 안에 있는 것은 내 경우의 명령이다.

### Hugo 설치

나는 Windows 운영체제에서 사용할꺼니까~~(언젠가는 Mac을 사야지...)~~ 아래 순서대로 설치한다.

1. [hugo Github](https://github.com/gohugoio/hugo/releases)에서 최신버전 다운로드 [`Windows-64bit`]
2. 압축을 풀고 원하는 위치에 놓음 [`C:\Hugo\bin`]
3. 쉽게 실행하기 위해 환경변수 `Path`에 추가 [`$ set PATH=%PATH%;C:\Hugo\bin`]
4.  커맨드창에 `$ hugo version`으로 확인

확인까지 했으면 다음 단계로 넘어간다.

### Github 설정

Hugo 설정을 하기 전에 Gihub repository부터 만든다. 만들 repository는 2가지다.

1. source repository(`<blog source name>`): 소스를 저장한다. hugo를 실행하면 내가 작성한 Markdown(이하 md) 파일들을 html 파일들로 만들고 이것으로 내 블로그 repository에 올린다. 따라서 소스를 따로 저장할 필요가 있다.[`ChoHyungHo/blog`]
2. blog repository(`<github name>.github.io`): 실제로 블로그 파일들이 올라가는 곳이다. 생성할 때 나중을 위해서 README.md 파일은 생성하도록 하자. 이 repository를 Submodule로 연결할 예정인데, 아무것도 없으면 Submodule로 clone을 할 수 없다. [`ChoHyungHo/ChoHyungHo.github.io`]

### Hugo 소스 생성

먼저 원하는 위치에 폴더를 생성한다.[`D:\Blog`] 그리고 그 폴더로 이동하여 `$ hugo new site <source folder name>` 으로 새로운 hugo 사이트를 생성한다. [`$ hugo new site blog`] 그러면 `<source folder name>`으로 폴더가 생성되고 기본 소스가 `<source folder name>`에 생성되어 있다.


```
<source folder name>
└ archetypes
  └ default.md
└ content
└ data
└ layouts
└ resources
  └ _gen
    └ assets
    └ images
└ static
└ themes
└ config.toml

```

### Hugo 테마 설정

1. [이곳](https://themes.gohugo.io/)에서 원하는 테마를 찾는다. [ 내 테마는 [Love It](https://themes.gohugo.io/loveit/) ]
2. 그 테마의 gihub repository 주소를 복사한다.
3. 선택한 테마를 submodule로 추가한다. 해당 테마를 submodule로 추가하기 위해서 `$ git init`으로 `source folder`를 초기화 해준다.[`$ git init` 이후 `$ git submodule add https://github.com/dillonzq/LoveIt.git themes/LoveIt`]
4. config.toml 파일을 선택한 테마의 설명에 따라 수정한다. [나는 [여기](https://themes.gohugo.io//theme/LoveIt/theme-documentation-basics/) 기반으로 작성]

### 글을 쓰고 확인하기

1. `$ hugo new <post name>.md`로 파일을 생성하면 `content/<post name>.md` 에 파일이 생성된다. 만약 해당 폴더에 구분을 짓고 싶으면 `$ hugo new <folder name>/<post name>.md`로 명령하면 `content/<folder name>/<post name>.md` 로 파일이 생성된다. [`$ hugo new posts/first_post.md`]

2. 생성된 파일을 열어보면 아래처럼 나온다.

   ```markdown
   ---
   title: "first_post"
   date: 2021-01-26T14:43:37+09:00
   draft: true
   ---
   
   ```

   그 밑에 간단히 글을 쓰고 저장한다.

3. `$ hugo server -D`로 서버를 실행하고 `http://localhost;1313`으로 들어가면 문서를 확인할 수 있다.(-D 옵션은 draft 문서(=초안 문서)도 볼 수 있게 해준다. draft 문서는 `$ hugo`로 빌드할 때 빌드에서 제외한다. 추가하려면 위의 양식에서 `draft: false`로 변경하면 된다.)

### Github에 소스 올리기

이제 Gihub와 연결해보자.

1. Github Page repository에 submodule로 연결한다. 이때 폴더는 public 폴더로 연결한다. 이유는 `hugo`를 빌드하면(`$ hugo`) public 폴더로 빌드하기 때문이다. 
   [`git submodule add https://ChoHyungHo@github.com/ChoHyungHo/ChoHyungHo.github.io.git public`]
   (※ 중간에 `ChoHyungHo@github.com`이 들어가는 것은 내 컴퓨터에 회사 아이디로 로그인 되어 있어서 개인 github에 올리기 위해서 넣었다.)
2. hugo를 빌드한다. [`$ hugo`]
3. public 폴더로 이동하여 github로 올린다. [다음 순서대로 명령 : `$ cd public` `$ git add .` `$ git commit -m "<message>"` `$ git push` ]
4. 루트 폴더로 이동하고(`$ cd ..`) 소스를 github로 올린다. [다음 순서대로 명령 : `$ git add .` `$ git commit -m <message>` `$ git remote add origin https://ChoHyungHo@github.com/ChoHyungHo/blog.git` `$ git push`]

<br />

소스를 다 올렸으면 한번 직접 사이트로 들어가서 확인해보자. 사이트 주소는 `<your github name>.github.io`이다.
[`ChoHyungHo.github.io`]

이후로는 글을 작성하고 `$ hugo service -D`로 `http://localhost:1313`에서 확인 후 git으로 올려주면 된다.

<br />

## Hugo 추가 사항

여기까지 했으면 기본적인 부분은 다 끝났다. 이제 블로그를 만들면 된다. 하지만 내가 원하는 대로 만드려면 몇가지 체크해야 할 사항들이 남아있다.

### 스크립트로 업로드 자동화

나는 Powershell로 실행하는 방법을 찾았다. 소스는 아래와 같다.

```powershell
Write-Output "Deploying updates to GitHub..."

# Remove-Item .\public\* -Recurse

hugo

Set-Location .\public

git add .

$msg = "rebuilding site $((Get-Date).ToString('yyyy-MM-dd')) "

git commit -m "$msg"

git push

Set-Location ..

git add .

git commit -m "$msg"

git push
```

### Post

1. 그냥 최초에 파일을 생성해서 글을 작성한 후 public 폴더에 빌드된 것을 보면 원하는 모양으로 만들어지지 않을 때가 있다. 그때는 md 파일 상단에 `url:<url>`을 추가하면 해당 폴더로 빌드된다. 기본적으로는 `config.toml`의 `[permalinks] posts` 설정으로 생성한다.
2. 처음 생성할 때 상단에 나오는 것을 변경하고 싶을 때가 있다. 그때는 `archetypes/default.md` 파일을 수정하면 생성할 때부터 원하는 대로 나오도록 할 수 있다. 그리고 post의 포멧, newsletter의 포멧 등을 나눠서 설정할 수도 있다. 해당 부분에 대한 자세한 내용은 [이곳](https://gohugo.io/content-management/archetypes/)을 참조하자.

### Customize(config.toml만으로 안될 때)

테마의 모양을 바꾸거나 특정 위치에 내가 원하는 것들을 넣고 싶을 때 사용한다. 나 같은 경우 테마에서 아바타의 링크가 post로 고정되어 있었다. 이것을 고치고 싶었는데, 아래처럼 방법을 사용했다.

1. 아바타의 페이지를 html을 찾는다. 내 테마의 경우 `themes/LoveIt/layouts/partials/home/profile.html`이었다. 
2. 해당 파일을 `layouts/partials/home/profile.html`로 복사하고 원하는 부분을 수정한다.

그리고 빌드하면 원하는 링크로 변경되어 있다. 이렇게 테마의 파일을 폴더와 같이 복사하여  `layout` 폴더에 넣은 후 수정하면 테마의 파일을 대신하여 내가 수정한 파일로 해당 부분을 수정한다. 비슷한 방법으로 아래에 나와있는 Gist를 삽입할 수 있다.

### Utterences 추가(예정)

### Gist 삽입(예정)


