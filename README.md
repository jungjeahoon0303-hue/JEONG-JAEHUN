# KYO: Selected Works — Portfolio

---

## 새 프로젝트 추가 방법

### 1. 프로젝트 상세 페이지 만들기

`projects/project-001.html`을 복사해서 `projects/project-002.html`로 저장하세요.

```bash
cp projects/project-001.html projects/project-002.html
```

`projects/project-002.html`을 열고 아래 항목을 수정하세요.

- `<title>` — 프로젝트 이름으로 변경
- `.post-tag` — 번호/카테고리 변경 (예: `Project · 002`)
- `.post-title` — 프로젝트 제목 변경
- `.post-meta` 안의 Location, Year, Type 값 변경
- `<article class="post-body">` 안의 본문 내용 변경
- 이미지 경로 변경 (`../images/...` 형식 유지)

---

### 2. works.html에 새 카드 추가하기

`works.html`의 `.works-grid` 안에 아래 카드 블록을 복사해서 붙여 넣으세요.

```html
<!-- Project 002 -->
<a class="works-item" href="projects/project-002.html">
  <div class="works-item-media">
    <img src="images/works/project-002-cover.jpg" alt="Project 002 제목" />
  </div>
  <div class="works-item-meta">
    <div class="works-item-title">Project 002 — 두 번째 작업</div>
  </div>
</a>
```

이미지 파일은 `images/works/` 폴더에 넣고 `src` 경로를 맞춰주세요.

---

### 3. index.html의 featured 썸네일을 최신 프로젝트로 교체하기

메인 페이지(`index.html`)의 featured 섹션은 가장 최근 프로젝트 한 장을 전면에 보여줍니다.
새 프로젝트를 추가했다면 아래 부분을 수정해 최신 작업으로 교체하세요.

```html
<!-- index.html — #page-works 안의 featured 섹션 -->
<section class="featured">
  <a href="projects/project-002.html">   <!-- 링크를 최신 프로젝트로 변경 -->
    <div class="featured-media">
      <img src="images/works/project-002-cover.jpg" alt="" />  <!-- 이미지 경로 변경 -->
    </div>
    <div class="meta-line">
      <span class="credit">c Photographer Name</span>
      <span class="tag">Project</span>
      <span class="title">Project 002 — 두 번째 작업</span>   <!-- 제목 변경 -->
      <span class="sub">Seoul, South Korea</span>
    </div>
  </a>
</section>
```

---

정적 HTML/CSS 포트폴리오 사이트입니다. 별도 빌드 도구 없이 브라우저에서 바로 열거나, 정적 호스팅 서비스(GitHub Pages, Netlify, Vercel 등)에 그대로 배포할 수 있습니다.

---

## 폴더 구조

```
kyo-portfolio/
├── index.html              # 메인 페이지
├── styles.css              # 모든 스타일
├── fonts/
│   ├── HelveticaCompressed.ttf
│   └── HelveticaCondensed.ttf
├── images/
│   ├── works/              # 프로젝트 이미지
│   └── about/              # 프로필/소개 이미지
└── README.md
```

---

## 사진 추가하는 방법

### 1. 파일 넣기

사진 파일을 알맞은 폴더에 넣으세요.

| 용도 | 폴더 |
|------|------|
| Works 페이지 프로젝트 이미지 | `images/works/` |
| About 페이지 프로필 사진 | `images/about/` |

**권장 파일명 예시:**
```
images/works/project-001-cover.jpg
images/works/project-001-gallery-1.jpg
images/works/project-001-gallery-2.jpg
images/about/profile.jpg
```

**권장 사양:**
- 형식: JPG (사진), PNG (투명 배경이 필요한 경우)
- 커버/히어로 이미지: 1600×900px 이상, 가로형
- 갤러리 이미지: 800×1000px 이상, 세로형(4:5 비율)
- 파일 크기: 장당 500KB 이하 권장 (웹 최적화)

---

### 2. index.html에서 이미지 경로 교체

`index.html`을 열고 현재 임시 이미지(`https://picsum.photos/...`)를 실제 파일 경로로 바꾸세요.

**Works 페이지 커버 이미지:**
```html
<!-- 변경 전 -->
<img src="https://picsum.photos/seed/featured1/1600/900" alt="" />

<!-- 변경 후 -->
<img src="images/works/project-001-cover.jpg" alt="Project 001 커버" />
```

**Post 상세 페이지 히어로 이미지:**
```html
<!-- 변경 전 -->
<img src="https://picsum.photos/seed/featured1/1600/900" alt="" />

<!-- 변경 후 -->
<img src="images/works/project-001-cover.jpg" alt="Project 001" />
```

**Post 갤러리 이미지 (2장):**
```html
<!-- 변경 전 -->
<img src="https://picsum.photos/seed/g1/800/1000" alt="" />
<img src="https://picsum.photos/seed/g2/800/1000" alt="" />

<!-- 변경 후 -->
<img src="images/works/project-001-gallery-1.jpg" alt="" />
<img src="images/works/project-001-gallery-2.jpg" alt="" />
```

---

### 3. 프로젝트 여러 개 추가하기

현재 Works 페이지는 프로젝트 1개만 표시합니다. 프로젝트를 추가하려면 `index.html`의 `#page-works` 섹션 안에 `<section class="featured">` 블록을 복사해서 붙여 넣으세요.

각 프로젝트마다 `data-page` 값을 다르게 줘서 별도 상세 페이지로 연결할 수 있습니다:

```html
<!-- Works 목록에 두 번째 프로젝트 추가 -->
<section class="featured">
  <a data-page="post-2">
    <div class="featured-media">
      <img src="images/works/project-002-cover.jpg" alt="" />
    </div>
    <div class="meta-line">
      <span class="tag">Project</span>
      <span class="title">Project 002 — 두 번째 작업</span>
      <span class="sub">Seoul, South Korea</span>
    </div>
  </a>
</section>
```

그리고 `#page-post`를 복사해서 `id="page-post-2"`로 만들면 됩니다.

---

## 배포 방법

### GitHub Pages
1. 이 폴더를 GitHub 저장소로 push
2. Settings → Pages → Branch: `main`, folder: `/ (root)` 선택
3. 자동으로 `https://username.github.io/repo-name` 에 배포됨

### Netlify / Vercel
1. 저장소를 연결하거나 폴더를 드래그 앤 드롭으로 업로드
2. Build command: 없음 (빈칸)
3. Publish directory: `/` (루트)

---

## 로컬에서 미리보기

터미널에서 이 폴더로 이동 후:

```bash
# Python 3
python3 -m http.server 8080
```

브라우저에서 `http://localhost:8080` 열기.

> `index.html`을 파일 탐색기에서 더블클릭하면 폰트 로딩이 안 될 수 있습니다. 로컬 서버를 통해 여는 것을 권장합니다.
