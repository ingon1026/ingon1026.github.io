# CLAUDE.md

김인곤 개인 포트폴리오 사이트(https://ingon1026.github.io). al-folio v1.x 스타터를 fork한 **사용자 사이트**예요.

## 주의: 템플릿 문서는 이 사이트와 다름

`AGENTS.md`, `docs/`는 al-folio 원본 저장소용 문서예요. 아래 항목은 이 사이트에 맞지 않아요.

- **baseurl은 비어 있음.** `/al-folio`가 아니에요. `--baseurl` 옵션 없이 빌드하고, dev 서버 주소는 `http://localhost:4000/`예요.
- **`_includes/header.liquid`는 의도된 override.** 언어 전환 navbar예요. 그래서 `npm run lint:style-contract`는 항상 실패하는데, 정상이에요. 사용자 사이트는 gem 파일을 override해도 돼요.
- `test/integration_*.sh`, `test/visual/`은 템플릿 유지보수용이에요. 이 사이트 변경을 검증하는 용도가 아니에요.

## 콘텐츠 규칙

- **한국어가 기본, 영어는 짝 파일.** `_pages/X.md` ↔ `_pages/en/X.md`, `_projects/X.md` ↔ `_projects/en/X.md` 구조예요. front matter에 `lang: ko|en`을 넣고, 영어판 permalink는 `/en/...`이에요. 한쪽을 고치면 다른 쪽도 같이 고쳐요.
- 프로젝트는 `category: industry | research`로 나뉘고, `importance`로 순서를 정해요.
- 한국어 페이지에는 회사명을 `(주)케이쓰리아이`, 영어 페이지에는 `K3I`로 써요.
- 뉴스(`_news/`)와 논문(`_bibliography/papers.bib`)은 언어 구분 없이 하나씩 있어요.
- About·Patents 스타일(`yd-*`, `pt-*`)은 각 페이지 안의 `<style>` 블록에 있어요. ko/en 파일에 같은 블록이 복사돼 있어요.
- `assets/css/main.scss`는 gem 파일을 override한 거예요. 하단의 accent 색만 추가했어요. gem을 업그레이드할 때는 `@use` 목록을 gem과 맞춰야 해요.
- 논문·특허 정보는 원문(게재 논문, KIPO 접수증)과 대조한 값이에요. 추측으로 바꾸지 않아요.

## 빌드 확인

로컬에 Ruby가 없어서 Docker로 빌드해요. 이 PC의 `~/.docker/config.json`에 WSL 시절 `credsStore`가 남아 있다면 pull이 실패해요. 그럴 땐 `DOCKER_CONFIG=<빈 디렉터리>`를 앞에 붙여 실행해요.

```bash
docker run --rm -v "$PWD":/srv -w /srv -e JEKYLL_ENV=production ruby:3.3.5 bash -c \
  'apt-get update -qq && apt-get install -y -qq imagemagick nodejs >/dev/null &&
   bundle install --quiet && bundle exec jekyll build -d /tmp/_site'
```

빌드 중 나오는 `drawing-bvh-flow-1400.webp` 중복 생성 경고는 원래 있던 거예요 (빌드 실패 아님).

## 배포 · 커밋

- `main`에 push하면 `deploy.yml`이 빌드해서 `gh-pages` 브랜치로 배포돼요. push가 곧 공개예요.
- 커밋은 Conventional Commits 형식으로 써요 (`feat(projects): ...`, `fix(about): ...`).
