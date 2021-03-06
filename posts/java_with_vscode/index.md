# VS Code에서 Java 프로그래밍


## 다시 Java로

나는 자바로 시작했다가 c#으로 넘어왔다. 회사에서 java를 사용하지 않기에 거의 잊어버렸다. 이러다 완전 놓치게 될까봐 다시 한번 공부하기로 했다.

## Java 설치

처음엔 기억을 더듬어 자바를 깔려고 했더니 오라클로 연결이 되더라. 오라클로 인수되었다는 소식을 듣긴 했지만 실제로 들어가보니 생소했다. 듣기로 오라클 자바를 사용하면 여러 추가적인 요소 때문에 라이센스 문제가 발생한다더라. 그래서 그냥 자바를 사용할 수 있는 것을 찾았더니 [OpenJDK](https://openjdk.java.net/)라는 것이 있어 이 자바를 설치하면 된다고 했다. 자 이제 최신 버전을 다운을 받고 설치를 해보자.

어라? 그냥 zip 파일이네...? 설치 파일은 따로 없고 실행을 위한 파일만 zip으로 묶여 있다. 흠... 그럼 일단 설치하는 방법부터 찾아보자.

1. 원하는 위치에 압축을 푼다. [`C:\Java\jdk` -> `C:\Java\jdk\jdk-15.0.1`]

2. 환경변수 추가

    A. Window 키 -> `고급 시스템 설정 보기` 라고 타이핑 후 선택 -> `환경 변수(N)` 선택

    B. 시스템 변수에 `새로 만들기(W)`선택하여 변수 이름은 `JAVA_HOME` 변수값은 압축을 푼 폴더(`c:\Java\jdk\jdk-15.0.1`)를 넣고 `확인`
    
3. 시스템 변수에서 `Path` 더블클릭 -> `새로 만들기` -> `%JAVA_HOME%\bin` 이라고 입력 후 `확인`

이렇게 입력하면 기본적인 java의 설치는 끝난다.

## VS Code(Visual Studio Code)

다시 기억을 더듬어 java의 IDE인 이클립스를 사용하기 위해 설치를 하고 잠깐 사용했더니... 이런, 너무 답답하다는 느낌이 들었다. 그래서 이번엔 조금 더 익숙하고 이제는 유명해진 VS Code로 java를 개발해 보기로 했다.(사실 다른 프로젝트에 기술 자문으로 참여했던 적이 있었는데 그때 이미 이클립스를 사용해보고 아니다 싶어 vs code로 개발하도록 지원했다.)

vs code를 설치하고 필요한 extention을 설치했다.

- Korean Language Pack for Visual Studio Code: 한국인이라면...
- Java Extentio Pack: 여기에 자바 개발에 필요한 여러가지 확장을 하나의 팩으로 MS에서 묶어놓았다. MS는  vs code로 java를 개발할 수 있도록 많은 지원을 하고 있다. ㄳㄳ
- Spring Boot Extention Pack: 이것도 MS에 모아놓은 Spring 관련 extention들. 나중에라도 시작할 수 있으니 

별로 안되어 보이지만 Pack으로 묶어놨기에 꽤 많은 확장들을 간단히 설치할 수 있었다.

## Java로 "Hello World" 찍기

공부할 폴더를 만들고(`D:\Study\Java`) 거기에 시작을 해봐야 하는데... 여기서 시행착오를 좀 거쳤다.

결론만 말하면 아래의 순서대로 진행했다.

1. `ctrl + shift + p`  를 누르면 모든 명령 표시 창이 나오고 거기서 `java project`라고 타이핑을 하면 `java:create java projects`라고 나온다. 그걸 선택한다.
2. 그러면 빌드 툴을 선택하게 되어 있는데 나는 익숙한 `Maven`을 선택했다.
3. 그리고 archetype을 선택하는데 일단 단순히 공부하는 거니까 `maven-archetype-quickstart`를 선택했다.
4. 그러면 터미널 창에서 maven이 실행되면서 프로젝트를 생성하는데 `groupId`와 `artifactId`를 입력하고 나머지는 그냥 스킵하면 프로젝트 폴더를 `artifactId`로 만들고 그 안에 기본적인 소스들을 넣어준다.

이렇게 기본적인 프로젝트는 생성했다.

이제 유명한 `Hello World`를 찍어보자. 

간단히 f5 키만 눌러도 컴파일 되고 실행이 된다. 그리고 터미널 창에 찍히는 "Hello World!". 간만에 보는 `Hello World`다.

## 간단히 둘러보는 vs code

### Debug

f5 키를 누르면 컴파일을 하고 프로그램이 debuging mode로 실행이 된다. 당연히 break를 걸어서 확인해 볼 수도 있다.

### Unit Test

프로젝트를 생성하고 나면 src/test/ 안에 UnitTest를 만들 수 있는 곳이 있다. 이곳에서 UnitTest를 위한 파일을 생성한다.

UnitTest 소스를 만들면 테스트를 실행하는 방법이 몇가지 있는데, 하나는 왼쪽 확장 창에서 테스트 창을 띄우는 것이고, 다른 하나는 소스 내에 `Run Test | Debug Test` 버튼을 누르는 것이다.

1. 확장을 이용한 UnitTest

   처음 UnitTest 파일을 만들고 나면 이곳에 해당 클래스가 보이게 되는데, 만약 안보인다면 위쪽에 있는 refresh 버튼을 누르면 나온다. 여기서 각 클래스 별로 테스트를 진행하거나 함수별로 테스트를 진행할 수 있다. 진행 후 결과는 이 창의 각 함수 옆에 아이콘으로 표시된다.

2. 소스 내 `Run Test | Debug Test`

   처음 UnitTest 파일을 만들고 나면 이 버튼이 보이지 않는다. 함수를 만들고 그 위에 `@Test` annotation을 붙이고 나면 해당 버튼들이 보인다. 이 버튼을 클릭해서 클래스 별로 테스트를 진행하거나 함수별로 테스트를 진행할 수 있다. 진행 후 결과는 다른 창(Java Test Report)에서 따로 보인다. 만약 보이지 않는다면 밑 상태표시줄에 보면 `X 0 √ 1`이런 표시가 보이는데 마우스를 올려보면 `Show test report`라고 나온다. 이걸 클릭하면 Java Test Report 창이 나온다.

<br />

이제 간단히 둘러봤다. Java 공부를 시작해보자.
