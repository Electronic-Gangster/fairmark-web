# 페어마크 웹사이트

시험장 무결성 운영 표준 '페어마크'(가칭)의 서비스 홈과 투자자 페이지입니다. 빌드 과정이 없는 정적 사이트라서 파일을 그대로 올리면 됩니다.

| 파일 | 내용 | 검색 노출 |
|---|---|---|
| `index.html` | 서비스 홈 (키네틱 타이포 디자인) | 노출 |
| `investor.html` | 투자자 정보, 2인 겸업 창업 계획 v1 | 차단 (`noindex`) |
| `fairmark-business-plan-v1.pdf` | 사업계획서 28쪽 | 차단 (`X-Robots-Tag`) |
| `404.html` | 없는 주소로 들어왔을 때의 안내 | 차단 |
| `vendor/` | GSAP 3.15.1 (무료 Standard License) | — |
| `vercel.json` | Vercel 보안 헤더, 검색 차단, 캐시 설정 | — |
| `.github/workflows/pages.yml` | GitHub Pages 자동 배포 (선택) | — |

> 검색 차단은 검색엔진에 나오지 않게 할 뿐, 주소를 아는 사람은 누구나 볼 수 있습니다. 사업계획과 재무 숫자를 외부에 보이고 싶지 않다면 `investor.html`과 PDF를 이 저장소에서 빼고 따로 전달하세요.

## Vercel로 배포

1. 이 폴더를 GitHub 저장소에 올립니다 (비공개 저장소도 됩니다).
2. vercel.com > Add New > Project > 저장소 선택 > Framework Preset은 **Other**, Build Command와 Output Directory는 비워 둡니다.
3. Deploy. 이후 `main` 브랜치에 push할 때마다 자동으로 다시 배포됩니다.

Vercel 무료(Hobby) 플랜은 개인·비상업용입니다. 실제 영업에 쓰는 사이트라면 Pro 플랜 조건을 확인하세요.

## GitHub Pages로 배포

1. 저장소 Settings > Pages > Source를 **GitHub Actions**로 바꿉니다.
2. `main`에 push하면 `.github/workflows/pages.yml`이 사이트를 배포합니다.

무료 계정에서 GitHub Pages는 **공개 저장소**에서만 쓸 수 있습니다. 이때는 저장소 안의 사업계획서 PDF와 코드도 공개되므로, 투자자 자료는 빼고 올리는 것을 권합니다.

## 출시 전에 바꿀 것

- `index.html`의 `var MAIL="contact@example.com"`과 푸터 이메일
- 신청 양식: 지금은 메일 앱을 여는 방식. 폼 접수 서비스나 서버로 교체
- 사업자 정보 (법인 설립 후)
- 커스텀 도메인 연결 (Vercel: Settings > Domains, GitHub Pages: Settings > Pages > Custom domain)
