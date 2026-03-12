# 📊 CEOK Portfolio

> **개인 투자 포트폴리오 관리 웹앱** — 실시간 가격 조회 · 리밸런싱 · 시장 심리 분석

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-brightgreen?style=for-the-badge&logo=github)](https://tanesia911.github.io/portfolio/)
[![PWA](https://img.shields.io/badge/PWA-지원-blue?style=for-the-badge)](https://tanesia911.github.io/portfolio/)
[![No Backend](https://img.shields.io/badge/Backend-불필요-orange?style=for-the-badge)](https://tanesia911.github.io/portfolio/)

---

## 📱 스크린샷

### 대시보드 — 시장 지표 & 매매신호
![Dashboard](https://tanesia911.github.io/portfolio/screenshot-dashboard.png)

*F&G 지수 · VIX · 환율 · 풋콜레이쇼 · 장단기 금리차 · HYG · S&P500 추세 · 종합 매매신호*

### 보유종목 — 실시간 수익률 현황
![Holdings](https://tanesia911.github.io/portfolio/screenshot-holdings.png)

---

## ✨ 주요 기능

### 📊 대시보드
| 지표 | 설명 | 데이터 소스 |
|------|------|------------|
| **F&G 지수 (미국)** | CNN 공포·탐욕 지수 0~100 | CNN Markets |
| **F&G 지수 (코인)** | 비트코인 시장 심리 지수 | Alternative.me |
| **VIX 공포지수** | S&P500 변동성 · 52주 범위 표시 | CBOE / Yahoo Finance |
| **환율 USD/KRW** | 실시간 달러-원화 · 52주 범위 | Yahoo Finance |
| **풋-콜 레이쇼** | CBOE 옵션 시장 심리 | CBOE |
| **📐 장단기 금리차** | 10년물 - 2년물 국채 스프레드 | Yahoo Finance |
| **🏦 신용시장 HYG** | 하이일드 채권 · 주식 선행지표 | Yahoo Finance |
| **📈 S&P500 추세** | 현재가 vs 200일 이동평균 | Yahoo Finance |
| **🎯 종합 매매신호** | 위 지표 종합 → 강력매수~강력매도 | 자체 계산 |

### 📋 보유종목
- 미국주식 · 국내주식 · 코인 · 금 · ETF 모두 지원
- 실시간 현재가 · 수익률 · 수익금 자동 계산
- 드래그로 종목 순서 변경
- 종목 복사 기능 (유사 종목 빠르게 추가)

### ⚖️ 리밸런싱
- 목표 비중 대비 현재 비중 차이 자동 계산
- 추가 투자금 입력 시 매수 수량 자동 계산
- 연금저축 · IRP 등 제외 계좌 설정 지원
- 계좌별 / 전체 리밸런싱 전환

### 📅 배당 관리
- 종목별 배당금 · 배당수익률 관리
- 연간 예상 배당금 합계

### ⚙️ 설정
- 계좌 추가 · 삭제 · 이름 변경 (인라인 편집)
- 계좌별 목표 비중 설정
- JSON 내보내기 / 불러오기 (데이터 백업)
- 자산군 관리

---

## 🎯 종합 매매신호 알고리즘

```
심리 점수 (기본값)
  ├─ F&G 지수    35% 가중치
  ├─ VIX         30% 가중치
  └─ 풋콜레이쇼  20% 가중치

구조 필터 (자동 조정)
  ├─ 장단기 금리차 역전 중    → -12점 (경기침체 선행 경고)
  ├─ 금리차 역전 해소 직후    → -8점  (가장 위험한 구간)
  ├─ S&P500 200일 MA 5% 하회  → -15점 (하락추세 매수신호 억제)
  └─ HYG 52주 저점 근처       → -10점 (신용위기 경고)

최종 판정
  ├─ 80점↑  🔴 강력매수
  ├─ 65~79  🟠 매수
  ├─ 40~64  🟡 홀드
  ├─ 25~39  🟢 매도
  └─ 24점↓  🔵 강력매도
```

> ⚠️ **주의**: 이 신호는 **참고용**입니다. 단독 매매 근거로 사용하지 마세요.  
> 펀더멘털(기업 실적, 금리 방향)은 반영되지 않습니다.

---

## 🚀 설치 & 사용

### 웹에서 바로 사용
👉 **[https://tanesia911.github.io/portfolio/](https://tanesia911.github.io/portfolio/)**

별도 설치 없이 브라우저에서 바로 사용 가능합니다.

### 홈 화면에 추가 (PWA)
앱처럼 사용하고 싶다면:
- **Android Chrome**: 주소창 옆 `⋮` → 홈 화면에 추가
- **iOS Safari**: 공유 버튼 `□↑` → 홈 화면에 추가
- **또는** 앱 내 `📲 홈에 추가` 버튼 클릭

### 로컬에서 실행
```bash
git clone https://github.com/tanesia911/portfolio.git
cd portfolio
# 그냥 index.html을 브라우저로 열기
open index.html
```

---

## 📖 사용법

### 1. 종목 추가
`보유종목 탭` → `+ 종목 추가` → 계좌 · 자산군 · 티커 · 수량 · 평균단가 입력

**티커 입력 예시**
| 종목 | 티커 |
|------|------|
| 애플 | `AAPL` |
| 나스닥100 ETF | `QQQ` |
| 삼성전자 | `005930.KS` |
| KODEX S&P500 | `379800.KS` |
| 비트코인 | `KRW-BTC` |
| KRX 금 | `KRX-GOLD` |

### 2. 잔고 입력
`설정 탭` → 주식계좌 잔고 · 업비트 잔고 입력  
*(증권사 앱의 "총자산" 금액 그대로 입력 → 예수금 자동 계산)*

### 3. 목표 비중 설정
`설정 탭` → 계좌 관리 → 각 계좌 비중(%) 설정  
*(🔒 독립 버튼: 연금저축·IRP처럼 비중 계산에서 제외)*

### 4. 리밸런싱 확인
`리밸런싱 탭` → 현재 비중 vs 목표 비중 차이 확인  
*추가 투자금 입력 시 매수 수량 자동 계산*

### 5. 데이터 백업
`설정 탭` → `JSON 내보내기` → 파일 저장  
*브라우저 변경 또는 초기화 시 `JSON 불러오기`로 복원*

---

## 🛠 기술 스택

```
Frontend      HTML5 · CSS3 · Vanilla JavaScript (의존성 없음)
데이터 저장   IndexedDB (영구 저장) + localStorage (폴백)
가격 조회     Yahoo Finance API · 업비트 API · CBOE
              CORS 우회: allorigins · corsproxy.org (Race 방식)
배포          GitHub Pages (무료)
PWA           Web App Manifest · 홈 화면 추가 지원
차트          Canvas API (외부 라이브러리 없음)
```

---

## 📁 파일 구조

```
portfolio/
└── index.html   ← 앱 전체 (단일 파일)
```

모든 로직 · 스타일 · 데이터가 `index.html` 하나에 포함되어 있습니다.  
별도 서버 · 데이터베이스 · 빌드 과정이 필요 없습니다.

---

## ⚡ 성능 최적화

- 가격 데이터 **5분 캐시** (불필요한 API 호출 방지)
- **60초 자동 새로고침** (화면 활성 시만)
- 저장 **300ms 디바운스** (잦은 DB 쓰기 방지)
- 렌더링 **requestAnimationFrame** 배치 처리
- 프록시 **Race 방식** (여러 프록시 동시 요청 → 가장 빠른 응답 사용)

---

## ⚠️ 알려진 한계

- **가격 조회**: 무료 공개 프록시 경유 → 간헐적 실패 가능 (새로고침으로 재시도)
- **데이터 저장**: 브라우저 로컬 저장 → 기기 간 동기화 없음
- **매매신호**: 심리 지표 기반 참고용, 투자 조언 아님
- **국내주식 가격**: `.KS` 종목은 Yahoo Finance 데이터 (15분 지연)

---

## 🔒 개인정보

- **서버 전송 없음**: 모든 데이터는 본인 기기에만 저장
- **로그인 불필요**: 계정 생성 없이 바로 사용
- **오픈소스**: 코드 전체 공개

---

## 📄 라이선스

MIT License — 자유롭게 사용, 수정, 배포 가능합니다.

---

<div align="center">

**CEOK Portfolio** · Made with ☕  
[Live Demo](https://tanesia911.github.io/portfolio/) · [Report Bug](https://github.com/tanesia911/portfolio/issues)

</div>
