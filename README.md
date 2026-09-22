# VEXOHUB Dashboard Rebuild

현재 VEXOHUB의 주문/회원/관리 API를 유지하면서, 사용자가 제공한 다크 대시보드 스타일을 기준으로 공개 상점 UI를 전면 교체한 운영용 빌드입니다.

## 구조
- `index.html` — 대시보드형 상점 UI
- `server.js` — 기존 주문/회원/관리 API + 라이선스 API가 포함된 서버
- `products.json` — API가 잠시 응답하지 않을 때 사용하는 43개 상품 fallback
- `assets/products/` — 실제 상품 이미지 12종
- `admin/licenses.html` — 관리자 라이선스 센터

## Render
Build Command: `npm install`
Start Command: `npm start`

필수 환경변수(기존 값 포함): `ADMIN_USERNAME`, `ADMIN_EMAIL`, `ADMIN_PASSWORD`, `BANK_INFO`, `DISCORD_INVITE_URL`, `DISCORD_WEBHOOK_URL`, `SESSION_SECRET`, `LICENSE_ADMIN_SECRET`.

## 상품
운영 중인 상품은 서버의 `/api/products`를 우선 사용합니다. API가 잠시 느리거나 실패하면 `products.json`이 먼저 표시되므로 빈 상품 화면을 만들지 않습니다.

## 이미지
상품 이미지는 `assets/products/`에 넣고 `index.html`의 이미지 매핑으로 연결합니다. 이미지가 없는 상품은 카테고리 기본 이미지로 대체됩니다.

## 라이선스
관리자 로그인 후 `/admin/licenses`에서 BASIC / BASIC PREMIUM / PRO / PRO PREMIUM 라이선스를 발급할 수 있습니다.

## 기존 운영 데이터
`server.js`가 사용하는 `data/db.json`은 GitHub에 커밋하지 마세요. Render에서는 영구 디스크/백업 방식을 따로 고려해야 합니다.
