# 매장 자동 발주 관리

매장 재고를 세어 입력하면 기준 재고에서 모자란 만큼 발주 수량을 계산하는 웹 페이지예요. 서버 없이 `public/` 폴더의 정적 파일로 동작해요.

- 주소: https://ayoung.hjparkk.com
- 호스팅: Cloudflare Pages. `main` 브랜치에 푸시하면 자동으로 다시 배포돼요.

## 파일

| 경로 | 내용 |
|---|---|
| `public/index.html` | 화면, 스타일, 품목 데이터(`INITIAL_ITEMS`), 동작 코드 |
| `public/manifest.webmanifest`, `public/*.png`, `public/favicon.svg` | 휴대폰 홈 화면에 추가할 때 쓰는 이름과 아이콘 |

## 데이터 저장 방식

- 입력한 재고, 발주 여부, 발주 기록, 화면에서 고친 품목은 각 기기 브라우저의 localStorage에 저장돼요. 다른 기기와 공유되지 않아요.
- 기기를 바꿀 때는 품목 관리 › 백업에서 JSON 파일을 내려받아 새 기기에서 불러오세요.
- 입력하지 않은 재고는 0개로 계산해요.

## 품목과 기준 재고 바꾸기

- 한 기기에서만 바꾸려면 화면의 품목 관리에서 고치면 돼요.
- 모든 기기에 반영하려면 `public/index.html`의 `INITIAL_ITEMS`를 고치고 `STORAGE` 값도 새 이름으로 바꿔서 푸시하세요. 이미 쓰던 기기는 저장해 둔 품목 목록을 먼저 읽기 때문에, `STORAGE`를 바꾸지 않으면 새 목록이 보이지 않아요. `STORAGE`를 바꾸면 각 기기에 입력해 둔 재고와 발주 기록도 처음 상태로 돌아가요.

## Cloudflare Pages 설정

| 항목 | 값 |
|---|---|
| Production branch | `main` |
| Framework preset | None |
| Build command | 비움 |
| Build output directory | `public` |
| Custom domain | `ayoung.hjparkk.com` |

## 로컬에서 보기

`public/index.html`을 브라우저로 열면 돼요.
