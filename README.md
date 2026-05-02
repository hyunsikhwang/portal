# Financial Intelligence Suite Portal

정적(Static) HTML 기반의 포털 페이지로, 여러 금융 분석 도구(Cloud Run 앱)로 빠르게 이동할 수 있는 **런처(Launcher)** 역할을 합니다.

## 프로젝트 개요

이 저장소는 단일 `index.html` 파일로 구성되어 있으며, 다음 목적을 가집니다.

- 금융 분석용 개별 서비스들을 한 화면에서 제공
- 카드 형태 UI를 통해 서비스별 설명 + 실행(Launch) 링크 제공
- 별도 빌드 과정 없이 브라우저에서 즉시 실행 가능

## 현재 연결된 서비스

포털 메인 화면에는 아래 8개 모듈 카드가 포함되어 있습니다.

1. Daily K-Stock Dashboard
2. Market Pulse KR
3. Global Index Performance
4. Calendar Explorer
5. Volatility Analyzer
6. ETF Performance
7. Stock Performance
8. Financial Sentinel

각 카드는 외부 Cloud Run URL로 새 탭(`target="_blank"`)에서 열립니다.

## 기술 스택

- **HTML5**: 단일 페이지 마크업
- **Tailwind CSS (CDN)**: 유틸리티 클래스 기반 스타일링
- **Google Fonts (Manrope)**
- **Material Symbols** 아이콘

## 파일 구조

```text
.
├── index.html   # 포털 UI 및 링크 카드 정의
└── README.md    # 프로젝트 문서
```

## 로컬에서 실행하기

빌드/설치가 필요 없는 정적 페이지입니다. 아래 중 하나로 실행할 수 있습니다.

### 방법 1) 파일 직접 열기

- `index.html` 파일을 브라우저에서 바로 열기

### 방법 2) 간단한 로컬 서버 실행 (권장)

```bash
python3 -m http.server 8000
```

실행 후 브라우저에서 아래 주소 접속:

- `http://localhost:8000`

## 운영/수정 가이드

### 새 서비스 카드 추가

`index.html`의 **Tool Grid** 영역에 기존 카드 블록을 복사해 아래 항목을 변경하세요.

- 카드 제목 (`<h3>...</h3>`)
- 카드 설명 (`<p>...</p>`)
- 링크 URL (`href="..."`)
- 아이콘 이름 (`data-icon="..."` 및 아이콘 텍스트)

### UI 일관성 유지 체크리스트

- 기존 카드와 동일한 레이아웃 클래스 유지
- 버튼 라벨은 `LAUNCH` 유지
- 보안 속성 `rel="noopener noreferrer"` 유지
- 새 탭 열기 `target="_blank"` 유지

## 배포 메모

이 프로젝트 자체는 정적 파일이므로, 어떤 정적 호스팅 환경에서도 배포 가능합니다.

예시:
- GitHub Pages
- Cloud Storage Static Hosting
- Nginx / Apache 정적 서빙

## 주의사항

- 각 카드 링크 대상(외부 서비스)의 가용성은 별도 관리됩니다.
- 포털은 링크 집합 UI이므로, 개별 분석 로직/데이터 파이프라인은 본 저장소 범위에 포함되지 않습니다.
