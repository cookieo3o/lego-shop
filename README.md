# 🛒레고 - 반응형 전자상거래 플랫폼 학습을 위한 코딩🛒
> **사용자 친화적 인터페이스와 완전한 반응형 디자인을 갖춘 전자상거래 플랫폼의 구조와 구현 방식을 이해하기 위해 코딩 실습을 수행했습니다😊**<br>
> **💻 [레고 페이지 보러가기](https://cookieo3o.github.io/lego-shop/)**<br>
<br>
<br>


## 작업 환경
![TOOL](https://img.shields.io/badge/TOOL-VS_CODE-blue) ![TOOL](https://img.shields.io/badge/TOOL-figma-brown) ![TOOL](https://img.shields.io/badge/TOOL-phtoshop-blue) ![TOOL](https://img.shields.io/badge/TOOL-illust-orange) <br>
![STATIC](https://img.shields.io/badge/STATIC-HTML-green) ![STATIC](https://img.shields.io/badge/STATIC-SCSS-hotpink) ![STATIC](https://img.shields.io/badge/STATIC-JAVA_script-yellow) 
<br>
<br>

## 프로젝트 주제
프리미엄  쇼핑몰 웹사이트  - 사용자 친화적인 인터페이스와 완전한 반응형 디자인을 갖춘 전자상거래 플랫폼
<br>
<br>

## 제작 목적
- **실전 웹 개발 학습** : HTML, CSS(SCSS), JavaScript를 활용한 실제 쇼핑몰 구현
- **반응형 웹 디자인 마스터** : 모바일, 태블릿, 데스크톱 모든 기기에서 완벽한 사용자 경험 제공
- **상태 관리 학습** : localStorage를 활용한 클라이언트 사이드 데이터 관리
- **컴포넌트 기반 개발** : 재사용 가능한 UI 컴포넌트 설계 및 구현
<br>
<br>

## 주요 타겟 사용자
- **주 사용자** : 레고를 좋아하는 모든 사용자
- **기술 수준** : 초보자부터 중급자까지 이해할 수 있는 코드 구조
- **접근성** : 키보드 네비게이션 및 스크린 리더 지원
<br>
<br>

## 사용 기술 스택
- **HTML5** : 시맨틱 마크업, 접근성 고려
- **SCSS/CSS3** : 변수, 믹스인, 중첩을 활용한 효율적인 스타일 관리
- **JavaScript** : 프레임워크 없이 순수 JavaScript로 구현
- **Bootstrap Icons** : 아이콘 라이브러리
- **LocalStorage API** : 클라이언트 사이드 데이터 저장
<br>

---

## 🏗️ 전체 구조 설명

### 페이지 구성도

```
index.html          → 메인 페이지 (홈)
sub1.html          → 상품 목록 페이지
sub2.html          → 베스트 상품 페이지
sub3.html          → 장바구니 페이지
sub4.html          → 마이페이지
product-detail.html → 상품 상세 페이지
```

### 공통 레이아웃 구조

모든 페이지 구조

```
Header (공통) 
- 로고                     
- 네비게이션 메뉴            
- 검색, 장바구니, 마이페이지

 Main Content (페이지별 고유 콘텐츠) 

Footer (공통)
- 고객센터 정보    
- 회사 정보 
```

---

## 📄 페이지별 구현 의도 및 설명

### [메인 페이지 (index.html)]

**구현 목표**
- 사용자가 서비스를 직관적으로 이해하고 주요 상품을 한눈에 볼 수 있도록 구성

**핵심 기능**
- Hero 슬라이더 (자동 전환 배너)
- 베스트/신상품/특가 상품 섹션
- 최근 본 상품 섹션
- 검색 기능
- 장바구니 아이콘에 실시간 개수 표시

**어려웠던 점**
- 슬라이더 자동 전환과 수동 전환 간 충돌 해결 → 상태 변수로 제어
- 모바일에서 상품 카드 이미지 비율 유지 → `object-fit: cover` 활용
- localStorage 데이터 동기화 → `updateCartCount()` 함수로 전역 관리

**개선 방향**
- 이미지 lazy loading 적용 예정
- 상품 데이터를 서버 API로 전환
- 무한 스크롤 또는 페이지네이션 추가

---

### [상품 목록 페이지 (sub1.html)]

**구현 목표**
- 다양한 필터와 정렬 옵션을 제공하여 사용자가 원하는 상품을 쉽게 찾을 수 있도록 구성

**핵심 기능**
- 카테고리 필터 (사이드바)
- 가격대 필터
- 정렬 옵션 (인기순, 가격순 등)
- 검색 결과 표시
- 검색 결과 없음 안내 메시지

**어려웠던 점**
- 하드코딩된 상품 카드에 `data-product-id` 속성이 없어 장바구니 추가 실패 → 제목으로 상품 찾기 로직 추가
- 검색어가 없을 때와 있을 때 UI 전환 → 조건부 렌더링으로 해결

**개선 방향**
- 실제 필터링 기능 구현 (현재는 UI만 존재)
- 페이지네이션 제거 완료 (사용자 요청)
- 필터 조합 기능 추가 예정

---

### [베스트 상품 페이지 (sub2.html)]

**구현 목표**
- 인기 상품을 순위별로 강조하여 표시하고, 사용자의 구매 결정을 돕는 정보 제공

**핵심 기능**
- TOP 3 상품 특별 강조 (큰 카드)
- 순위 배지 (1위: 트로피, 2-3위: 상 아이콘)
- 나머지 상품 그리드 표시
- 상품 정렬 기능

**어려웠던 점**
- 인라인 스타일을 SCSS 클래스로 전환 → 순위별 클래스 추가
- TOP 3 카드 크기 조정으로 레이아웃 깨짐 → `grid-column: span` 활용

**개선 방향**
- 실제 판매량 기반 순위 계산 로직 추가
- 상품 비교 기능 추가 예정

---

### [장바구니 페이지 (sub3.html)]

**구현 목표**
- 사용자가 선택한 상품을 확인하고 수량 조절, 삭제, 주문하기까지의 과정을 제공

**핵심 기능**
- 장바구니 상품 목록 표시
- 수량 증가/감소 버튼
- 상품 삭제 기능
- 총 금액 자동 계산
- 장바구니가 비어있을 때 안내 메시지

**어려웠던 점**
- 수량 변경 시 총 금액이 실시간으로 업데이트되지 않음 → 이벤트 위임으로 해결
- localStorage 데이터 형식 통일 → `{id, title, price, quantity, image}` 객체 구조로 표준화

**개선 방향**
- 옵션 선택 기능 추가 (색상, 사이즈 등)
- 주문하기 페이지 연결
- 쿠폰/할인 기능 추가 예정

---

### [마이페이지 (sub4.html)]

**구현 목표**
- 사용자의 주문 내역, 찜한 상품, 리뷰, 회원정보를 한 곳에서 관리할 수 있도록 구성

**핵심 기능**
- 탭 메뉴로 섹션 전환 (주문내역, 찜한 상품, 리뷰 관리, 회원정보 수정, 배송지 관리)
- 주문 내역 표시 (실제 상품 이미지 포함)
- 찜한 상품 그리드 표시
- 리뷰 작성/수정/삭제 UI
- 회원정보 수정 폼
- 배송지 관리 (기본 배송지 설정)

**어려웠던 점**
- 주문 내역 이미지가 placeholder로 표시됨 → 실제 상품 이미지 URL로 교체
- 인라인 스타일이 많아 유지보수 어려움 → 모든 스타일을 SCSS로 이동
- 찜한 상품이 없을 때와 있을 때 UI 전환 → 조건부 렌더링으로 해결

**개선 방향**
- 실제 주문 데이터 연동
- 리뷰 작성 모달 추가
- 배송지 추가/수정 모달 구현 예정

---

### [상품 상세 페이지 (product-detail.html)]

**구현 목표**
- 상품의 상세 정보를 제공하고, 옵션 선택, 수량 조절, 장바구니 추가 기능 제공

**핵심 기능**
- 상품 이미지 갤러리
- 상품 정보 표시 (가격, 할인율, 별점, 리뷰 수)
- 옵션 선택 (색상, 사이즈 등)
- 수량 선택
- 장바구니 추가 / 바로구매 버튼
- 최근 본 상품에 자동 추가

**어려웠던 점**
- 옵션 선택 시 가격 변동 처리 → 옵션별 가격 데이터 구조 설계 필요
- 최근 본 상품 중복 방지 → 배열에서 기존 항목 제거 후 맨 앞에 추가

**개선 방향**
- 이미지 확대/줌 기능 추가
- 상품 비교 기능 추가
- 리뷰 섹션 강화 (필터, 사진 리뷰)

---

## 반응형 브레이크포인트

```scss
// _variables.scss
$breakpoint-mobile: 767px;
$breakpoint-tablet: 1024px;
$breakpoint-desktop: 1200px;
```

- **모바일** ~767px 
- **태블릿** 768px ~ 1024px 
- **데스크톱** 1025px ~ 

---

## 디자인 시스템

### 색상 팔레트
- **브랜드 메인** `#0B488D` (파란색)
- **브랜드 서브** `#1900d3` (진한 파란색)
- **액센트** `#FFD912` (노란색)
- **에러** `#ED2040` (빨간색)
- **성공** `#27AE60` (초록색)

### 타이포그래피
- **제목** 24px ~ 32px, Bold
- **본문** 14px ~ 16px, Regular
- **작은 텍스트** 12px ~ 13px, Regular

---

## 📝학습 포인트

이 프로젝트를 통해 학습할 수 있는 내용:

1. **SCSS 활용** : 변수, 믹스인, 중첩을 통한 효율적인 CSS 작성
2. **반응형 디자인** : 미디어 쿼리와 유연한 레이아웃
3. **JavaScript 모듈화** : 기능별로 파일 분리하여 유지보수성 향상
4. **LocalStorage 활용** : 클라이언트 사이드 데이터 저장 및 관리
5. **이벤트 처리** : 이벤트 위임, 동적 요소 이벤트 연결
6. **접근성** : 시맨틱 HTML, ARIA 속성, 키보드 네비게이션

---

## 웹표준 및 웹 접근성 고려 사항

### 웹표준 준수

#### 1. HTML5 시맨틱 태그 사용

**사용한 태그와 목적**

```html
<!--문서 구조를 의미 있게 표현-->
<header>     <!--페이지 상단 헤더-->
<nav>        <!--네비게이션 메뉴-->
<main>       <!--메인 콘텐츠 영역-->
<section>    <!--논리적 콘텐츠 구분-->
<article>    <!--독립적인 콘텐츠 (상품 카드 등)-->
<footer>     <!--페이지 하단 푸터-->
```

**왜 중요한가?**
- 검색 엔진이 페이지 구조를 이해할 수 있음 (SEO 향상)
- 스크린 리더 사용자가 콘텐츠를 더 쉽게 탐색 가능
- 코드 가독성 향상 및 유지보수 용이

**학습한 점**
- `<div>` 대신 의미 있는 태그를 사용하면 코드가 더 명확해짐
- 시맨틱 태그는 스타일링뿐만 아니라 의미 전달이 목적

#### 2. 메타 태그 및 문서 정보

```html
<!DOCTYPE html>                    <!--HTML5 문서 타입 선언-->
<html lang="ko">                   <!--언어 지정 (스크린 리더용)-->
<meta charset="UTF-8">              <!--문자 인코딩 (한글 깨짐 방지)-->
<meta name="viewport" content="width=device-width, initial-scale=1.0">  <!--반응형 설정-->
<meta name="description" content="...">  <!--SEO를 위한 페이지 설명-->
```

**학습한 점**
- `lang="ko"`를 지정하면 스크린 리더가 한국어로 읽어줌
- `viewport` 메타 태그 없이는 모바일에서 레이아웃이 깨짐
- `description`은 검색 결과에 표시되어 클릭률에 영향

### 웹 접근성 (WCAG 2.1 준수)

#### 1. ARIA (Accessible Rich Internet Applications) 속성

**사용한 ARIA 속성**

```html
<!--버튼의 목적을 명확히 설명-->
<button aria-label="검색 열기/닫기">...</button>
<button aria-label="메뉴 토글">...</button>
<a href="..." aria-label="장바구니">...</a>

<!--숨겨진 콘텐츠 상태 표시-->
<div id="searchPanel" aria-hidden="true">...</div>
<input aria-expanded="false">  <!--드롭다운 열림/닫힘 상태-->
```

**왜 중요한가?**
- 스크린 리더 사용자가 버튼의 기능을 이해할 수 있음
- 아이콘만 있는 버튼은 시각 장애인에게 의미 전달 불가 → `aria-label` 필수
- `aria-hidden="true"`로 불필요한 콘텐츠를 스크린 리더에서 숨김

**학습한 점**
- 아이콘 버튼에는 반드시 `aria-label` 추가
- 동적으로 변경되는 UI는 `aria-expanded`, `aria-hidden` 등으로 상태 표시

#### 2. 키보드 접근성

**구현한 기능**

```html
<!--건너뛰기 링크: 키보드 사용자가 본문으로 바로 이동-->
<a class="skip-link" href="#main">본문 바로가기</a>

<!--포커스 가능한 요소에 명확한 포커스 스타일-->
.skip-link:focus {
    transform: translateY(0);  /* 포커스 시 보이도록 */
    outline: 3px solid rgba(25, 0, 211, 0.35);
}
```

**학습한 점**
- Tab 키로만 웹사이트를 사용하는 사람도 있음
- 모든 인터랙티브 요소는 키보드로 접근 가능해야 함
- 포커스 스타일을 명확히 해야 현재 위치를 알 수 있음

#### 3. 대체 텍스트 (Alt Text)

```html
<!--이미지에 의미 있는 대체 텍스트 제공-->
<img src="logo.svg" alt="Elexa(일렉사) 로고">
<img src="product.jpg" alt="삼성 갤럭시 버즈3 프로">

<!--장식용 이미지는 빈 alt-->
<img src="decoration.png" alt="">
```

**학습한 점**
- `alt` 속성은 이미지를 볼 수 없는 사용자를 위한 것
- 의미 있는 이미지는 설명을, 장식용은 빈 문자열
- SEO에도 도움이 됨 (검색 엔진이 이미지 내용 이해)

#### 4. 스크린 리더 전용 텍스트

```html
<!--시각적으로는 숨기지만 스크린 리더는 읽음-->
<label for="searchInput" class="sr-only">상품 검색</label>
```

**CSS 구현**
```scss
.sr-only {
    position: absolute !important;
    width: 1px !important;
    height: 1px !important;
    overflow: hidden !important;
    clip: rect(0, 0, 0, 0) !important;
}
```

**학습한 점**
- `display: none`은 스크린 리더에서도 숨겨짐
- `.sr-only` 클래스로 시각적으로만 숨기고 스크린 리더는 읽도록 함
- 폼 레이블 등 필수 정보는 반드시 제공

#### 5. JavaScript 비활성화 대응

```html
<noscript>
    <div class="noscript-notice">
        이 페이지는 원활한 동작을 위해 JavaScript가 필요합니다.
    </div>
</noscript>
```

**학습한 점**
- 일부 사용자는 보안을 위해 JavaScript를 비활성화
- 기본 HTML만으로도 콘텐츠를 볼 수 있어야 함 (점진적 향상)

---

## 상세 파일 구조 설명

### HTML 파일 구조

```
루트 디렉토리/
├── index.html              # 메인 페이지
│   ├── <header>            # 공통 헤더 (로고, 네비게이션)
│   ├── <main>              # 메인 콘텐츠
│   │   ├── Hero 슬라이더   # 자동 전환 배너
│   │   ├── 베스트 상품      # products.js로 동적 생성
│   │   ├── 신상품          # products.js로 동적 생성
│   │   └── 특가 상품       # products.js로 동적 생성
│   └── <footer>            # 공통 푸터
│
├── sub1.html               # 상품 목록 페이지
│   ├── 필터 사이드바       # 카테고리, 가격대, 정렬
│   └── 상품 그리드         # 검색 결과 또는 전체 상품
│
├── sub2.html               # 베스트 상품 페이지
│   ├── TOP 3 섹션          # best-products.js로 렌더링
│   └── 나머지 상품 그리드  # best-products.js로 렌더링
│
├── sub3.html               # 장바구니 페이지
│   └── 장바구니 목록        # cart-page.js로 localStorage에서 로드
│
├── sub4.html               # 마이페이지
│   ├── 사이드바 메뉴       # 탭 전환 (mypage.js)
│   └── 콘텐츠 패널         # 주문내역, 찜한 상품, 리뷰 등
│
└── product-detail.html     # 상품 상세 페이지
    ├── 상품 이미지 갤러리
    ├── 상품 정보
    └── 옵션 선택 및 장바구니 추가
```

### SCSS 파일 구조

```
SCSS 파일들/
├── style.scss              # 메인 파일 (모든 partial import)
│   ├── @import '_variables'  # 변수 정의
│   ├── @import '_reset'     # CSS 리셋
│   ├── @import '_fonts'     # 웹폰트
│   ├── @import '_mixins'    # 재사용 가능한 믹스인
│   ├── @import '_common'    # 공통 스타일
│   ├── @import 'responsive' # 반응형 스타일
│   └── 메인 스타일 코드     # 페이지별 스타일
│
├── _variables.scss         # 변수 정의 파일
│   ├── 색상 변수           # $c-brand-main, $c-error 등
│   ├── 폰트 변수           # $ff-primary-kr, $fw-bold 등
│   ├── 간격 변수           # $spacing-xs, $spacing-md 등
│   ├── 브레이크포인트      # $bp-mobile, $bp-tablet 등
│   └── 기타 변수           # $r-md, $transition-duration 등
│
├── _mixins.scss            # 믹스인 정의
│   ├── @mixin flex-center  # 중앙 정렬
│   ├── @mixin heading-style # 제목 스타일
│   └── @mixin text-style   # 텍스트 스타일
│
├── _reset.scss             # CSS 리셋
│   └── 브라우저 기본 스타일 제거
│
├── _fonts.scss             # 웹폰트
│   └── @font-face로 폰트 로드
│
├── _common.scss            # 공통 스타일
│   ├── 타이포그래피        # h1~h6 스타일
│   ├── 접근성 헬퍼        # .sr-only, .skip-link
│   └── 공통 컴포넌트       # 버튼, 폼 등
│
├── responsive.scss         # 반응형 스타일
│   └── @media 쿼리로 화면 크기별 스타일
│
└── _best-products.scss    # 베스트 상품 전용 스타일
    └── TOP 3 카드, 순위 배지 등
```

### JavaScript 파일 구조

```
js/
├── products-data.js        # 상품 데이터 (정적 데이터)
│   └── productsData 객체   # best, new, sale 배열
│
├── products.js              # 상품 관련 기능
│   ├── createProductCard() # 상품 카드 HTML 생성
│   ├── loadProducts()      # 상품 그리드에 로드
│   ├── attachProductEvents() # 이벤트 리스너 연결
│   └── searchProducts()    # 검색 기능
│
├── cart.js                 # 장바구니 기능
│   ├── addToCart()         # 장바구니에 추가
│   ├── removeFromCart()    # 장바구니에서 제거
│   ├── updateQuantity()    # 수량 변경
│   └── updateCartCount()   # 장바구니 개수 업데이트
│
├── cart-page.js            # 장바구니 페이지 로직
│   └── 장바구니 목록 렌더링 및 이벤트 처리
│
├── product-detail.js       # 상품 상세 페이지
│   ├── URL 파라미터로 상품 로드
│   └── 최근 본 상품 저장
│
├── search.js               # 검색 기능
│   ├── 검색 패널 열기/닫기
│   └── 검색어 자동완성
│
├── mypage.js               # 마이페이지
│   ├── initMyPageTabs()    # 탭 전환
│   ├── loadWishlist()      # 찜한 상품 로드
│   └── initReviewTabs()    # 리뷰 탭 전환
│
├── best-products.js        # 베스트 상품 페이지
│   ├── renderTop3Products() # TOP 3 렌더링
│   └── renderBestProducts() # 나머지 상품 렌더링
│
├── recent-products.js      # 최근 본 상품
│   └── localStorage에서 읽어와 표시
│
├── header.js               # 헤더 기능
│   └── 모바일 메뉴 토글
│
├── index.js                # 메인 페이지 로직
│   └── 페이지 초기화 및 이벤트 연결
│
├── utils.js                # 유틸리티 함수
│   └── 공통으로 사용하는 헬퍼 함수
│
└── notifications.js        # 알림 기능
    └── 알림 표시 및 자동 닫기
```

---

## 프로젝트에서 배운 점과 느낀 점 

**처음에는😥**
- JavaScript가 매우 어렵게 느껴져서 시작하기가 부담스러웠다.
- 함수, 이벤트, 배열 메서드(map, filter, find) 같은 개념을 이해하기 어려웠다.
- 프로젝트를 진행하면서 파일이 많아지자 구조를 이해하기 어려워 경로 설정에 오류가 많았다.

**지금은🙂**
- 함수가 재사용 가능한 코드 블록이라는 것을 이해하게 되었다.
- 시맨틱 HTML을 통해 웹 접근성을 고려한 개발의 중요성을 이해하게 되었다.
- 버튼 클릭이나 입력 등 사용자 행동에 반응하는 이벤트 개념을 알게 되었다.
- 프로젝트에서는 기능별로 파일을 나누고 작은 기능부터 단계적으로 구현하는 방식이 효율적이라는 것을 배웠다.

**가장 어려웠던 부분🥺**
- 코드가 길어질 때 버그의 원인을 찾는 과정과 디버깅
- map(), filter(), find() 같은 배열 메서드를 사용하는 것
- 프로젝트가 커지면서 코드 구조와 파일 관리를 정리하는 것
- 동적으로 생성된 요소에 이벤트가 적용되지 않는 문제를 이해하고 해결하는 것


##  앞으로 배우고 싶은 것
- **프레임워크** 
  → React나 Vue 같은 걸 배우면 더 쉽게 만들 수 있을 것 같음
- **백엔드**
  → 지금은 데이터를 하드코딩했는데, 서버에서 가져오고 싶음
- **테스트**
  → 내 코드가 제대로 작동하는지 자동으로 확인하는 방법
