
# visualcode 유저 셋팅


# ESLint 플러그인
자바스크립트 문법 에러를 잡아내고 , 특정 문법요소를 쓰도록 만드는등 코드 퀄리티를 고치기위해 사용한다.


# prettier 플러그인
한줄의 최대길이나, tab을 쓸것인지 space를 쓸것인지, 인용스타일은 '로 할것있지 "으로 할것인지
미학적으로 통일시키는 역활을 해줍니다.

따라서 이둘을 쓴다면 코드를 더욱 간결하고 통일되게 짤수있게된다.


그렇다면 이둘을 설치할때 사전으로 설정해줘야하는 것이있다.


# 사전에 필요한 설정

## Noder.js 모듈 설치

왜설치해야할까?
javasciprt front end & back end의 통합기술이다.
즉 back end라 불리우는 서버사이드 구현체를 node.js에서 javascript로 직접 컨트롤 할 수 있도록 구현할 수 있다.


따라서 node.js 프로젝트 환경을 기본적으로 만들어 볼려고 한다.

## node 설치 


맥을 사용중이라 terminal창에서 npm모듈로 설치해주었습니다.

### eslint 모듈



같은 디렉토리에서  터미널에 다음 명령어를 입력합니다.

```console
yeji@Yejiui-MacBookPro workspace % cd Nodejs
yeji@Yejiui-MacBookPro Nodejs % npm install eslint --save-dev
```

 ![Desktop View]({{ "/assets/img/esling_pic.png" | relative_url}})
 
 
  node modules 파일과 package-lock.jason이라는 파일이 생긴것을 볼수있습니다.
  
 ### prettier 모듈
 
 같은 디렉토리에서 역시 터미널에 다음 명령어를 입력합니다.
 
 ```console
 npm install prettier --save-dev --save-exact
 ```
  
  
  ### 필요한 추가 모듈들
  
  이둘을 함께 쓰러면 추가로 여러 모듈을 설치해야합니다.
  
  - eslint-config-prettier : prettier와 충돌할 설정들을 비활성화합니다.
  - eslint-plugin-prettier : 코드 코멧할때 prettier을 사용하게 만드는 규칙들을 추가합니다.

다음 명령어로 위에서 언급한 모듈을 설치합니다.


 ```console
 $ npm install eslint-plugin-prettier eslint-config-prettier --save-dev
 ```
  

# vs code 설정하기

vs code에서 파일을 저장할때마다 자동으로 고쳐지게 하고 싶다면, 설정을 수정해야합니다.
vs code 설정 윈도우, 리눅스에서는 ctrl + , 
맥에서는 cmd + , 으로 들어갑니다.

 ![Desktop View]({{ "/assets/img/settingjson.png" | relative_url}})
 
 settings.json으로 들어가서

다음의 값을 추가해줍니다.

```console
{
    // Set the default
    "editor.formatOnSave": false,
    // Enable per-language
    "[javascript]": {
        "editor.formatOnSave": true
    },
    "editor.codeActionsOnSave": {
        // For ESLint
        "source.fixAll.eslint": true
    }
}
```
