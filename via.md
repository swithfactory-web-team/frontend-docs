# ViA

> ⚠️ 현재 via 프론트엔드 소스 코드는 [해당 PR](https://github.com/swithfactory-web-team/via-front/pull/1) 에서 전체 리팩토링 중에 있습니다.

## 1. 사용 언어 및 라이브러리

- typescript + next.js (page router)
- styled-components
- jotai
- react-quill
- react-slick
- slick-carousel
- react-paginate
- react-unity-webgl

## 2. 프로젝트 구조

```
/public
  /icons
  /logos
  /fonts
  /unity
   /MobileUnityBuild
   /PCUnityBuild
/src
  /constants
  /stores
  /styles
  /components
   /common
   /[domain]
  /pages
   /[domain]
```

## 3. 컴포넌트 설계 및 구현

### 구조

현재 via의 컴포넌트 구조는 [Atomic Design Pattern](https://fe-developers.kakaoent.com/2022/220505-how-page-part-use-atomic-design-system/)에 기반하여 설계되어 있습니다.

- 각 페이지는 하나의 Template 컴포넌트를 가지고 있고, Template 내부에서 여러 컴포넌트를 조합하여 UI를 구성합니다.
  - ex. `pages/login.tsx` 은 비즈니스 로직을 담당하고, `LoginTemplate` 은 로그인 페이지의 UI 렌더링을 담당
- 여러 도메인에서 사용되는 컴포넌트는 `components/common` 에 위치합니다.
  - ex. `StyledText`, `StyledButton`, `NavigationBar`
- 특정 도메인에서 사용되는 컴포넌트는 `components/[domain]` 에 위치합니다.
  - ex. 마이페이지에서 사용되는 `MyInfoContent` 컴포넌트는 `components/mypage` 내 위치

### 디렉토리 구조

```
[component]/
  index.ts
  [component].tsx
  [component].styles.tsx
  [local_component].tsx
  [local_component].styles.tsx
```

## 4. 주요 설정

### 아이콘 추가

아이콘 svg 파일을 리액트 컴포넌트화하여 사용하기 위해 `@svgr/webpack` 라이브러리를 사용하고 있습니다.

1. `public/icons` 폴더에 아이콘 파일을 추가한다.
2. `public/icons/index.ts` 파일에서 다음과 같이 설정해준다. (아이콘 컴포넌트를 좀 더 편리하게 import하기 위한 설정)

```tsx
import SampleIcon from './sample.svg';

export {
  // ...
  SampleIcon,
};
```

3. 이후 아이콘을 사용하고자 하는 컴포넌트에서 다음과 같이 아이콘 컴포넌트를 사용할 수 있다.

```tsx
import { SampleIcon } from 'public/icons';

const SampleComponent = () => (
  <div>
    <SampleIcon />
  </div>
);
```

> 로고 파일도 동일하게 설정 및 사용해주시면 됩니다. (폴더명은 `public/logos`)

### UI 구성

1. 각 페이지는 해당 페이지의 Template 컴포넌트만을 import하여 렌더링합니다.

```tsx
import SampleTemplate from '@/components/sample/SampleTemplate';

// pages/sample.tsx
const SamplePage = () => <SampleTemplate />;
```

2. 모든 Template 컴포넌트 내부에서는 `Layout` 컴포넌트를 불러와 감싸고 있다.

```tsx
import * as styles from './SampleTemplate.styles';

const SampleTemplate = () => (
  <Layout>
    <styles.Content>템플릿 내용</styles.Content>
  </Layout>
);

export default SampleTemplate;
```

- `Layout` 은 대부분의 페이지에서 공통적으로 보여지는 `NavigationBar` 와 `Footer` 컴포넌트 렌더링을 담당합니다.
- 로그인 및 회원가입 등 `NavigationBar` 가 필요 없는 페이지인 경우 제외됩니다.

3. Template 컴포넌트에서 필요한 컴포넌트들을 조합합니다.

### Unity WebGL 관련

> 작성중...
