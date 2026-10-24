# potato-55min-projects
potato series 프로젝트를 통합 관리하는 **단일 게이트웨이**.
모든 repo를 같은 규칙(이름·브랜치·템플릿)으로 다뤄 소규모 프로젝트의 시작 비용을 0에 가깝게 만든다.

## 구조
```
projects.json        # 단일 레지스트리 (source of truth)
bin/potato           # CLI 게이트웨이 (생성/조회/clone/브랜치)
template/            # 새 프로젝트 공통 뼈대 (README, .gitignore, PR 템플릿, CI)
site/                # 웹 게이트웨이 (GitHub Pages, projects.json 렌더링)
```

## 공통 규칙
| 항목 | 규칙 |
|---|---|
| repo 이름 | `potato-<topic>` |
| 기본 브랜치 | `main` (보호, 직접 push 금지) |
| 작업 브랜치 | `feature/<topic>`, `fix/<topic>` |
| 병합 | PR → squash merge, 병합 후 브랜치 자동 삭제 |

## 사용법
요구사항: `git`, `jq`, `gh`(로그인 상태)
```bash
export PATH="$PWD/bin:$PATH"
potato list
potato new potato-foo "설명" web,tool   # repo 생성 + 템플릿 + 브랜치 보호 + 레지스트리 등록
potato sync                              # 전체 clone/pull (워크스페이스 = 이 repo의 상위 폴더)
potato feature potato-foo login          # feature/login 브랜치 시작
potato status
```
`new`/`add` 후 `projects.json` 변경을 커밋하면 웹 게이트웨이가 자동 갱신된다
(Settings → Pages → Source: GitHub Actions 1회 설정 필요).
