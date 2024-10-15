---
title: Hexo로 개인 블로그 만들기 (1)
date: 2024/10/10 10:03:12
categories: 블로그만들기
---

본 포스팅에서는 Hexo 설치 부터 테마 적용, GitHub Pages 배포 까지 진행하겠습니다.

## Hexo 설치

우선, node와 npm이 설치되어있어야 합니다.
<br>
아래는 사용한 버전입니다.
`node: 20.16.0` `npm: 10.8.1`
![](/images/2024-10-10/nodenpm.png)

node 설치가 완료되면, 사용하고자 하는 폴더에서 Hexo 설치 합니다.

```bash
$ npm install -g hexo-cli
```

<br>
동일한 폴더에서 디렉토리를 생성합니다.

```bash
$ hexo init (디렉토리 명)
```

![](/images/2024-10-10/hexoinit.png)
<br>

이후 생성된 폴더로 이동해서 필요한 패키지들을 설치합니다.

```bash
$ cd (디렉토리 명)
$ npm install
```

<br>
설치가 완료되면, 정상적으로 설치되었는지 확인해봅니다.

```bash
$ hexo clean; hexo generate; hexo server;
```

<br>

정상적으로 설치 되었다면, `localhost:4000`접속 시 아래와 같은 화면이 나타납니다.
![](/images/2024-10-10/firsthexo.png)
<br>

## Hexo 테마 적용

테마는 아래 페이지에서 찾아서 사용합니다.

**Hexo Themes** : https://hexo.io/themes/

저는 Next 테마를 사용해서 진행하겠습니다.
테마 설치에는 두 가지 방법이 있는데(`npm`, `git`), 포스팅에서는 `npm` 을 사용합니다.

```bash
$ npm install hexo-theme-next@latest
```

<br>

설치 완료되면 `node_modules/hexo-theme-next/` 경로에 있는 `_config.yml` 파일을 복사해서
루트 디렉토리에 `_config.next.yml` 파일로 붙여넣기 합니다.

```bash
$ cp node_modules/hexo-theme-next/_config.yml _config.next.yml
```

<br>

다른 문서에서는 기본 테마 설정 파일을 직접 수정하라고 제안할 수 있지만, 이 방법은 **업데이트 시 충돌이 발생할 수 있는 위험**이 있습니다. _(예를 들어, NexT 테마를 git으로 업데이트할 때 설정이 덮어씌워지는 경우)_ <br>
따라서 **\_config.next.yml** 파일을 사용하는 것이 좋습니다.
이 방식은 테마를 안전하게 업데이트하면서도 사용자 정의 설정을 유지할 수 있습니다.
<br>

theme 를 next로 변경해줍니다.

    theme: next

이후, 아래 명령어를 입력하면 테마가 바뀐 것을 확인 할 수 있습니다.

```bash
$ hexo generate; hexo server;
```

![](/images/2024-10-10/nexthexo.png)
<br>

## GitHub Pages 배포

`hexo deploy` 같은 명령어 없이, push만 해도 자동으로 배포가 되도록 설정합니다.

우선, GitHub Pages에 배포할 것이기 때문에 레포를 만들어줍니다.
레포 이름은 `(github아이디).github.io` 으로 합니다.
![](/images/2024-10-10/githubrepo.png)

생성이 완료 되었으면, `Settings -> Pages`로 들어가서 Build and Deployment를 GitHub Actions 로 변경해줍니다.
![](/images/2024-10-10/githubaction.png)<br>

VSCode를 열고 터미널에 아래 명령어를 입력해서 로컬 저장소와 git 레포를 연결합니다.

```bash
$ git init
$ git add .
$ git commit -m "메시지"
$ git branch -M main
$ git remote add origin (깃헙 레포)
$ git push -u origin main
```

<br>

이후 빈 파일을 하나 생성하고 `.github/worksflows/hexo.yaml`

아래 yaml 파일을 붙여넣습니다. (저는 주석 부분만 수정하였습니다.)

_.github/workflows/hexo.yaml_

```yaml
name: Deploy Hexo site to Pages

on:
  push:
    branches: [$default-branch] # 사용하는 브랜치 명

  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

defaults:
  run:
    shell: bash

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
        with:
          submodules: recursive
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v3
      - name: Use Node.js 18.x # 사용하는 node 버전
        uses: actions/setup-node@v3
        with:
          node-version: "18" # 사용하는 node 버전
      - name: Install Dependencies
        run: npm install
      - name: Build with Hexo
        run: npx hexo g
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v1
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }} # GitHub Repo 주소
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v2
```

<br>

그리고, 저는 기본 테마를 변경해주기 위해 아래와 같이 수정했습니다.
![](/images/2024-10-10/scheme.png)

이후 `soruce/_posts/` 에 새로운 md 파일을 만들어줍니다. (새로운 게시물)
![](/images/2024-10-10/firstpost.png)

완료 후, push를 하면 아래와 같이 정상적으로 배포가 된 것을 확인할 수 있습니다.
![](/images/2024-10-10/workflowhexo.png)

이상 끝 -!
<br>
<br>
<br>

**_참고 및 인용_**
https://hexo.io/docs/
https://theme-next.js.org/
