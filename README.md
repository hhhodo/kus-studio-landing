# Kus—Studio by Mike Kus — 랜딩페이지

**Live: https://hhhodo.github.io/kus-studio-landing/**

[mikekus.com](https://mikekus.com/)의 실제 카피(히어로 문구, 프로젝트 목록, 서비스, 클라이언트 추천글, 푸터)를
그대로 참고해 재구성한 단일 페이지 랜딩페이지입니다. `styles.css`(디자인 토큰)와 `CHEATSHEET_16.md`
(작성용 단일 참조 요약)의 규칙을 그대로 따랐습니다.

## 이번 변주(Variant) 설정

첫 줄 코드 주석: `<!-- variant: typo=loud / image=높음 / color=accent / radius=sharp / border=outlined -->`

| 축 | 값 | 근거 |
|---|---|---|
| 타이포그래피 태도 | `loud` | "bored of blending in"이라는 단정적 브랜드 선언 — 히어로 `display-md`, 섹션 헤드라인 `h0` |
| 이미지 비중 | `높음` | 포트폴리오 사이트 특성상 프로젝트 4개(Just Phil / Slashwork / Epic Travel / MIXD) 썸네일이 콘텐츠의 핵심. 히어로 비주얼·워크 그리드는 `.container` 밖 풀블리드 |
| 섹션 너비 | 2단계만 사용 | 풀블리드(`.container` 없음, 히어로 비주얼·워크 그리드·다크 CTA 배경)와 기본 `.container`(1440px, 그 외 전 섹션) 딱 둘만 — 1280/1600 같은 중간 폭을 섞으면 섹션마다 폭이 들쭉날쭉해 보여서 통일함 |
| 컬러 모드 | `accent` | mikekus.com 실제 CSS(`--framer-link-text-color:#09f`, 아이콘 마스크 `#06f`)에서 추출한 블루를 브랜드 컬러로 채택. `--color-brand:#0066ff` 등 토큰을 `:root` 상단에 추가하고 칩·CTA 버튼·hover·이미지 프레임 라인에만 사용 — 본문/헤드라인 텍스트는 계속 그레이스케일 |
| 라운드 | `sharp` | 모서리 전부 각짐(`--radius-0`) — 자신감 있고 엄격한 브랜딩 스튜디오 무드 |
| 보더 | `outlined` | 구조 구분선은 `--border-1`(중립), 이미지 프레임·카드는 브랜드 라인(`--color-brand-line`), CTA는 브랜드 배경 — 정교하게 구획된 그래픽 디자인 스튜디오 인상 |

## 원본과의 차이

사용자 요청에 따라 **페이지 이동처럼 보이는 버튼을 전부 제거**했습니다:
- 캐러셀/페이지네이션/이전·다음 버튼 없음
- 히어로의 "View our Work" 버튼, Work Highlights 헤더의 "View our Work" 링크, 카드마다 있던
  "View Project"는 전부 삭제 — 존재하지 않는 하위 페이지로 이동하는 것처럼 보였기 때문
- 남긴 액션은 상단 nav(같은 페이지 내 스크롤 이동)와 Contact의 메일 CTA(실제 액션)뿐
- 모달·아코디언 없음, 전체가 한 페이지에 스크롤로 구성

## Structure

```
index.html          메인 페이지 1개 (Hero → Work Highlights → Our Clients → Services → Testimonial → Contact → Footer)
css/style.css        디자인 토큰(styles.css 원본) + 컴포넌트 스타일
js/main.js           스크롤 리빌(IntersectionObserver), reduced-motion 대응
assets/favicon.svg   파비콘
```

## 로컬 실행

```bash
python3 -m http.server 8000
# http://localhost:8000 접속
```

## 배포

`main` 브랜치에 push하면 GitHub Actions가 자동으로 GitHub Pages에 배포합니다.
저장소 Settings → Pages → Source가 "GitHub Actions"로 설정되어 있어야 합니다.
