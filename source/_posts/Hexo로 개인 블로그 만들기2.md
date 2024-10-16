---
title: Hexo로 개인 블로그 만들기 (2) - 커스터마이징
date: 2024/10/16 15:03:12
categories: [블로그만들기]
tags: [Hexo, Blog, Themes, GitHub, GitHub Actions, Github Pages, workflows]
---

## 커스터 마이징 준비

모든 게시물들을 스크롤로 간략하게(제목, 섬네일) 보여줄 수 있는 기능이 있었으면 좋겠다고 생각했다. (티스토리 or 벨로그 같이)<br><br>

![](/images/2024-10-16/custom.png)
next 공식 문서에서 커스터마이징 방법을 제공하긴 했지만, `source/\_data`폴더를 사용해서 `head, header, footer, post-body ..` 등등 매우 제한적 이었고 내가 원하는 건 이게 아니었다.

우선 내가 원하는 대로 커스터마이징을 하려면 `node_moudules` 를 건드려야 했다. _(npm으로 설치했기 때문)_
하지만 파일 관리가 어려울 것 같고 `node_modules`를 건드리는게 뭔가 좀 이상(?)해서 `git clone` 방식으로 next 테마를 재설치 했다.

아래 순서대로 진행했다.

1. `node_modules` 폴더 삭제
2. `packge.json` 파일에서 next 설치 된 부분 삭제 _(아마 hexo-theme-next일 것이다.)_
3. `npm install` _(next 테마 설치 전 상태로 의존성 재설치)_
4. `themes` 폴더에 next라는 이름으로 `git clone`

```bash
git clone https://github.com/next-theme/hexo-theme-next themes/next
```

![](/images/2024-10-16/gitclone.png)

5. `.git` 파일 삭제 _(딱히 필요없음)_
6. 푸쉬(재배포) 후 문제 없는 것 확인
   <br><br>

## 페이지 만들기

터미널 열고 아래 명령어 입력, 원하는 폴더명을 사용한다.

```bash
hexo new page allposts
```

생성된 `allposts/index.md` 파일에 아래와 같이 layout을 추가한다.

```
title: allposts
date: 2024-10-15 15:53:12
layout: allposts
```

<br><br>

## 메뉴 만들기

`_config.next.yml` 파일을 수정한다. 편의상 메뉴는 한글로 변경했다.
`"모든 게시물": /allposts/ || fa fa-list` 이 부분이 추가됬다.

```yaml
menu:
  "홈": / || fa fa-home
  "모든 게시물": /allposts/ || fa fa-list
  #about: /about/ || fa fa-user
  "태그": /tags/ || fa fa-tags
  "카테고리": /categories/ || fa fa-th
  "기록 보관소": /archives/ || fa fa-archive
```

이후 `_config.yml` 파일도 수정한다.
`allposts_dir: allposts` 추가

```yaml
# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
allposts_dir: allposts
```

<br><br>

## 본격 커스터마이징

이후 아까 클론한 `themes` 폴더를 만져야 한다.
`themes` 폴더 구성을 보면 아래 이미지와 같이 되어 있다.

![](/images/2024-10-16/theme.png)<br><br>

우선 여기서 건드려야 할 건, `layout` 폴더와 `source`폴더이다.

하기 전에, extensions 설치하면 보기 편하다.

![](/images/2024-10-16/nunjucks.png)

![](/images/2024-10-16/stylus.png)

layout 폴더에 파일을 하나 생성한다. `allposts.njk` _(파일명은 아까 만든 페이지와 동일하도록 작성)_

![](/images/2024-10-16/layout.png)

njk 문법은 처음이라 다른 파일 참고해가면서 원하는 레이아웃 구성으로 코딩해준다.

css를 입히기 위해 source 폴더에도 파일을 생성해준다. `allposts.css`

![](/images/2024-10-16/source.png)

원하는 스타일에 맞게 스타일링 해준다.

이후 `layout/_partials/head/head.njk` 파일로 가서 아래 코드를 추가해준다.

```js
<link rel="stylesheet" href="{{ url_for('css/custom/allposts.css') }}">
```

![](/images/2024-10-16/link.png)

여기까지 하면 기본적인 세팅은 완료이다.

아래는 완성된 결과물이다.

![](/images/2024-10-16/result.png)

이상 끝 -!
