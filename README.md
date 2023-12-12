# Mafia

- 🗓 기간: 2023.11.06 ~ 2023.11.16
- Socket.io의 양방향 통신을 활용한 채팅게임

## Overview

https://github.com/noSPkeepgoing/Mafia-team4/assets/85981963/55acffb4-9bb8-4062-b0c0-10648ed541e1



## 💾 데스크탑 앱 포맷팅
![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/be782887-8921-4eaf-ac74-2e5d5f3779be)

[💿 Win x64 게임 파일 설치 링크](https://drive.google.com/file/d/1Hrq-l6EoEaIVnmpMBdsXLwkJ8z03APIw/view?usp=drive_link)
[💿 Mac 게임 파일 설치 링크](https://drive.google.com/file/d/1VQrNbMlapkXwOkMHjgPVjtX1PcYUzBUR/view?usp=share_link)

❗ win x64버전과 mac 버전이 따로 구분되어 있습니다. os에 맞는 파일을 실행하셔야 정상적으로 작동합니다.


## 🔍️ <주요 기능>

- 존재하는 모든 게임 방들의 정보를 받아 페이지에 렌더링
- 특정 게임방에 접속 시 제공받은 api와 추가 배포한 서버 api를 활용해 게임에 필요한 데이터를 요청 및 저장
- Socket 연결을 통한 게임 참가자들끼리의 채팅
- 추가 서버 api를 활용한 투표 시스템
- 투표 결과를 바탕으로 서버 데이터를 수정하고 결과를 화면에 렌더링

### 🧨선택 이유

  
- **React**
    
    우리가 만들려는 게임의 특성 상 단일 앱으로의 특성을 가지고 있기 때문에 SPA형태가 유저 경험을 향상시킬 수 있을 것이라 생각 했고, SPA 단점인  SEO의 단점에 있어서도 페이지 별 웹 노출도가 필요 없을 것이라고 생각해서 React를 적용했다.
    

- **Typescript**
    
    패스트캠퍼스에서 제공해주는 API의 응답 데이터들에 대한 스키마가 정해져있고, 불러올 데이터들의 타입을 내가 임의로 설정할 수 없게 하고, 그로 인해 오류의 가능성을 낮추기 위해 프로젝트에 타입스크립트를 적용했다.
    
- **Scss Module**
    
    CSS-in-JS는 스타일의 직렬화 과정에서 추가 CPU 리소스를 소모하기 때문에 성능에 영향을 준다는 점, 번들 크기를 늘린다는 점, css 프로퍼티를 사용하는 각 요소에 대해 Emotion의 내부 컴포넌트가 React DevTools를 어지럽힌다는 점을 근거로 CSS-in-JS의 이점을 유지하면서 성능적으로는 일반 CSS와 유사한 ‘styling system’을 고민하게 되었다.
    
    CSS-in-JS의 이점인 지역 스코프, 배치의 자율성을 그대로 가져가면서 성능의 이점을 최대화한 시스템은 css module이었다. 그러나 코드 중복을 줄이는 등의 확장 기능의 부족으로 인해 Sass Module을 선택하게 되었다.
    
    Sass Module은 기본적으로 런타임 비용 없이 지역 스코프의 CSS Module 스타일과 Sass의 빌드 시간 장점을 누릴 수 있다. 뿐만 아니라 중첩 규칙과 Mixin, 간편한 상수 선언과 사용을 통해 효율적인 개발 환경을 구성할 수 있다고 생각했다.
    
- **Vite**
    
    React 프로젝트의 대표적 생성 방식인 CRA와 비교하여 모듈 사이즈가 작고 커스텀 빌드가 쉽다는 것이 선택에 이유가 되었다. 우리 프로젝트의 경우 Electron을 적용하여 빌드를 하기 때문에 세팅이 쉬워야 했고, 모듈 사이즈의  축소는 데스크탑 앱 빌드 과정을 빠르게 해준다고 생각했다. 추가로 기존 CRA와 비교하여 src 데이터들 자체의 빌드 또한 매우 빠르다는 것이 선택의 이유였다.
    
- **Electron**
    
    페이지 이동을 통해 게임의 이벤트들과 결과들을 출력하는 우리 프로젝트의 특성 상 새로고침이나 뒤로가기 등의 유저의 예상치 못한 행동들을 막는 것에 데스크탑 앱으로 빌드하는 것이 장점이 있다고 생각했다. 뿐만아니라 게임의 특성 상 정보 페이지가 아니라 하나의 단일 어플리케이션으로써 기능하기 때문에 데스크탑 앱으로 접근하는 것이 유저 경험에 도움이 될 것이라고 생각했다.
    
- **GitHub**
    
    프로젝트의 버전 관리를 위해 선택하게 되었다. 접근성도 좋고, 이슈발생, pr생성 등 문서화에 용이하기 때문에 선택하게 되었다.
    
- **Gitflow**
    
    깃 브랜치 충돌을 최소화하고, 브랜치 분기를 강제하여 메인 브랜치에서 일어날 수 있는 혹시 모를 이슈에 기민하게 대응할 수 있도록 했다.
    
- **PocketHost**
    
    기존 제공받은 api만으로는 게임을 구현하는데 있어서 필요한 데이터들을 온전히 처리할 수가 없었다. 따라서 `noSQL` 구조로 새로운 데이터들을 담을 공간으로 추가적인 api를 배포하고 사용함으로써 추가적인 데이터를 주고 받으며 프로젝트를 진행할 수 있었다.
    
- **Redux/Toolkit**
    
    리덕스를 사용하다 보면 여러 라이브러리들을 설치하게 된다. 하지만 `Redux-Toolkit`에는 이런 많은 라이브러리들이 내장되어 있어서 많은 라이브러리들의 의존성을 줄일 수 있어서 적용했다.
    
- **Socket.io**
    
    모든 브라우저에서 동일한 기술을 적용하기 위해 사용하게 되었다. 또한 백엔드와의 원활한 통신을 위해 적용하였다.
    
    client가 요청을 보내고 server가 응답하면 연결이 바로 종료되는 기존 Rest API와는  달리 port로 실시간 양방향 통신을 하고 계속 연결을 유지하는 연결 지향형 통신이기에 Socket.io를 이용하였다.

</details>

## 🎨 프로토타입 디자인

![image](https://github.com/NamgungJongMin/Mafia-team4/assets/100336573/5f2bbb4a-f62a-46e5-961c-eeb475b23b0a)

## 📄 페이지 별 디자인 및 주요 기능

### 로그인
![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/3c9b1cde-bad2-46c6-ab89-3b2ecdb8431f)


### 회원가입
![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/e5bec1c9-7a27-4cee-bb6f-3c4d2b0d9b58)

![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/826d09ef-497a-46f3-8796-5b6d737858ff)

### 로비
![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/22c6b2de-f8b6-4b38-b652-38a7d3f7d7d4)

### 대기실
![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/5440d50d-96b2-4722-a6fd-aa05d2464f63)

### 역할 부여
![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/e7b98ce8-a4ae-4356-a420-3507f2c2994d)

### 채팅

![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/e86e574b-ee8b-456e-af37-bb45e359e39d)

### 마피아 투표

![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/0ff4513f-eaab-4e4f-956e-c404c43bb122)

### 투표 결과

![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/98affa2c-5ba7-4bc2-81c5-2c8215d82405)

### 게임 결과

![image](https://github.com/noSPkeepgoing/Mafia-team4/assets/100336573/e466cdff-c8e1-44c5-a57f-aac3154657d7)
