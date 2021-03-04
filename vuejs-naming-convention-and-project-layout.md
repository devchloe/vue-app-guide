# Vue.js Style guide
Vue.js 어플리케이션을 위한 Code Convention 입니다.

## Table of Contents
- Why project layout, naming rule important?
- Vue 컴포넌트 네이밍 컨벤션
  - Vue 스타일 가이드
  - 추가
- CSS 네이밍 컨벤션
  - BEM 소개
  - BEM 사용방법
- 프로젝트 레이아웃
  - 기본: smart-dummy pattern
  - 확장: one pick

## 왜 프로젝트 레이아웃, 네이밍 룰을 정해야하는가?
- 명확한 기준점
- 코드 가독성/명확성 (빠르게 파일 찾기 가능)
- 코드 생산성 (이름짓는데 시간이 많이 걸림)
- 팀원간 커뮤니케이션 (+ 새로운 팀원의 합류)
- 코드품질

## Vue 컴포넌트 네이밍 컨벤션
### Vue 스타일 가이드
- [참조: Vue 스타일 가이드](https://kr.vuejs.org/v2/style-guide/index.html#%EA%B7%9C%EC%B9%99-%EB%B6%84%EB%A5%98)
- 싱글 파일 컴포넌트 이름 규칙 (**)
  - Pascal: MyComponent.vue (더 많은 장점이 있다)
  - kebab: my-component.vue Vue
- Base 컴포넌트 이름 Prefix 규칙 (**)
  - Base
    - BaseButton.vue
    - BaseTable.vue
    - BaseIcon.vue
  - App
    - AppButton.vue
    - AppTable.vue
    - AppIcon.vue
  - V
    - VButton.vue
    - VTable.vue
    - VIcon.vue
- 싱글 인스턴스 컴포넌트 이름 Prefix 규칙
  - The
    - TheHeading.vue
    - TheSidebar.vue
- 강한 연관성을 가진 컴포넌트 이름 규칙
  - 자식 컴포넌트는 부모 컴포넌트명을 Prefix로 한다
    - X
      - SearchSidebar.vue
      - NavigationForSearchSidebar.vue
    - O
      - SearchSidebar.vue
      - SearchSidebarNavigation.vue
- [컴포넌트 이름의 단어 순서 정렬](https://kr.vuejs.org/v2/style-guide/index.html#%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-%EC%9D%B4%EB%A6%84%EC%9D%98-%EB%8B%A8%EC%96%B4-%EC%88%9C%EC%84%9C-%EC%A0%95%EB%A0%AC-%EB%A7%A4%EC%9A%B0-%EC%B6%94%EC%B2%9C%ED%95%A8)
 
  **"컴포넌트 이름은 the highest-level 단어로 시작하고 수식어로 끝내라"**

  - 자연스러운 영어에서는 명사를 수식하는 형용사가 앞에 나온다. **(예) 아름다운 가게**
  - 그러나 예외도 있다. 연결어가 필요한 경우, 명사 + 명사 **예) Coffee `with` milk, Soup `of the` day**
  - 이런 연결어를 컴포넌트 이름에 포함시킬 수 있지만, 순서가 상당히 중요하다.

  - 왜 중요한가? 어떤 것이 the highest level이냐는 어플리케이션 context에 따라 달라진다.
  - 예를 들어서, search form을 만든다고 생각해보자.

  ```
  ClearSearchButton.vue
  ExcludeFromSearchInput.vue
  LaunchOnStartupCheckbox.vue
  RunSearchButton.vue
  SearchInput.vue
  TermsCheckbox.vue
  ```
  어떤 컴포넌트가 search form과 관련있는지 이해하기 상당히 어렵다.
  이름을 리팩토링 해보자.

  ```
  SearchButtonClear.vue
  SearchButtonRun.vue
  SearchInputExcludeGlob.vue
  SearchInputQuery.vue
  SettingsCheckboxLaunchOnStartup.vue
  SettingsCheckboxTerms.vue
  ```
  이렇게 이름을 작성하면 editor들이 알파벳 순으로 파일을 정렬하기 때문에 컴포넌트간 관계를 한 번에 알아볼 수 있게 된다.

- 컴포넌트 이름은 약어를 쓰지 않는다.
- Prop 이름 규칙
  - HTML 템플릿 안에서는 kebab-case를 사용
  - Prop 선언은 camelCase
  ```
  export default {
      name: 'WelcomeMessage',
      props: {
        greetingText: String
    }
  }
  ```
  ```
  <WelcomeMessage greeting-text="hi"/>
  ```
### 추가 스타일 가이드
- 메서드, 이벤트 리스너 이름

## BEM 패턴을 이용한 CSS 네이밍 컨벤션

### CSS Namining 기본 규칙 
- 원칙1. 이름만 보고도 **용도**를 알 수 있아야 함
- 원칙2. 이름을 보고 **어디에 쓸 수 있을지** 알 수 있아야 함
- 원칙3. 이름을 보고 **HTML element간의 관계**를 알 수 있어야 함

### BEM 이란 
- Block(블럭, 부모), Element(요소, 자식), Modifier(변환자)
- 코딩 스타일이 아닌 패턴

### BEM 목표 
- 빠른 개발 속도, 효율적인 구조와 커뮤니케이션 확립, 학습 곡선없이 바로 작업 환경 조성, 재사용 가능한 모듈 개발, 시간이 지나도 유지보수 가능하게 

### Unified Data Domain 지향
- 팀원이 개별적으로 일하는게 아니라 팀원이 함께 Block의 이름을 함께 짓고 이 용어를 공통적으로 사용하는 것

### BEM을 이용한 CSS Naming 예시
- [참조](https://www.freecodecamp.org/news/css-naming-conventions-that-will-save-you-hours-of-debugging-35cea737d849/)
- Block-Element-Modifier 세 요소로 나뉘어짐

- Block은 덩어리, element는 개별 요소, 부모 컴포넌트 - 자식 컴포넌트 관계와 같다.

- B: block, standalone으로 의미를 갖는단위
![stick-man](./images/stick-man.png)
    - .stick-man
- E: element
![stick-man-element](./images/stick-man-element.png)
    - .stick-man__head : .stick-main의 자식 요소를 의미
    - .stick-man__arms
    - .stick-man__feet
- M: modifier (변경 상태(스타일, 동작 등)를 나타낸다)
![stick-man-modifier](./images/stick-man-modifier.png)
    - .stick-man—red
    - .stick-man—blue
    - element 일부가 바뀐 경우
        - .stick-man__head—small
        - .stick-man__head—large
- 요약
  - 하이픈 1개로 연결된 단어는 하나의 단어를 의미
  - 상위 컴포넌트와 자식 컴포넌트는 언더스코어 2개로 연결
  - 하이픈 2개는 변경된 상태를 의미 (컴포넌트 바로 뒤에 하이픈2개로 연결한다)
- 주의
  - BEM은 DOM Tree를 그대로 표현하자는 룰은 아니기 때문에 적당한 중첩 레벨을 선택한다. 하나의 자식만 표현(언더스코어 2개는 한번만 나타나도록 정의)

## 프로젝트 레이아웃
### Vue/React 개발자라면 누구나 들어보게 되는 개념
- 기본: Smart-Dummy pattern
  - Smart Component & Dummy Component로 분할
  - HTML 요소만 갖고 있는 컴포넌트, 화면만 렌더링하는 역할 컴포넌트
  - 여러 컴포넌트를 조합하거나 데이터를 가져오는 등 서버와 통신하는 컴포넌트 등
- 변형: 시스템 크기, 특성에 따라 디렉토리를 더 세분화할 수 있음
  - 시스템은 변화하기 때문에 레이아웃 또한 시스템에 맞게 언제든 변화할 수 있다는 열린 마음을 갖는게 중요함!
  - 언제든 바꿀 수 있다? 가능한가? UI를 작은 컴포넌트 단위로 잘 쪼개서 만들어놨다면 + 네이밍 잘 + 명확한 컴포넌트 역할이라면 가능

  > 어차피 많은 고민을 해봤자 더 좋은 답은 없다. 5분 정도 고민해보고 의사결정할 것

### [이걸로 시작해봅시다](https://vueschool.io/articles/vuejs-tutorials/structuring-vue-components/)

**0단계: Vue CLI로 프로젝트 생성한 후**
```
  src
    ├─components
    │      
    │
    └─pages
```
- components: 다른 컴포넌트 안에서 쓰이는 단일 컴포넌트
- pages: url별로 화면이 바뀌는 컴포넌트, components 디렉토리에 속한 다른 컴포넌트들이나 HTML 요소들을 포함할 수 있음
```bash
npm run serve # http://localhost:<PORT>/ 또는 http://localhost:<PORT>/about 확인
```

<br>

이제부터 `블로그`를 만든다고 가정해봅시다.

**1단계: ArticlePage, ArticleTitle, ArticleList, LastArticlesSection 컴포넌트 생성**

<요구조건>

- "/blog/1로 접속하면 1번 `블로그 글`이 보이게 해주세요."
- "블로그 글이 나오는 페이지에는 `블로그 제목`, `블로그 목록`, `최근 블로그글들`을 보여주세요"
- `"아 근데 똑같이 생긴 블로그 목록이 메인 화면에서도 보여야 해요."`

**1-1단계: 화면을 UI 컴포넌트 단위로 나누고 Vue 컴포넌트 이름 규칙에 맞게 이름 짓기**
- 블로그 제목 - ArticleTitle
- 블로그 목록 - ArticleList
- 최근 블로그글 영역 - LastArticlesSection
- 블로그 글 - ArticlePage


**1-1단계: 위 컴포넌트들을 pages/ 와 components/ 디렉토리 역할에 맞게 넣기**
```
  src
    ├─components
    │      ArticleList.vue
    │      ArticleTitle.vue
    │      LastArticlesSection.vue
    │
    └─pages
            ArticlePage.vue
```

**1-2단계: components/ 밑에 있는 ArticleTitle, ArticleList, LastArticlesSection 역할 구분**

요구 조건을 떠올려보자.

- "블로그 글이 나오는 페이지에는 `블로그 제목`, `블로그 목록`, `최근 블로그글들`을 보여주세요"
- "아 근데 똑같이 생긴 `블로그 목록`이 메인 화면에서도 보여야 해요."

요구 조건에 따라 컴포넌트의 역할을 두가지로 구분할 수 있다.

- ArticleList 컴포넌트는 여러 군데서 재사용할 수 있다.
- ArticleTitle, LastArticlesSection 컴포넌트는 ArticlePage 컴포넌트에서만 쓰인다.
```
  src
    ├─components
    │      ArticleList.vue
    │
    └─pages
            ArticlePage.vue
            ArticleTitle.vue
            LastArticlesSection.vue
```
ArticlePage 단위로 묶자. 그리고 ArticlePage.vue는 index.vue로 이름을 수정한다.

이름을 index.vue로 수정하면 import할 때 pages/ArticlePage/ArticlePage가 아니라 pages/ArticlePage로 줄여쓸 수 있기 때문에 가독성이 좋아진다.
```
  src
    ├─components
    │      ArticleList.vue
    │
    └─pages
        └─ArticlePage
                ArticleTitle.vue
                index.vue
                LastArticlesSection.vue
```

**2단계: domain과 관련된 컴포넌트와 관련없는 컴포넌트로 역할 구분**

앗! 사이트에 Header도 없고 Footer도 없고 사이트에서 공통으로 사용되는 Button과 List 컴포넌트도 필요한데... 만들자.

```
  src
    ├─components
    │      *AppButton.vue
    │      *AppFooter.vue
    │      *AppHeader.vue
    │      *AppList.vue
    │      ArticleList.vue
    │
    └─pages
        └─ArticlePage
                ArticleTitle.vue
                index.vue
                LastArticlesSection.vue
```

**2-1단계: domain과 관련된 컴포넌트와 관련없는 컴포넌트로 역할 구분**

domain과 관련없는 컴포넌트는 어디서든 재사용할 수 있다.
이 컴포넌트들은 다른 컴포넌트들과 props, events를 통해서만 커뮤니케이션할 뿐 어떠한 비즈니스 로직도 가져서는 안된다.

이런 컴포넌트들은 ui/ 디렉토리로 구분
```
  src
    ├─components
    │  │  AppFooter.vue
    │  │  AppHeader.vue
    │  │  ArticleList.vue
    │  │
    │  └─ui
    │          *AppButton.vue
    │          *AppList.vue
    │
    └─pages
        └─ArticlePage
                ArticleTitle.vue
                index.vue
                LastArticlesSection.vue
```

**2-2단계: layout 컴포넌트는 따로 구분**

AppHeader와 AppFooter는 어플리케이션 내에서 오직 한 번만! 사용되는 layout과 관련된 컴포넌트들이다. layout/ 디렉토리로 구분할 수도 있다.
```
  src
    ├─components
    │  │  ArticleList.vue
    │  │
    │  ├─layout
    │  │      *AppFooter.vue
    │  │      *AppHeader.vue
    │  │
    │  └─ui
    │          AppButton.vue
    │          AppList.vue
    │
    └─pages
        └─ArticlePage
                ArticleTitle.vue
                index.vue
                LastArticlesSection.vue
```
**2-3단계: domain과 관련된 컴포넌트도 따로 구분**

ArticleList.vue는 재사용이 가능하기 때문에 pages/ 디렉토리에 Page 컴포넌트 하위에 둘 수 없다. 별도의 디렉토리로 구분한다.
```
  src
    ├─components
    │  │
    │  ├─article
    │  │      ArticleList.vue
    │  │
    │  ├─layout
    │  │      AppFooter.vue
    │  │      AppHeader.vue
    │  │
    │  └─ui
    │          AppButton.vue
    │          AppList.vue
    │
    └─pages
        └─ArticlePage
                ArticleTitle.vue
                index.vue
                LastArticlesSection.vue  
```

(부록)

흠... domain 관련도 없고 ui도 아니고 layout도 아닌 컴포넌트가 있을 수 있다.

utility 성격을 가진 컴포넌트. 이 컴포넌트들은 그 자체로 렌더링을 담당하고 자식 컴포넌트에게 렌더링을 위임하지 않는다.

이런 컴포넌트들은 components/common/ 디렉토리로 구분한다.

## 정리
### 디렉토리 기준
- components/ 재사용 가능한 컴포넌트들
  - domain별 디렉토리
  - ui/ (domain 관련 없이 재사용 가능한 컴포넌트들)
  - layout/ (domain 관련 없이 재사용 가능하지만 어플리케이션 내에서 한 번만 사용되는 컴포넌트)
  - common/ (유틸리티 성격을 가진 컴포넌트)
- pages/ url 단위로 보여지는 Page 단위 컴포넌트
  - page별 디렉토리
    -  index.vue, Page 컴포넌트 안에서만 사용되는 단일 컴포넌트

### 컴포넌트 종류
- domain 컴포넌트
- ui 컴포넌트
- layout 컴포넌트
- page 컴포넌트
- utility 컴포넌트
