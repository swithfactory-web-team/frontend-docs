# ViA

- repo: https://github.com/swithfactory-web-team/via-front
- service: https://www.vrinart.com/

## 1. 사용 언어 및 라이브러리

- typescript + next.js (page router)
- styled-components
- axios
- jotai
- react-hook-form
- react-paginate
- react-slick & slick-carousel 

## 2. 프로젝트 구조

```
/public
  /icons
  /logos
  /images
  /videos
/src
  /components
   /common
   /[domain]
  /pages
   /[domain]
  /apis
  /hooks
  /libs
  /stores
  /styles
```

## 3. 컴포넌트 설계 및 구현

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

## 5. Git 작업 순서

1. 작업하기 전, 작업과 관련된 **Github Issue**를 생성 후 작업 내용, 일정 등을 작성한다.

2. 메인 브랜치로 이동 후, 브랜치를 최신화한다. (다른 브랜치에서 병합된 추가 작업이 있을 수 있기 때문)

   ```bash
   git checkout main
   git pull
   ```
3. 작업을 진행할 브랜치를 새로 생성한다. 이때 브랜치명은 `feature/#[issue-number]-[work-title]` 으로 한다.

   - ex. 로그인 및 회원가입 페이지 작업 (이슈번호 : 9) -> `feature/#9-login-register-page`

4. 해당 브랜치에서 작업을 진행한다. 

5. 작업 완료 후, 각 세부 작업 별로 commit을 해준다. 커밋 메세지는 [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/)를 따른다.

   ```bash
   git commit -am "feat: 로그인 페이지 추가"
   git commit -am "feat: 회원가입 페이지 추가"
   ...
   git push origin [branch-name]
   ```

6. 커밋과 origin에 push까지 완료했다면, **Pull Request**를 생성한다. 

   - PR에 관련 Issue, 작업 내용 등을 기재한다.
   - PR 제목 역시 conventionnal commits를 따른다. (ex. `feat: add login and register page`)

7. Vercel Preview 배포가 성공이 뜨고 코드가 메인에 병합될 준비가 완료되었다면, Reviewers에 팀원을 추가하여 코드 리뷰를 요청한다.

   - 코드를 빠르게 병합해야 하는 경우 리뷰 생략 가능 

8. 팀원으로부터 병합 승인을 받았다면, 메인 브랜치에 **Squash Merge**한다.

   

