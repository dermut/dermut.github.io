# 블로그 운영 가이드

> **용기와 꿈** — dermut의 Jekyll 블로그 (Minimal Mistakes 테마)

---

## 목차

1. [프로젝트 구조](#1-프로젝트-구조)
2. [포스트 작성하기](#2-포스트-작성하기)
3. [카테고리와 태그](#3-카테고리와-태그)
4. [레이아웃 종류](#4-레이아웃-종류)
5. [페이지 추가하기](#5-페이지-추가하기)
6. [네비게이션 수정](#6-네비게이션-수정)
7. [저자 프로필 설정](#7-저자-프로필-설정)
8. [테마 스킨 변경](#8-테마-스킨-변경)
9. [댓글 설정](#9-댓글-설정)
10. [소셜 공유 버튼](#10-소셜-공유-버튼)
11. [배포 (GitHub Pages)](#11-배포-github-pages)

---

## 1. 프로젝트 구조

```
dermut.github.io/
│
├── _config.yml          # 블로그 전체 설정 (가장 중요)
│
├── _posts/              # 블로그 포스트 (실제 글)
│   └── YYYY-MM-DD-제목.md
│
├── _pages/              # 고정 페이지
│   ├── about.md         # 소개 페이지
│   ├── games.md         # 게임 페이지
│   ├── posts.md         # 포스트 아카이브
│   └── category-archive.md  # 카테고리 아카이브
│
├── _data/
│   ├── navigation.yml   # 상단 메뉴 구성
│   └── ui-text.yml      # 다국어 UI 텍스트
│
├── _includes/           # 재사용 HTML 컴포넌트 (수정 주의)
│   └── social-share.html    # 소셜 공유 버튼
│
├── _layouts/            # 페이지 레이아웃 템플릿 (수정 주의)
│
├── _sass/               # 스타일시트 소스
│   └── minimal-mistakes/
│       ├── _variables.scss  # 색상·폰트 변수
│       ├── _buttons.scss    # 버튼 스타일
│       └── skins/           # 테마 스킨
│
└── assets/
    ├── css/main.scss    # 전체 CSS 진입점
    ├── image/           # 블로그에서 사용하는 이미지
    └── js/              # JavaScript 파일
```

---

## 2. 포스트 작성하기

### 파일명 규칙

```
_posts/YYYY-MM-DD-제목.md
```

예: `_posts/2024-06-01-Python-기초.md`

### Front Matter (필수 헤더)

포스트 최상단에 `---`로 감싼 YAML 블록을 반드시 작성해야 합니다.

```yaml
---
title: "포스트 제목"
date: 2024-06-01
categories:
  - 개발
tags:
  - Python
  - 입문
excerpt: "포스트 요약 (목록에서 미리보기로 표시)"
header:
  image: /assets/image/header.jpg   # 상단 헤더 이미지 (선택)
  teaser: /assets/image/thumb.jpg   # 목록 썸네일 (선택)
---
```

### 기본 제공 Front Matter 옵션

| 옵션 | 기본값 | 설명 |
|------|--------|------|
| `layout` | `single` | 레이아웃 (기본 적용, 생략 가능) |
| `author_profile` | `true` | 왼쪽 저자 프로필 표시 |
| `read_time` | `true` | 읽기 시간 표시 |
| `comments` | `false` | 댓글 활성화 |
| `share` | `true` | 소셜 공유 버튼 표시 |
| `related` | `true` | 하단 관련 글 표시 |
| `toc` | `false` | 목차(Table of Contents) 표시 |
| `toc_sticky` | `false` | 목차 스크롤 고정 |

### 목차 사용 예시

```yaml
---
title: "긴 포스트 제목"
toc: true
toc_sticky: true   # 스크롤해도 목차가 화면에 고정
---

## 섹션 1
내용...

## 섹션 2
내용...
```

---

## 3. 카테고리와 태그

### 권장 구조

```yaml
categories:
  - 개발          # 큰 주제 분류 (1~2개 권장)
tags:
  - Python        # 세부 키워드 (여러 개 가능)
  - 알고리즘
  - 입문
```

### 카테고리 아카이브

- 주소: `https://dermut.github.io/categories/`
- 각 카테고리별 포스트 목록 자동 생성
- `_pages/category-archive.md`가 이 페이지를 담당

### 태그 아카이브

- 주소: `https://dermut.github.io/tags/`
- 태그 아카이브 페이지를 추가하려면 `_pages/`에 아래 파일 생성:

```yaml
# _pages/tag-archive.md
---
title: "Tag"
layout: tags
permalink: /tags/
---
```

### URL 구조

`_config.yml`의 `permalink: /:categories/:title/` 설정으로
카테고리가 URL에 포함됩니다.

예: `https://dermut.github.io/개발/Python-기초/`

---

## 4. 레이아웃 종류

| 레이아웃 | 용도 |
|----------|------|
| `single` | 일반 포스트/페이지 (기본) |
| `posts` | 포스트 전체 목록 아카이브 |
| `categories` | 카테고리별 아카이브 목록 |
| `tags` | 태그별 아카이브 목록 |
| `splash` | 히어로 이미지가 있는 랜딩 페이지 |
| `home` | 최신 포스트 피드 (페이지네이션 지원) |

### splash 레이아웃 예시 (games.md에서 사용 중)

```yaml
---
title: "페이지 제목"
layout: splash
permalink: /example/
header:
  overlay_image: /assets/image/background.jpg
  overlay_color: "#333"
  overlay_filter: 0.5
---
```

---

## 5. 페이지 추가하기

`_pages/` 폴더에 `.md` 파일을 생성합니다.

```yaml
# _pages/new-page.md
---
title: "새 페이지"
layout: single
permalink: /new-page/
author_profile: true
---

페이지 내용을 여기에 작성합니다.
```

생성 후 `_data/navigation.yml`에 메뉴 항목을 추가하면 상단 네비게이션에 표시됩니다.

---

## 6. 네비게이션 수정

`_data/navigation.yml`에서 상단 메뉴를 관리합니다.

```yaml
# _data/navigation.yml
main:
  - title: "POST"
    url: /post/
  - title: "CATEGORY"
    url: /categories/
  - title: "GAMES"
    url: /games/
  - title: "ABOUT"
    url: /about/
```

드롭다운 메뉴도 지원합니다:

```yaml
main:
  - title: "개발"
    children:
      - title: "Python"
        url: /categories/python/
      - title: "JavaScript"
        url: /categories/javascript/
```

---

## 7. 저자 프로필 설정

`_config.yml`의 `author` 섹션에서 수정합니다.

```yaml
author:
  name: "dermut😄️"
  bio: "I am a **programmer**."
  location: "Yongin-si, Republic of Korea"
  avatar: "/assets/image/profile.jpg"   # 프로필 사진 경로
  links:
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/dermut"
    - label: "Instagram"
      icon: "fab fa-fw fa-instagram"
      url: "https://instagram.com/아이디"
```

사용 가능한 Font Awesome 6 아이콘: [https://fontawesome.com/icons](https://fontawesome.com/icons)

---

## 8. 테마 스킨 변경

`_config.yml` 상단에서 변경합니다.

```yaml
minimal_mistakes_skin: "default"
```

| 스킨 | 특징 |
|------|------|
| `default` | 회색 계열 기본 |
| `air` | 밝고 깔끔한 파란 계열 |
| `aqua` | 청록색 계열 |
| `contrast` | 고대비 흑백 |
| `dark` | 다크 모드 |
| `dirt` | 브라운 계열 |
| `mint` | 민트 계열 |
| `neon` | 네온 컬러 |
| `plum` | 보라색 계열 |
| `sunrise` | 오렌지·빨강 계열 |

### 색상 직접 커스터마이징

`_sass/minimal-mistakes/_variables.scss`에서 `$primary-color` 등 변수를 수정합니다.

---

## 9. 댓글 설정

현재 댓글은 비활성화 상태입니다. `_config.yml`에서 활성화할 수 있습니다.

```yaml
comments:
  provider: "disqus"   # 또는 "giscus"
  disqus:
    shortname: "dermut-log"
```

활성화 후 특정 포스트에만 댓글 허용:

```yaml
# 포스트 front matter
---
comments: true
---
```

---

## 10. 소셜 공유 버튼

현재 **Threads, X, LinkedIn** 버튼이 설정되어 있습니다.
`_includes/social-share.html`에서 수정할 수 있습니다.

포스트별로 공유 버튼 숨기기:

```yaml
---
share: false
---
```

---

## 11. 배포 (GitHub Pages)

포스트나 파일을 수정한 후 아래 명령으로 배포합니다.

```bash
git add .
git commit -m "커밋 메시지"
git push
```

GitHub Actions가 자동으로 빌드하여 `https://dermut.github.io`에 반영됩니다.
반영까지 보통 1~2분 소요됩니다.

---

> 테마 공식 문서: [https://mmistakes.github.io/minimal-mistakes/](https://mmistakes.github.io/minimal-mistakes/)
