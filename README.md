# potato-55min-projects
potato series 프로젝트에 접속하는 **sitemap** 페이지.

- `projects.json`: 프로젝트 목록 (여기만 수정)
- `index.html`: 목록을 카드로 렌더링 (검색, 프로젝트 열기, repo 링크)

## 프로젝트 추가
`projects.json`에 항목 추가 → main에 merge → GitHub Pages 자동 배포.
```json
{ "name": "potato-foo", "description": "설명", "url": "https://...", "tags": ["web"] }
```
`url`이 비어 있으면 "준비중"으로 표시된다.

## 최초 1회
Settings → Pages → Source: **GitHub Actions**
