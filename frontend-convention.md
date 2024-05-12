# Frontend Convention

## 1. Git Convention

### Commit Message 

- 커밋 메세지 컨벤션은 [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)을 채택하여 사용하고 있습니다. 
- 커밋에 대한 설명은 한글로 작성해주셔도 좋습니다. (ex. `feat: 네비게이션바 컴포넌트 생성`)
- `main` 브랜치에 PR 커밋이 아닌 단일 커밋을 날려야하는 경우 `fix` 가 아닌 `hotfix` 를 사용해주세요.
  - ⚠️ 정말 급한 작업이 아니라면 `main` 브랜치에 단일 커밋을 날리는 걸 지양하는 것이 좋습니다!

### Branch

현재 스위드팩토리 프론트엔드 팀에서는 **Github Flow 전략**을 채택하여 사용하고 있습니다.

- `main` : 배포용 브랜치로, <u>실제 서비스하고 있는 버전</u>으로 유지합니다. 
  - ⚠️ 사용되지 않거나 연습용 코드는 포함되지 않는 것이 원칙입니다!
- `feature` : `main`에 기반하여 하나의 기능을 구현하는 브랜치로, 개발이 완료되면 소스 코드를 `main`에 합칩니다. 
  - ex. `feature/kakao-login`
- `hotfix` : `main`에 기반하여 급하게 수정해야 하는 작업을 위한 브랜치로, 수정이 끝나면 소스 코드를 `main`에 합칩니다.
  - ex. `hotfix/fix-login-error`

### Flow

1. `main`에서 `feature` 브랜치를 생성합니다.
2. `feature` 브랜치에서 신규 기능 작업 완료 후, PR을 날리고 코드 리뷰를 받습니다.
3. `main` 브랜치에 squash merge 후, 해당 `feature` 브랜치를 삭제합니다.
4. hotfix issue가 발생한 경우, `main` 에서 `hotfix` 브랜치를 생성 후, 작업이 끝나면 PR 날리고 `main` 브랜치에 squash merge 합니다.

### Pull Request

- 제목은 커밋 컨벤션에 맞추어 작성합니다.
- 작업 내용 및 관련 안내 사항을 간단하게 작성해주세요.
- 아직 작업 중이지만 중간 리뷰 등의 이유로 미리 날린 PR의 경우 Draft로 설정합니다.

## 2. Coding Convention

### 네이밍

- camelCase: 변수, 함수, parameter, property, method
- PascalCase: 컴포넌트, 클래스, type, interface, enum, type parameter (ex. `Array<T>` 의 `T`)
- kebab-case: 파일명 (ex. `via-logo.svg`)
- SNAKE_CASE: 절대 변하지 않는 상수값

### 규칙

- `var` 이 아닌 `const` 와 `let` 을 사용하여 변수를 선언합니다.
- `boolean` 타입의 변수에는 `is` , `can` 등 접두사를 붙입니다.
- custom hook은 `use` 접두사를 붙입니다.

### 관련 툴

- Eslint
- Prettier

### 컴포넌트 디렉토리 구조

```
[component_name]/
  index.ts
  [component_name].tsx
  [component_name].style.tsx
  [component_name].stories.tsx
  [local_component_name]/*
```

- 컴포넌트 이름으로 폴더를 생성하고, `index.ts`로 쉽게 import할 수 있도록 합니다.
- 특정 컴포넌트 내부에서만 사용하는 컴포넌트는 해당 컴포넌트 내부에서 정의합니다.
- (Storybook 사용시) 컴포넌트에 대한 스토리 파일은 해당 컴포넌트 폴더에 정의합니다.

