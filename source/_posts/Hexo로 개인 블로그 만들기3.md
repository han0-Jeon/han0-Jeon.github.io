---
title: Hexo로 개인 블로그 만들기 (3) - Gitalk 추가
date: 2024/10/17 09:03:12
categories: [블로그만들기]
tags: [Hexo, Blog, Themes, GitHub, GitHub Actions, Github Pages, workflows]
thumbnail: /images/2024/10/17/thumbnail.png
---

댓글 플러그인을 고민하던 중 Disqus는 원하지 않는 광고가 많이 게시된다고 했고,

github pages 로 블로그를 배포한김에 github으로 댓글 관리 까지 하면 통일성도 있고 관리하기 좋겠다 싶어서 gitalk으로 결정했다.

## OAtuh app 가입

우선 OAuth app 에 가입한다.
![](/images/2024/10/17/oauth.png)

- `Application name` : 원하는 이름
- `Homepage URL` : 블로그 URL
- `Application description` : 선택 사항
- `Authorization callback URL` : 리다이렉트될 게시물 주소

만들어지면, Client ID와 Client secret을 받게 된다.<br><br>

## \_config.yml 설정

\_config.yml 파일에 gitalk 부분을 찾아서 Client ID, Client secret를 입력한다.

그리고 나머지 아래 세가지 값만 제대로 넣으면 된다.

```yaml
enable: true
github_id: han0-Jeon
repo: han0-Jeon.github.io
```

- `github_id` : 본인 GitHub 아이디
- `repo` : 블로그 레포지토리

이후 블로그로 돌아가보면 아래와 같은 화면이 뜬다.

![](/images/2024/10/17/gitlogin.png)

근데 주의할점은 꼭 배포를 하고 확인해봐야한다. [localhost](http://localhost) 에서 테스트 해보다가 리다이렉트 주소가 잘못됬다길래 한참 삽질했다.

## 테스트

`Login with GitHub` 를 눌러서 로그인 하면 댓글기능이 잘 나타나진다.
![](/images/2024/10/17/gitalk.png)<br><br>

테스트로 댓글을 적어보면, 댓글이 잘 등록되고, GitHub Issues 에서도 확인이 가능하다.
![](/images/2024/10/17/gitalktest.png)<br><br>

당연하지만(?) GitHub Issues 에서 댓글을 달아도 블로그에 잘 연동이 된다.
![](/images/2024/10/17/gitissue.png)<br><br>

MarkDown 문법도 지원해서 쓸만 한 것 같다!
![](/images/2024/10/17/markdown.png)<br><br>
