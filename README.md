# Red-Ocean Money Factory — 체험판 (Demo)

레드오션 구조 해부 → AI 숏폼 대본 → 영상 프리뷰 → 성과 진단까지, **백엔드 설치 없이 브라우저에서 전 과정을 체험**하는 정적 데모 사이트입니다.

- 체험 URL: https://ssunwoochoi-create.github.io/red-ocean-demo/
- 원본 앱: https://github.com/ssunwoochoi-create/red-ocean-money-factory (FastAPI + Next.js)

## 체험 범위

| 단계 | 화면 | 체험 모드에서 동작 |
| --- | --- | --- |
| 01 | `/` 키워드 투입 | 입력한 키워드로 즉시 데모 분석 시작 |
| 02 | `/analysis` 시장 해부 | 경쟁 영상 5개, 떡상 공식(후킹·제목·썸네일), 시청자 결핍/욕망·대표 댓글 |
| 03 | `/draft` 대본 생성 | 후킹–문제제기–해결책–증거–행동유도 5개 씬 대본 (직접 수정 가능) |
| 04 | `/production` 영상 제작 | 실제 MP4 대신 **9:16 숏폼 프리뷰 카드 + 진행 상태** 시뮬레이션, 멀티플랫폼(쇼츠/릴스/틱톡) 규격 변환 시뮬레이션, 블로그·스레드·인스타 텍스트 자산 생성 |
| 05 | `/dashboard` 성과 진단 | 유지율 입력 → 이탈 지점 진단, 부캐 채널 복제 전략 |
| — | `/settings` 설정 | API 키 상태 안내 (모두 "데모 모드") |

실제 API 호출과 MP4 합성은 PC에서 원본 저장소의 `run.bat`(Windows) / `./run.sh`(macOS·Linux)을 실행하면 동작합니다.
입력한 키워드와 대본은 브라우저 localStorage에만 저장되며 서버로 전송되지 않습니다.

## 이 저장소의 구성

이 저장소에는 **빌드 결과물만** 올라가 있습니다 (GitHub Pages / main 브랜치 루트).

```text
index.html, analysis/, draft/, production/, dashboard/, settings/
_next/          ← 정적 자산 (basePath: /red-ocean-demo)
.nojekyll       ← GitHub Pages Jekyll 처리 방지 (필수)
```

## 수정·재배포 방법

원본 저장소의 `frontend/`를 고친 뒤, 체험판 빌드 작업 디렉터리에서 다음을 실행합니다.

```bash
cd deploy/red-ocean-demo
./publish.sh "변경 내용"
```

`next.config.js` 핵심 설정: `output: 'export'`, `basePath: '/red-ocean-demo'`, `trailingSlash: true`, `images.unoptimized: true`.
데모 폴백 로직은 `lib/api.ts`에 있으며, `NEXT_PUBLIC_API_URL`이 없거나 호출이 실패하면 에러 없이 데모 데이터를 반환합니다.
