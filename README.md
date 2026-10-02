# ingon1026.github.io

김인곤(Vision AI 연구원)의 개인 포트폴리오 사이트예요 → **https://ingon1026.github.io**

- 기본 언어는 한국어이고, 영어판은 `/en/` 아래에 있어요.
- [al-folio](https://github.com/alshedivat/al-folio) v1.x(Jekyll)를 기반으로 만들었어요. 라이선스는 [MIT](LICENSE)예요.

## 구조

| 경로                                    | 내용                                                               |
| --------------------------------------- | ------------------------------------------------------------------ |
| `_pages/` · `_pages/en/`                | About, Experience, Projects, Publications, Patents (한국어 · 영어) |
| `_projects/` · `_projects/en/`          | 프로젝트 상세 페이지 (`category: industry` / `research`)           |
| `_news/`                                | About의 뉴스 항목                                                  |
| `_bibliography/papers.bib`              | 논문 목록                                                          |
| `_data/cv.yml`, `_data/socials.yml`     | CV · 소셜 링크                                                     |
| `_includes/header.liquid`               | 언어 전환 navbar (gem 레이아웃 override)                           |
| `assets/css/main.scss`                  | gem CSS override (accent 색)                                       |
| `assets/img/projects/`, `assets/video/` | 프로젝트 이미지 · 데모 영상                                        |
| `assets/pdf/KimInGon_CV.pdf`            | About 페이지 CV 버튼과 연결된 PDF                                  |

## 로컬 빌드

Ruby가 없어도 Docker만 있으면 빌드할 수 있어요 (CI와 같은 Ruby 3.3.5).

```bash
docker run --rm -v "$PWD":/srv -w /srv -p 4000:4000 ruby:3.3.5 bash -c \
  'apt-get update -qq && apt-get install -y -qq imagemagick nodejs >/dev/null &&
   bundle install && bundle exec jekyll serve --host 0.0.0.0'
# → http://localhost:4000/
```

## 배포

`main`에 push하면 `.github/workflows/deploy.yml`이 빌드해서 `gh-pages` 브랜치에 올리고, GitHub Pages가 그 브랜치를 서비스해요.
