# saegim.life

> Saegim 브랜드 페이지: "삶을 새기다", Saegim이 만드는 서비스를 모아 보여 주고 각 서비스로 연결

## 주요 기능

- 서비스 목록: career(웹 서비스), BlogAutoMate(Windows 앱 내려받기)로 이동
- 문의하기(`contact.html`): career 서버의 문의 API로 보내 운영자 화면 「받은 문의」에 쌓임
- 밝게/어둡게는 시스템 설정을 따름

## 기술 스택

| 구분 | 사용 기술 |
| --- | --- |
| Frontend | 정적 HTML, CSS (빌드 도구 없음) |
| 글꼴 | Noto Serif KR 400, 700 (`fonts/`에 직접 담음, OFL 1.1) |
| Infra | GitHub Pages, 사용자 지정 도메인 `saegim.life` |

## 시작하기

빌드 없이 `index.html`을 브라우저로 열면 됨

- 문의 보내기는 `https://saegim.life`에서만 동작 (career 서버가 이 출처만 허용, 로컬 파일로 열면 거절)

## 프로젝트 구조

```text
.
├── index.html     # 브랜드 페이지
├── contact.html   # 문의하기
├── style.css      # 두 페이지 공통 스타일
├── fonts/         # Noto Serif KR (글자 범위별 woff2와 @font-face)
├── logo.svg       # 로고, 파비콘
├── logo-512.png   # 홈 화면 아이콘, 링크 미리보기 그림
└── CNAME          # GitHub Pages 사용자 지정 도메인
```

## 서비스 추가

- `index.html`의 `<ul class="list">`에서 `<li>` 하나 복사해 번호, 이름, 종류, 설명, 주소 수정
- 목록 제목의 개수(`.count span`), 하단 서비스 목록, `contact.html`의 문의 대상(`<select>`)도 함께 수정
- 문의 대상을 늘리면 career 서버 `ContactIn.topic` 허용 값도 함께 추가 (gyeomii/career.saegim.life)

## 개발 규칙

- 공통 지침: [AGENTS.md](AGENTS.md)
- 브랜치: `<conventional commit prefix>/<영문 소문자 작업 요약>` (예: `feat/user-search`)
- 커밋: conventional commit 형식, 설명은 한국어 개조식

## 배포

- `main`에 push하면 GitHub Pages가 그대로 배포
- DNS(Gabia): `saegim.life` A 레코드 4개를 GitHub Pages IP로, `www` CNAME을 `gyeomii.github.io`로
