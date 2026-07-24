# Financial Intelligence Suite Portal

정적(Static) HTML 기반의 금융 도구 포털입니다. 단일 `index.html` 파일에서 Public / Private 모드별 분석 도구 카드를 렌더링하고, 각 Cloud Run 서비스로 빠르게 이동하는 **런처(Launcher)** 역할을 합니다.

## 프로젝트 개요

이 저장소는 별도 빌드 과정 없이 브라우저에서 바로 실행할 수 있는 단일 페이지 포털입니다.

- 금융 분석용 개별 서비스들을 카드 UI로 제공
- `Public` / `Private` 토글로 공개 도구와 개인 도구를 구분
- 카드 번호/문자 단축키로 현재 표시된 도구를 즉시 실행
- 좌우 방향키 또는 모바일 가로 스와이프로 모드 전환
- 외부 서비스 링크는 새 탭으로 열고 `noopener noreferrer` 보안 속성을 적용
- 금융 포털에 맞는 상승 차트형 SVG favicon을 브라우저 탭 아이콘으로 사용

## 화면 구성

### Header

- 좌측 브랜드 텍스트: `Investor Portal`
- 우측 모드 토글: `Public`, `Private`
- 계정 아이콘 버튼: Material Symbols `account_circle`

### Main

- Public 제목: `Financial Intelligence Suite`
- Public 설명: `Select a specialized module to begin your market analysis. Professional grade tools for institutional accuracy.`
- Private 제목: `Private Workspace`
- Private 설명: `Open a personal dashboard or utility for private workflows. Dedicated tools for everyday tasks and quick access.`
- 카드 그리드: 반응형 1~4열 구성
- 카드 hover 시 설명 툴팁 표시
- 카드 우측 상단에는 실행 단축키 번호/문자 표시

### Footer

- 저작권 문구: `© 2024 Investor Portal. All rights reserved.`
- 하단 링크: `Privacy Policy`, `Terms of Service`, `Contact Support`

## 현재 연결된 서비스

### Public 모드

포털 기본 화면에는 아래 13개 모듈 카드가 포함되어 있습니다.

| 단축키 | 서비스 | URL | 아이콘 |
| --- | --- | --- | --- |
| `1` | Daily K-Stock Dashboard | `https://daily-kr-stock.ai.studio` | `dashboard` |
| `2` | Market Pulse KR | `https://krx-market-pulse.ai.studio` | `monitoring` |
| `3` | Global Index Performance | `https://global-stock-index-performance.ai.studio` | `public` |
| `4` | Calendar Explorer | `https://stock-calendar-explorer.ai.studio` | `calendar_today` |
| `5` | Volatility Analyzer | `https://kospi-volatility-returns-analyzer.ai.studio` | `show_chart` |
| `6` | ETF Performance | `https://etf-performance.ai.studio` | `query_stats` |
| `7` | Stock Performance | `https://stock-performance.ai.studio` | `trending_up` |
| `8` | Financial Sentinel | `https://financial-sentinel.ai.studio` | `shield` |
| `9` | DART Financial Analysis | `https://dart-financial-analysis.ai.studio` | `analytics` |
| `A` | Global Market Index Dashboard | `https://global-market-index.ai.studio` | `language` |
| `B` | KOSPI Shock Recovery Analyzer | `https://kospi-shock-recover.ai.studio` | `stacked_line_chart` |
| `C` | KiStock AI Studio | `https://kistock.ai.studio` | `auto_awesome` |
| `D` | KRX Market Action Monitor | `https://krx-market-action-monitor.ai.studio` | `candlestick_chart` |

### Private 모드

우측 상단의 `Private` 토글을 선택하면 Public 카드가 전환 애니메이션과 함께 사라지고, 아래 7개 private 메뉴 카드가 표시됩니다.

| 단축키 | 서비스 | URL | 아이콘 |
| --- | --- | --- | --- |
| `1` | Retirement Countdown | `https://retirement-countdown.ai.studio` | `timer` |
| `2` | Naver Blog Scraper | `https://naver-blog-scraper.ai.studio` | `article` |
| `3` | HIRA Stats Explorer | `https://hira-stats-explorer.ai.studio` | `bar_chart` |
| `4` | Real Estate Explorer | `https://real-estate-explorer-kr.wonderful-writing-32.chatgpt.site/` | `real_estate_agent` |
| `5` | PDF Password Remover | `https://pdf-free.ai.studio` | `picture_as_pdf` |
| `6` | Social Screenshot Studio | `https://social-screenshot-studio.ai.studio` | `photo_camera` |
| `7` | Memoir | `https://memoir.ai.studio` | `folder_special` |

## 주요 동작

- `Public` / `Private` 버튼 클릭 시 현재 모드가 전환됩니다.
- 모드 전환 시 상단 제목과 설명도 Public / Private 용도에 맞게 변경됩니다.
- 좌우 방향키(`ArrowLeft`, `ArrowRight`)로 Public / Private 모드를 번갈아 전환할 수 있으며, 입력 방향에 맞춰 카드 가운데 축을 기준으로 넘기듯 전환됩니다.
- 모바일 터치 환경에서는 일정 거리 이상의 가로 스와이프로 모드를 전환할 수 있습니다.
- 현재 화면에 표시된 카드의 단축키를 누르면 해당 카드 링크가 실행됩니다.
- 입력 필드, 셀렉트, 텍스트 영역, contenteditable 요소에 포커스가 있을 때는 단축키가 동작하지 않습니다.
- 카드 클릭 시 외부 Cloud Run URL이 새 탭(`target="_blank"`)으로 열립니다.

## 기술 스택

- **HTML5**: 단일 페이지 마크업
- **Tailwind CSS CDN**: `forms`, `container-queries` 플러그인 포함
- **Google Fonts**: Manrope
- **Material Symbols**: 카드 및 계정 아이콘
- **Vanilla JavaScript**: 카드 렌더링, 모드 전환, 키보드 단축키, 터치 스와이프 처리
- **SVG favicon**: `data:image/svg+xml` 인라인 favicon

## 파일 구조

```text
.
├── .gitignore   # 로컬 작업 메모 및 임시 파일 제외
├── index.html   # 포털 UI, Public/Private 카드 정의 및 동작 로직
└── README.md    # 프로젝트 문서
```

`tasks/todo.md`는 작업 진행용 로컬 메모 파일로 사용하며 저장소에는 포함하지 않습니다.

## 로컬에서 실행하기

빌드/설치가 필요 없는 정적 페이지입니다.

### 방법 1) 파일 직접 열기

브라우저에서 `index.html` 파일을 바로 엽니다.

### 방법 2) 간단한 로컬 서버 실행

```bash
python3 -m http.server 8000
```

실행 후 브라우저에서 아래 주소로 접속합니다.

```text
http://localhost:8000
```

## 운영/수정 가이드

### 새 서비스 카드 추가

`index.html`의 `publicCards` 또는 `privateCards` 배열에 아래 항목을 추가합니다.

- `key`: 카드 번호 또는 문자 단축키
- `title`: 카드 제목
- `href`: 이동할 Cloud Run URL
- `icon`: Material Symbols 아이콘 이름
- `description`: hover 툴팁에 표시할 설명

### UI 일관성 유지 체크리스트

- 기존 카드와 동일한 `cardClass` 기반 레이아웃 유지
- 외부 링크 보안 속성 `rel="noopener noreferrer"` 유지
- 새 탭 열기 `target="_blank"` 유지
- 단축키는 현재 표시된 카드 기준으로만 동작하도록 유지
- 카드 추가/삭제 시 README의 서비스 표도 함께 갱신

## 배포 메모

이 프로젝트 자체는 정적 파일이므로, 어떤 정적 호스팅 환경에서도 배포 가능합니다.

- GitHub Pages
- Cloud Storage Static Hosting
- Nginx / Apache 정적 서빙

## 주의사항

- 각 카드 링크 대상인 외부 Cloud Run 서비스의 가용성은 별도 관리됩니다.
- 포털은 링크 집합 UI이므로, 개별 분석 로직과 데이터 파이프라인은 본 저장소 범위에 포함되지 않습니다.
- Private 모드는 인증 기능이 아니라 포털 내 메뉴 분류 기능입니다.
