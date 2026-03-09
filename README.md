# Elexa(일렉사) - 프리미엄 쇼핑몰 프로젝트 - ⭐프로젝트 제목이랑 주제 수정하고 덜어내야 할 내용 삭제⭐

## 프로젝트 개요

### 프로젝트 주제
**프리미엄 전자제품 쇼핑몰 웹사이트** - 사용자 친화적인 인터페이스와 완전한 반응형 디자인을 갖춘 전자상거래 플랫폼

### 제작 목적
- **실전 웹 개발 학습**: HTML, CSS(SCSS), JavaScript를 활용한 실제 쇼핑몰 구현
- **반응형 웹 디자인 마스터**: 모바일, 태블릿, 데스크톱 모든 기기에서 완벽한 사용자 경험 제공
- **상태 관리 학습**: localStorage를 활용한 클라이언트 사이드 데이터 관리
- **컴포넌트 기반 개발**: 재사용 가능한 UI 컴포넌트 설계 및 구현

### 주요 타겟 사용자
- **주 사용자**: 전자제품 구매를 원하는 일반 소비자 (20-50대)
- **기술 수준**: 초보자부터 중급자까지 이해할 수 있는 코드 구조
- **접근성**: 키보드 네비게이션 및 스크린 리더 지원

### 사용 기술 스택
- **HTML5**: 시맨틱 마크업, 접근성 고려
- **SCSS/CSS3**: 변수, 믹스인, 중첩을 활용한 효율적인 스타일 관리
- **JavaScript (Vanilla)**: 프레임워크 없이 순수 JavaScript로 구현
- **Bootstrap Icons**: 아이콘 라이브러리
- **LocalStorage API**: 클라이언트 사이드 데이터 저장

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

모든 페이지는 다음 구조를 공유합니다:

```
┌─────────────────────────────────┐
│         Header (공통)            │
│  - 로고                          │
│  - 네비게이션 메뉴               │
│  - 검색, 장바구니, 마이페이지     │
├─────────────────────────────────┤
│                                 │
│         Main Content            │
│  (페이지별 고유 콘텐츠)         │
│                                 │
├─────────────────────────────────┤
│         Footer (공통)            │
│  - 고객센터 정보                │
│  - 회사 정보                    │
└─────────────────────────────────┘
```

---

## 📄 페이지별 구현 의도 및 설명

### [메인 페이지 (index.html)]

**구현 목표**: 사용자가 서비스를 직관적으로 이해하고 주요 상품을 한눈에 볼 수 있도록 구성

**핵심 기능**:
- Hero 슬라이더 (자동 전환 배너)
- 베스트/신상품/특가 상품 섹션
- 최근 본 상품 섹션
- 검색 기능
- 장바구니 아이콘에 실시간 개수 표시

**구현 방법**:
- **Hero 슬라이더**: `setInterval`로 5초마다 자동 전환, 호버 시 일시정지
- **상품 그리드**: CSS Grid를 활용한 반응형 레이아웃 (모바일: 1열, 태블릿: 2열, 데스크톱: 4열)
- **상품 카드**: `products.js`의 `createProductCard()` 함수로 동적 생성
- **장바구니 개수**: `localStorage`에서 읽어와 실시간 업데이트

**어려웠던 점**:
- 슬라이더 자동 전환과 수동 전환 간 충돌 해결 → 상태 변수로 제어
- 모바일에서 상품 카드 이미지 비율 유지 → `object-fit: cover` 활용
- localStorage 데이터 동기화 → `updateCartCount()` 함수로 전역 관리

**개선 방향**:
- 이미지 lazy loading 적용 예정
- 상품 데이터를 서버 API로 전환
- 무한 스크롤 또는 페이지네이션 추가

---

### [상품 목록 페이지 (sub1.html)]

**구현 목표**: 다양한 필터와 정렬 옵션을 제공하여 사용자가 원하는 상품을 쉽게 찾을 수 있도록 구성

**핵심 기능**:
- 카테고리 필터 (사이드바)
- 가격대 필터
- 정렬 옵션 (인기순, 가격순 등)
- 검색 결과 표시
- 검색 결과 없음 안내 메시지

**구현 방법**:
- **검색 기능**: URL 파라미터(`?search=검색어`)를 읽어 상품 제목에서 필터링
- **상품 필터링**: `searchProducts()` 함수로 대소문자 구분 없이 검색
- **검색 결과 없음**: `showNoSearchResults()` 함수로 안내 메시지 및 메인으로 가기 버튼 표시
- **반응형 레이아웃**: 사이드바 + 메인 콘텐츠 (모바일에서는 사이드바 숨김)

**어려웠던 점**:
- 하드코딩된 상품 카드에 `data-product-id` 속성이 없어 장바구니 추가 실패 → 제목으로 상품 찾기 로직 추가
- 검색어가 없을 때와 있을 때 UI 전환 → 조건부 렌더링으로 해결

**개선 방향**:
- 실제 필터링 기능 구현 (현재는 UI만 존재)
- 페이지네이션 제거 완료 (사용자 요청)
- 필터 조합 기능 추가 예정

---

### [베스트 상품 페이지 (sub2.html)]

**구현 목표**: 인기 상품을 순위별로 강조하여 표시하고, 사용자의 구매 결정을 돕는 정보 제공

**핵심 기능**:
- TOP 3 상품 특별 강조 (큰 카드)
- 순위 배지 (1위: 트로피, 2-3위: 상 아이콘)
- 나머지 상품 그리드 표시
- 상품 정렬 기능

**구현 방법**:
- **TOP 3 카드**: `createTop3ProductCard()` 함수로 순위별 다른 스타일 적용
- **순위 배지**: SCSS 클래스(`rank-1`, `rank-2`, `rank-3`)로 배경색 구분 (인라인 스타일 제거)
- **그리드 레이아웃**: CSS Grid로 TOP 3는 3열, 나머지는 4열 배치
- **반응형**: 모바일에서는 1열, 태블릿에서는 2열로 자동 조정

**어려웠던 점**:
- 인라인 스타일을 SCSS 클래스로 전환 → 순위별 클래스 추가
- TOP 3 카드 크기 조정으로 레이아웃 깨짐 → `grid-column: span` 활용

**개선 방향**:
- 실제 판매량 기반 순위 계산 로직 추가
- 상품 비교 기능 추가 예정

---

### [장바구니 페이지 (sub3.html)]

**구현 목표**: 사용자가 선택한 상품을 확인하고 수량 조절, 삭제, 주문하기까지의 과정을 제공

**핵심 기능**:
- 장바구니 상품 목록 표시
- 수량 증가/감소 버튼
- 상품 삭제 기능
- 총 금액 자동 계산
- 장바구니가 비어있을 때 안내 메시지

**구현 방법**:
- **데이터 저장**: `localStorage`에 `cartItems` 배열로 저장
- **수량 변경**: `updateQuantity()` 함수로 수량 변경 후 localStorage 업데이트
- **금액 계산**: `calculateTotal()` 함수로 각 상품 가격 × 수량 합산
- **삭제 기능**: `removeFromCart()` 함수로 배열에서 제거 후 재렌더링

**어려웠던 점**:
- 수량 변경 시 총 금액이 실시간으로 업데이트되지 않음 → 이벤트 위임으로 해결
- localStorage 데이터 형식 통일 → `{id, title, price, quantity, image}` 객체 구조로 표준화

**개선 방향**:
- 옵션 선택 기능 추가 (색상, 사이즈 등)
- 주문하기 페이지 연결
- 쿠폰/할인 기능 추가 예정

---

### [마이페이지 (sub4.html)]

**구현 목표**: 사용자의 주문 내역, 찜한 상품, 리뷰, 회원정보를 한 곳에서 관리할 수 있도록 구성

**핵심 기능**:
- 탭 메뉴로 섹션 전환 (주문내역, 찜한 상품, 리뷰 관리, 회원정보 수정, 배송지 관리)
- 주문 내역 표시 (실제 상품 이미지 포함)
- 찜한 상품 그리드 표시
- 리뷰 작성/수정/삭제 UI
- 회원정보 수정 폼
- 배송지 관리 (기본 배송지 설정)

**구현 방법**:
- **탭 전환**: `initMyPageTabs()` 함수로 `data-panel` 속성 기반 섹션 표시/숨김
- **찜한 상품**: `loadWishlist()` 함수로 localStorage에서 찜한 상품 ID 읽어와 상품 데이터 매칭
- **리뷰 탭**: `initReviewTabs()` 함수로 "작성 가능한 리뷰" / "작성한 리뷰" 전환
- **폼 유효성 검사**: HTML5 `required` 속성 및 JavaScript 검증

**어려웠던 점**:
- 주문 내역 이미지가 placeholder로 표시됨 → 실제 상품 이미지 URL로 교체
- 인라인 스타일이 많아 유지보수 어려움 → 모든 스타일을 SCSS로 이동
- 찜한 상품이 없을 때와 있을 때 UI 전환 → 조건부 렌더링으로 해결

**개선 방향**:
- 실제 주문 데이터 연동
- 리뷰 작성 모달 추가
- 배송지 추가/수정 모달 구현 예정

---

### [상품 상세 페이지 (product-detail.html)]

**구현 목표**: 상품의 상세 정보를 제공하고, 옵션 선택, 수량 조절, 장바구니 추가 기능 제공

**핵심 기능**:
- 상품 이미지 갤러리
- 상품 정보 표시 (가격, 할인율, 별점, 리뷰 수)
- 옵션 선택 (색상, 사이즈 등)
- 수량 선택
- 장바구니 추가 / 바로구매 버튼
- 최근 본 상품에 자동 추가

**구현 방법**:
- **URL 파라미터**: `?id=상품ID`로 상품 데이터 로드
- **최근 본 상품**: `saveRecentProduct()` 함수로 localStorage에 저장 (최대 10개)
- **장바구니 추가**: `addToCart()` 함수로 옵션과 수량 포함하여 추가
- **이미지 갤러리**: 메인 이미지 + 썸네일 리스트

**어려웠던 점**:
- 옵션 선택 시 가격 변동 처리 → 옵션별 가격 데이터 구조 설계 필요
- 최근 본 상품 중복 방지 → 배열에서 기존 항목 제거 후 맨 앞에 추가

**개선 방향**:
- 이미지 확대/줌 기능 추가
- 상품 비교 기능 추가
- 리뷰 섹션 강화 (필터, 사진 리뷰)

---

## 🔧 기능별 핵심 구현 설명

### 1. 로그인 유효성 검사 로직

**현재 상태**: 로그인 페이지는 미구현 상태입니다.

**예상 구현 방법**:
```javascript
// 이메일 형식 검증
function validateEmail(email) {
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return regex.test(email);
}

// 비밀번호 강도 검증
function validatePassword(password) {
    return password.length >= 8 && 
           /[A-Z]/.test(password) && 
           /[0-9]/.test(password);
}
```

---

### 2. 필터링 알고리즘

**검색 기능** (`js/products.js`):
```javascript
function searchProducts(query) {
    // 모든 상품을 하나의 배열로 합치기
    const allProducts = [...best, ...new, ...sale];
    
    // 중복 제거 (같은 ID는 한 번만)
    const uniqueProducts = allProducts.filter((product, index, self) =>
        index === self.findIndex(p => p.id === product.id)
    );
    
    // 대소문자 구분 없이 검색
    const searchQuery = query.trim().toLowerCase();
    
    // 상품 제목에서 검색어 포함 여부 확인
    return uniqueProducts.filter(product => {
        const title = (product.title || '').toLowerCase();
        return title.includes(searchQuery);
    });
}
```

**동작 흐름**:
1. URL 파라미터에서 검색어 추출
2. 모든 상품 데이터를 하나로 합침
3. 제목에 검색어가 포함된 상품만 필터링
4. 결과가 없으면 안내 메시지 표시

---

### 3. 상태 관리 방식

**LocalStorage 활용**:

```javascript
// 장바구니 데이터 구조
{
    "cartItems": [
        {
            "id": 1,
            "title": "삼성 갤럭시 버즈3 프로",
            "price": 229000,
            "quantity": 2,
            "image": "https://..."
        }
    ]
}

// 저장
localStorage.setItem('cartItems', JSON.stringify(cartItems));

// 읽기
const cartItems = JSON.parse(localStorage.getItem('cartItems') || '[]');

// 업데이트
function updateCartCount() {
    const totalItems = cartItems.reduce((sum, item) => sum + item.quantity, 0);
    document.querySelector('.cart-count').textContent = totalItems;
}
```

**데이터 동기화**:
- 장바구니 추가/삭제 시 모든 페이지의 장바구니 아이콘 개수 자동 업데이트
- `updateCartCount()` 함수를 전역으로 호출하여 동기화

---

### 4. 이벤트 처리 흐름

**상품 카드 이벤트 연결** (`js/products.js`):

```javascript
function attachProductEvents() {
    // 장바구니 추가 버튼
    document.querySelectorAll('.add-to-cart-btn').forEach(button => {
        button.addEventListener('click', function() {
            const productCard = this.closest('.product-card');
            const productId = parseInt(productCard.dataset.productId);
            
            // 장바구니에 추가
            addToCart(productId);
            
            // 클릭 애니메이션
            this.style.transform = 'scale(0.95)';
            setTimeout(() => {
                this.style.transform = '';
            }, 200);
        });
    });
}
```

**이벤트 위임 패턴**:
- 동적으로 생성된 요소에도 이벤트가 작동하도록 부모 요소에 이벤트 리스너 등록
- `closest()` 메서드로 클릭된 요소의 부모 요소 찾기

---

##  문제 해결 사례

### 사례 1: 장바구니 아이콘 숫자가 보이지 않음

**발생한 오류**:
- 네비게이션의 장바구니 아이콘 옆에 숫자가 표시되지 않음

**원인 분석**:
1. HTML에 `<span class="cart-count">` 요소는 존재
2. JavaScript에서 `updateCartCount()` 함수는 정상 작동
3. CSS에서 `.cart-count` 스타일이 없거나 `display: none`으로 설정됨

**해결 방법**:
```scss
// style.scss에 추가
.cart-count {
    position: absolute;
    top: -8px;
    right: -8px;
    background: $color-error;
    color: $color-white;
    border-radius: 50%;
    width: 20px;
    height: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 12px;
    font-weight: $font-weight-bold;
}
```

---

### 사례 2: 상품목록 페이지에서 장바구니 추가가 작동하지 않음

**발생한 오류**:
- 상품목록 페이지의 "장바구니" 버튼 클릭 시 아무 반응 없음

**원인 분석**:
1. 하드코딩된 상품 카드에 `data-product-id` 속성이 없음
2. `attachProductEvents()` 함수가 `productId`를 찾지 못함
3. 상품 제목으로 상품을 찾는 로직이 없음

**해결 방법**:
```javascript
// productId가 없으면 제목으로 상품 찾기
if (!productId || isNaN(productId)) {
    const titleElement = productCard.querySelector('.product-title');
    if (titleElement) {
        const title = titleElement.textContent.trim();
        const allProducts = [...best, ...new, ...sale];
        const foundProduct = allProducts.find(p => p.title === title);
        if (foundProduct) {
            productId = foundProduct.id;
        }
    }
}
```

---

### 사례 3: 검색 결과가 없을 때 빈 화면 표시

**발생한 오류**:
- 검색 결과가 없을 때 아무것도 표시되지 않음

**원인 분석**:
1. 검색 결과가 없을 때의 UI가 구현되지 않음
2. 사용자에게 피드백이 없어 혼란 발생

**해결 방법**:
```javascript
function showNoSearchResults(query) {
    const productsGrid = document.querySelector('.products-grid');
    productsGrid.innerHTML = `
        <div class="search-no-results">
            <div class="no-results-icon">
                <i class="bi bi-search"></i>
            </div>
            <h2>"${query}"로 검색한 상품이 존재하지 않습니다</h2>
            <p>다른 검색어로 시도해보시거나, 메인 페이지로 돌아가세요.</p>
            <a href="index.html" class="btn btn-primary">메인으로 가기</a>
        </div>
    `;
}
```

---

### 사례 4: 인라인 스타일 사용으로 인한 유지보수 어려움

**발생한 오류**:
- JavaScript에서 HTML 생성 시 인라인 스타일을 많이 사용하여 CSS 관리가 어려움

**원인 분석**:
- 빠른 구현을 위해 인라인 스타일 사용
- 스타일 변경 시 JavaScript와 CSS 두 곳을 수정해야 함

**해결 방법**:
1. 모든 인라인 스타일을 SCSS 클래스로 전환
2. JavaScript에서는 클래스명만 추가
3. SCSS에서 일관된 스타일 관리

```javascript
// Before (인라인 스타일)
<div style="font-size: 64px; color: #ddd; margin-bottom: 20px;">

// After (SCSS 클래스)
<div class="empty-icon">
```

```scss
// style.scss
.empty-icon {
    font-size: 64px;
    color: $color-border-primary;
    margin-bottom: $spacing-md;
    opacity: 0.5;
}
```



---

## 반응형 브레이크포인트

```scss
// _variables.scss
$breakpoint-mobile: 767px;
$breakpoint-tablet: 1024px;
$breakpoint-desktop: 1200px;
```

- **모바일**: ~767px 
- **태블릿**: 768px ~ 1024px 
- **데스크톱**: 1025px ~ 

---

## 디자인 시스템

### 색상 팔레트
- **브랜드 메인**: `#0B488D` (파란색)
- **브랜드 서브**: `#1900d3` (진한 파란색)
- **액센트**: `#FFD912` (노란색)
- **에러**: `#ED2040` (빨간색)
- **성공**: `#27AE60` (초록색)

### 타이포그래피
- **제목**: 24px ~ 32px, Bold
- **본문**: 14px ~ 16px, Regular
- **작은 텍스트**: 12px ~ 13px, Regular

---

## 📝 학습 포인트

이 프로젝트를 통해 학습할 수 있는 내용:

1. **SCSS 활용**: 변수, 믹스인, 중첩을 통한 효율적인 CSS 작성
2. **반응형 디자인**: 미디어 쿼리와 유연한 레이아웃
3. **JavaScript 모듈화**: 기능별로 파일 분리하여 유지보수성 향상
4. **LocalStorage 활용**: 클라이언트 사이드 데이터 저장 및 관리
5. **이벤트 처리**: 이벤트 위임, 동적 요소 이벤트 연결
6. **접근성**: 시맨틱 HTML, ARIA 속성, 키보드 네비게이션

---

## 웹표준 및 웹 접근성 고려 사항

### 웹표준 준수

#### 1. HTML5 시맨틱 태그 사용

**사용한 태그와 목적**:

```html
<!-- 문서 구조를 의미 있게 표현 -->
<header>     <!-- 페이지 상단 헤더 -->
<nav>        <!-- 네비게이션 메뉴 -->
<main>       <!-- 메인 콘텐츠 영역 -->
<section>    <!-- 논리적 콘텐츠 구분 -->
<article>    <!-- 독립적인 콘텐츠 (상품 카드 등) -->
<footer>     <!-- 페이지 하단 푸터 -->
```

**왜 중요한가?**
- 검색 엔진이 페이지 구조를 이해할 수 있음 (SEO 향상)
- 스크린 리더 사용자가 콘텐츠를 더 쉽게 탐색 가능
- 코드 가독성 향상 및 유지보수 용이

**학습한 점**:
- `<div>` 대신 의미 있는 태그를 사용하면 코드가 더 명확해짐
- 시맨틱 태그는 스타일링뿐만 아니라 의미 전달이 목적

#### 2. 메타 태그 및 문서 정보

```html
<!DOCTYPE html>                    <!-- HTML5 문서 타입 선언 -->
<html lang="ko">                   <!-- 언어 지정 (스크린 리더용) -->
<meta charset="UTF-8">              <!-- 문자 인코딩 (한글 깨짐 방지) -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">  <!-- 반응형 설정 -->
<meta name="description" content="...">  <!-- SEO를 위한 페이지 설명 -->
```

**학습한 점**:
- `lang="ko"`를 지정하면 스크린 리더가 한국어로 읽어줌
- `viewport` 메타 태그 없이는 모바일에서 레이아웃이 깨짐
- `description`은 검색 결과에 표시되어 클릭률에 영향

### 웹 접근성 (WCAG 2.1 준수)

#### 1. ARIA (Accessible Rich Internet Applications) 속성

**사용한 ARIA 속성**:

```html
<!-- 버튼의 목적을 명확히 설명 -->
<button aria-label="검색 열기/닫기">...</button>
<button aria-label="메뉴 토글">...</button>
<a href="..." aria-label="장바구니">...</a>

<!-- 숨겨진 콘텐츠 상태 표시 -->
<div id="searchPanel" aria-hidden="true">...</div>
<input aria-expanded="false">  <!-- 드롭다운 열림/닫힘 상태 -->
```

**왜 중요한가?**
- 스크린 리더 사용자가 버튼의 기능을 이해할 수 있음
- 아이콘만 있는 버튼은 시각 장애인에게 의미 전달 불가 → `aria-label` 필수
- `aria-hidden="true"`로 불필요한 콘텐츠를 스크린 리더에서 숨김

**학습한 점**:
- 아이콘 버튼에는 반드시 `aria-label` 추가
- 동적으로 변경되는 UI는 `aria-expanded`, `aria-hidden` 등으로 상태 표시

#### 2. 키보드 접근성

**구현한 기능**:

```html
<!-- 건너뛰기 링크: 키보드 사용자가 본문으로 바로 이동 -->
<a class="skip-link" href="#main">본문 바로가기</a>

<!-- 포커스 가능한 요소에 명확한 포커스 스타일 -->
.skip-link:focus {
    transform: translateY(0);  /* 포커스 시 보이도록 */
    outline: 3px solid rgba(25, 0, 211, 0.35);
}
```

**학습한 점**:
- Tab 키로만 웹사이트를 사용하는 사람도 있음
- 모든 인터랙티브 요소는 키보드로 접근 가능해야 함
- 포커스 스타일을 명확히 해야 현재 위치를 알 수 있음

#### 3. 대체 텍스트 (Alt Text)

```html
<!-- 이미지에 의미 있는 대체 텍스트 제공 -->
<img src="logo.svg" alt="Elexa(일렉사) 로고">
<img src="product.jpg" alt="삼성 갤럭시 버즈3 프로">

<!-- 장식용 이미지는 빈 alt -->
<img src="decoration.png" alt="">
```

**학습한 점**:
- `alt` 속성은 이미지를 볼 수 없는 사용자를 위한 것
- 의미 있는 이미지는 설명을, 장식용은 빈 문자열
- SEO에도 도움이 됨 (검색 엔진이 이미지 내용 이해)

#### 4. 스크린 리더 전용 텍스트

```html
<!-- 시각적으로는 숨기지만 스크린 리더는 읽음 -->
<label for="searchInput" class="sr-only">상품 검색</label>
```

**CSS 구현**:
```scss
.sr-only {
    position: absolute !important;
    width: 1px !important;
    height: 1px !important;
    overflow: hidden !important;
    clip: rect(0, 0, 0, 0) !important;
}
```

**학습한 점**:
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

**학습한 점**:
- 일부 사용자는 보안을 위해 JavaScript를 비활성화
- 기본 HTML만으로도 콘텐츠를 볼 수 있어야 함 (점진적 향상)

---

## 각 섹션별 학습 내용

### HTML 구조 섹션

**배운 내용**:
- **시맨틱 HTML**: `<div>` 남발 대신 의미 있는 태그 사용
- **문서 구조**: `<header>`, `<main>`, `<footer>`로 논리적 구조화
- **메타 정보**: SEO와 접근성을 위한 메타 태그의 중요성

**어려웠던 점**:
- 처음에는 모든 것을 `<div>`로 만들려고 함
- 시맨틱 태그를 언제 사용해야 할지 헷갈림
- 해결: 각 태그의 의미를 공부하고, 콘텐츠의 성격에 맞게 선택

### CSS/SCSS 섹션

**배운 내용**:
- **SCSS 변수**: 색상, 폰트, 간격을 변수로 관리하여 일관성 유지
- **중첩 (Nesting)**: 부모-자식 관계를 명확히 표현
- **믹스인**: 반복되는 스타일을 함수처럼 재사용
- **반응형 디자인**: 미디어 쿼리로 다양한 화면 크기 대응

**어려웠던 점**:
- CSS가 길어지면 어디에 뭐가 있는지 찾기 어려움
- 반응형 브레이크포인트 설정이 헷갈림
- 해결: SCSS로 파일 분리하고, 변수로 브레이크포인트 통일

### JavaScript 섹션

**배운 내용**:
- **모듈화**: 기능별로 파일 분리하여 유지보수성 향상
- **이벤트 위임**: 동적 요소에도 이벤트가 작동하도록 부모에 리스너 등록
- **LocalStorage**: 클라이언트 사이드 데이터 저장
- **DOM 조작**: `querySelector`, `createElement` 등으로 동적 콘텐츠 생성

**어려웠던 점**:
- 동적으로 생성된 요소에 이벤트가 안 붙음
- LocalStorage 데이터 형식 관리가 어려움
- 해결: 이벤트 위임 패턴 학습, 데이터 구조 표준화

### 접근성 섹션

**배운 내용**:
- **ARIA 속성**: 스크린 리더 사용자를 위한 속성
- **키보드 네비게이션**: Tab 키로 모든 기능 사용 가능하도록
- **대체 텍스트**: 이미지에 의미 있는 설명 제공
- **포커스 관리**: 현재 위치를 명확히 표시

**어려웠던 점**:
- 접근성이 왜 중요한지 처음엔 이해 못함
- ARIA 속성을 언제 사용해야 할지 모름
- 해결: 스크린 리더 시뮬레이터로 직접 테스트해보니 중요성 이해

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

## 프로젝트에서 배운 점과 느낀 점 (왕초보 관점)

### 1. HTML/CSS를 배우면서

**처음에는**:
- HTML은 그냥 텍스트를 화면에 보여주는 거라고 생각했음
- CSS는 색깔 바꾸고 크기 조절하는 거라고만 생각

**지금은**:
- HTML은 **의미를 전달하는 것**이라는 걸 알게 됨
  - `<div>` 대신 `<header>`, `<nav>`, `<main>`을 쓰면 코드가 훨씬 읽기 쉬움
  - 검색 엔진도 이해하고, 스크린 리더 사용자도 이해할 수 있음
- CSS는 **레이아웃을 만드는 것**이라는 걸 배움
  - `display: flex`, `display: grid`를 알기 전에는 정렬이 너무 어려웠음
  - SCSS 변수를 쓰니까 색상 바꿀 때 한 곳만 수정하면 됨 (엄청 편함!)

**가장 어려웠던 부분**:
- 반응형 디자인: 모바일, 태블릿, 데스크톱에서 다르게 보이게 하는 게 어려웠음
- 해결: 미디어 쿼리를 하나씩 테스트하면서 배움
- Grid 레이아웃: 처음에는 `grid-template-columns`가 뭔지도 몰랐음
- 해결: 간단한 예제부터 만들어보면서 이해

### 2. JavaScript를 배우면서

**처음에는**:
- JavaScript는 너무 어려워 보였음
- 변수, 함수, 이벤트... 뭐가 뭔지도 모르겠음

**지금은**:
- **함수는 재사용 가능한 코드 블록**이라는 걸 이해함
  - 같은 코드를 여러 번 쓰지 않고 함수로 만들어서 호출
  - `createProductCard()` 함수 하나로 모든 상품 카드를 만들 수 있음
- **이벤트는 사용자 행동에 반응하는 것**이라는 걸 배움
  - 버튼 클릭, 입력, 스크롤 등 모든 게 이벤트
- **LocalStorage는 브라우저에 데이터 저장하는 것**
  - 장바구니에 담은 상품이 새로고침해도 남아있음 (신기함!)

**가장 어려웠던 부분**:
- 동적 요소에 이벤트가 안 붙는 문제
  - 처음에는 왜 안 되는지 몰랐음
  - 나중에 알게 된 것: 페이지 로드 후에 생성된 요소는 이벤트 리스너를 다시 붙여야 함
  - 해결: 이벤트 위임 패턴을 배워서 부모 요소에 리스너를 붙임
- 배열과 객체 다루기
  - `map()`, `filter()`, `find()` 같은 메서드가 처음에는 너무 어려웠음
  - 해결: 하나씩 콘솔에 찍어보면서 결과를 확인하면서 배움

### 3. 웹 접근성을 배우면서

**처음에는**:
- 접근성이 뭔지도 몰랐음
- 그냥 예쁘게 만들면 되는 거 아니야? 라고 생각

**지금은**:
- **모든 사람이 사용할 수 있어야 한다**는 걸 알게 됨
  - 시각 장애인도, 키보드만 쓰는 사람도, JavaScript를 끈 사람도
- **ARIA 속성의 중요성**을 배움
  - 아이콘만 있는 버튼은 스크린 리더가 읽을 수 없음
  - `aria-label`을 추가하면 "검색 열기/닫기"라고 읽어줌
- **시맨틱 HTML의 중요성**을 이해함
  - `<div>` 대신 `<header>`, `<nav>`를 쓰면 스크린 리더가 구조를 이해함

**가장 인상 깊었던 부분**:
- 스크린 리더 시뮬레이터로 테스트해봤을 때
  - 내가 만든 버튼이 "버튼"이라고만 읽히고 뭘 하는 건지 모름
  - `aria-label`을 추가하니 "검색 열기/닫기"라고 명확하게 읽어줌
  - 이때 접근성의 중요성을 진짜로 느낌

### 4. 프로젝트를 진행하면서

**처음에는**:
- 파일이 많아지니까 뭐가 뭔지 모르겠음
- 어디서 뭘 수정해야 할지 헷갈림

**지금은**:
- **파일을 기능별로 나누는 게 중요**하다는 걸 배움
  - `products.js`는 상품 관련, `cart.js`는 장바구니 관련
  - 나중에 수정할 때 어디를 봐야 할지 바로 알 수 있음
- **주석을 많이 쓰는 게 좋다**는 걸 배움
  - 나중에 내가 봐도, 다른 사람이 봐도 이해하기 쉬움
- **작은 것부터 하나씩 만드는 게 중요**하다는 걸 배움
  - 처음에는 모든 걸 한 번에 만들려고 했는데 실패
  - 하나씩 만들고 테스트하고, 다음 걸 추가하는 게 훨씬 쉬움

**가장 힘들었던 부분**:
- 버그를 찾는 것
  - 왜 안 되는지 모를 때가 너무 많았음
  - 해결: `console.log()`를 많이 찍어보면서 어디서 문제가 생기는지 찾음
- 코드가 길어지면 헷갈림
  - 해결: 함수로 나누고, 파일로 나누면서 정리

**가장 뿌듯했던 부분**:
- 장바구니 기능이 완성되었을 때
  - 상품을 담고, 수량을 바꾸고, 삭제하는 게 다 작동함
  - 새로고침해도 데이터가 남아있음 (LocalStorage의 힘!)
- 반응형으로 만들었을 때
  - 모바일에서도, 태블릿에서도, 데스크톱에서도 예쁘게 보임
  - 이게 진짜 웹사이트구나! 라는 느낌

### 5. 앞으로 배우고 싶은 것

- **프레임워크**: React나 Vue 같은 걸 배우면 더 쉽게 만들 수 있을 것 같음
- **백엔드**: 지금은 데이터를 하드코딩했는데, 서버에서 가져오고 싶음
- **성능 최적화**: 이미지 lazy loading, 코드 압축 등
- **테스트**: 내 코드가 제대로 작동하는지 자동으로 확인하는 방법


---

##  기여자

프로젝트 개발 및 문서화: 초보자 관점에서 이해하기 쉽도록 상세한 주석과 설명을 포함했습니다.
