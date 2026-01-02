# Html 실습_25.11.30


**사이트 바로가기 -> [시험기간 공부하기 좋은 경희대학교 주변 카페 추천](https://ppck75.github.io/html_khu-cafe/)

## 카페 추천 웹사이트 제작기

### 1. 프로젝트 제목




**카페 추천 웹사이트 제작기**

---

### 2. 프로젝트 소개

시험기간이 되면 “어디가 조용하지?”, “콘센트 많은 카페는 어디지?”, “늦게까지 여는 곳 없나?” 같은 고민이 늘어납니다. 그래서 **경희대학교 주변에서 실제로 공부하기 좋았던 카페 6곳**을 직접 선정해, **정문·후문·회기역** 기준으로 한눈에 볼 수 있는 **싱글 페이지 웹사이트**로 정리했습니다.

이 프로젝트의 목표는 단순한 리스트가 아니라, 사용자가 **필요한 구역을 빠르게 찾아가고**, 각 카페의 **좌석/분위기/공부 적합 포인트**를 짧게 읽고 바로 **지도까지 연결**될 수 있도록 만드는 것이었습니다.

---

### 3. 이 페이지가 하는 일(사용자의 경험 흐름)

이 웹사이트는 사용자가 “시험기간 카공 카페”를 빠르게 찾고 결정하는 흐름으로 설계했습니다.

1. 사용자는 페이지에 들어오자마자 **상단 고정 메뉴바**에서 구역을 선택합니다.

* `정문 근처 카페 / 후문 근처 카페 / 회기역 근처 카페`

2. 메뉴를 클릭하면 해당 구역 섹션으로 **바로 이동(앵커 이동)**합니다.

* `#front-gate`, `#back-gate`, `#hoegi`

3. 각 구역에는 카드형으로 카페가 정리되어 있어서, 

* **도보 거리**, **공부 포인트(콘센트/좌석/분위기)**, **추천 메뉴**를 빠르게 확인할 수 있습니다.

4. 메뉴판/공간 사진을 보며 분위기를 확인하고,
5. “네이버 지도에서 위치 보기” 버튼으로 **바로 이동**해 방문 결정을 마무리합니다.

---

### 4. 핵심 코드

이 페이지의 핵심은 “사용자가 원하는 구역으로 즉시 이동 + 카드형으로 정보 전달”입니다.

#### 4-1. 상단 고정 메뉴바 + 앵커 이동

```html
<nav class="nav-bar">
  <a href="#front-gate">정문 근처 카페</a>
  <a href="#back-gate">후문 근처 카페</a>
  <a href="#hoegi">회기역 근처 카페</a>
</nav>
```

```css
.nav-bar {
  position: sticky;
  top: 0;
  z-index: 100;
  background: #ffffff;
  border-bottom: 1px solid #e1e4ea;
  display: flex;
  justify-content: center;
  gap: 24px;
  padding: 10px 16px;
}
```

#### 4-2. 카드형 레이아웃(반응형)

```css
.cafe-list {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
}

.cafe-card {
  background: var(--card-bg);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 14px 16px;
  flex: 1 1 280px;
  box-shadow: 0 6px 14px rgba(0,0,0,0.05);
}
```

#### 4-3. 섹션 등장 애니메이션(fadeUp)

```css
.section {
  margin-top: 24px;
  opacity: 0;
  transform: translateY(20px);
  animation: fadeUp 0.8s ease-out forwards;
}

@keyframes fadeUp {
  to { opacity: 1; transform: translateY(0); }
}
```

---

### 5. 구현 기능

이번 웹사이트에서 구현한 기능은 다음과 같습니다.

* **구역별 카페 분류**: 정문/후문/회기역 기준으로 사용자 탐색 동선을 단순화
* **상단 메뉴바 고정(sticky)**: 스크롤 중에도 메뉴 접근이 가능해 이동이 빠름
* **앵커 링크 이동**: 클릭 한 번으로 원하는 섹션으로 즉시 점프
* **카드형 정보 제공**: 핵심 정보(거리/좌석/콘센트/분위기/추천 메뉴)를 빠르게 스캔 가능
* **이미지 표시**: 메뉴판/공간 사진으로 분위기 판단 보조
* **지도 버튼 연결**: 네이버 지도로 바로 이동해 실제 방문 결정까지 이어짐
* **반응형 레이아웃**: PC에서는 2열 느낌, 모바일에서는 이미지가 1장씩 크게 보이도록 조정

---

### 6. 스타일링

디자인은 “공부할 때 보기 편한 깔끔함”에 집중했습니다.

#### 6-1. 컬러 시스템(CSS 변수)

```css
:root {
  --primary: #2c3e50;
  --accent: #e67e22;
  --border: #ddd;
  --bg: #f5f6fa;
  --card-bg: #ffffff;
}
```

* **primary(딥 네이비 계열)**로 제목/정보를 안정적으로 잡고
* **accent(오렌지 계열)**로 강조 문구에 포인트를 줬습니다.
* 전체 배경은 밝게(`--bg`) 해서 카드가 떠 보이도록 구성했습니다.

#### 6-2. 가독성 중심 레이아웃

* `max-width: 960px`로 너무 넓지 않게 잡아 **눈이 덜 피로**하게
* 카드에 `shadow`를 줘서 섹션 구분이 자연스럽게 되도록

#### 6-3. 이미지 배치 전략

* 기본 카드는 이미지 `width: 50%`로 **한 줄에 두 장**
* 회기역 섹션처럼 단일 이미지는 `width: 100%`로 **크게 강조**
* 모바일에서는 `width: 100%`로 전환해 **한 장씩 보기 편하게** 구성했습니다.

### 7. 느낀점

이번 프로젝트를 통해 배운 점은 웹페이지를 이루고 있는 HTML+CSS+JS의 기본적인 구조를 이해하고 있다면,
AI의 도움을 통해 웹 페이지 개발도 충분히 가능하다는 것이다.

물론, 웹 페이지의 기본 구조 특히 그 뼈대가 되는 HTML에 대한 기본적인 이해가 반드시 필요하다. 이러한 이해와 웹을 구성할 신박한 아이디어가 결합한다면, 관련 전공이 아니더라고 웹 페이지를 그럴싸하게 만들 수 있다는 것이다.

디자인의 경우 AI가 있다면, 얼마든지 구현할 수 있다. 

모두가 AI를 사용할 수 있지만, 그 기본적인 구조를 이해하고 있는 사람과 그렇지 못한 사람의 결과물은 반드시 다를 것이다. 

데이터 사이언티스트는 커뮤니케이션 능력이 중요하다. 후에 내가 협업할 동료가 웹 개발자일 수도 있고 프로그래머일 수 있다. 그러므로 웹 개발의 기본적인 구조를 이해하는 것은 나에게 큰 강점이 될 것이다. 


## 프로젝트의 핵심을 요약하자면... 

1.페이지 성격: 시험기간 카공 카페 추천 싱글 페이지

2.핵심 UX: 상단 sticky 메뉴 → 섹션 앵커 이동

3.구성: 정문/후문/회기역 3구역 × 카드형 리스트

4.카드 구성: 거리/특징/추천메뉴/이미지/지도 버튼

5.디자인: CSS 변수 기반 톤 + 카드 그림자 + 반응형

6.기술 포인트: fadeUp 애니메이션(딜레이 방식은 개선 여지 있음)



##내가 작성한 HTML 코드 전체 

*텍스트로 작성하기 위해 스타일 부분은 주석처리 하였습니다.*


<!-- <title>경희대 주변 시험기간 카공 카페 추천</title> -->

<!-- =========================
     디자인(CSS) 코드: 비적용 처리
     아래 <style> 전체를 HTML 주석으로 감쌌습니다.
     ========================= -->
<!--
<style>
    :root {
        --primary: #2c3e50;
        --accent: #e67e22;
        --border: #ddd;
        --bg: #f5f6fa;
        --card-bg: #ffffff;
    }

    * { box-sizing: border-box; }

    body {
        margin: 0;
        font-family: -apple-system, BlinkMacSystemFont, "Apple SD Gothic Neo",
                     "Noto Sans KR", "Malgun Gothic", sans-serif;
        background: var(--bg);
        color: #333;
        line-height: 1.6;
    }

    /* 상단 메뉴바 */
    .nav-bar {
        position: sticky;
        top: 0;
        z-index: 100;
        background: #ffffff;
        border-bottom: 1px solid #e1e4ea;
        display: flex;
        justify-content: center;
        gap: 24px;
        padding: 10px 16px;
    }

    .nav-bar a {
        text-decoration: none;
        color: var(--primary);
        font-weight: 600;
        font-size: 14px;
        padding: 6px 10px;
        border-radius: 999px;
        transition: background 0.2s, color 0.2s;
    }

    .nav-bar a:hover {
        background: var(--primary);
        color: #ffffff;
    }

    .page-wrap {
        max-width: 960px;
        margin: 0 auto;
        padding: 20px 16px 40px;
    }

    #title {
        color: var(--primary);
        font-size: 28px;
        text-align: center;
        font-weight: bold;
        margin-bottom: 8px;
    }

    .subtitle {
        text-align: center;
        font-size: 15px;
        color: #555;
    }

    .highlight {
        color: var(--accent);
        font-weight: bold;
    }

    /* 섹션 공통 + 애니메이션 */
    .section {
        margin-top: 24px;
        opacity: 0;
        transform: translateY(20px);
        animation: fadeUp 0.8s ease-out forwards;
    }

    /* 순서별로 살짝 시간차 애니메이션 */
    .section:nth-of-type(1) { animation-delay: 0.0s; }
    .section:nth-of-type(2) { animation-delay: 0.1s; }
    .section:nth-of-type(3) { animation-delay: 0.2s; }
    .section:nth-of-type(4) { animation-delay: 0.3s; }

    @keyframes fadeUp {
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    .section h2 {
        color: #34495e;
        border-left: 4px solid #3498db;
        padding-left: 10px;
        font-size: 20px;
        margin-bottom: 14px;
    }

    /* 카드형 카페 레이아웃 */
    .cafe-list {
        display: flex;
        flex-wrap: wrap;
        gap: 16px;
    }

    .cafe-card {
        background: var(--card-bg);
        border: 1px solid var(--border);
        border-radius: 12px;
        padding: 14px 16px;
        flex: 1 1 280px;
        box-shadow: 0 6px 14px rgba(0,0,0,0.05);
    }

    .cafe-name {
        color: var(--primary);
        font-weight: 700;
        font-size: 16px;
        margin-bottom: 6px;
    }

    .cafe-meta {
        font-size: 13px;
        color: #777;
        margin-bottom: 6px;
    }

    .cafe-card ul {
        list-style-type: disc;
        padding-left: 20px;
        margin: 6px 0 8px;
        font-size: 14px;
    }

    .cafe-card ul li {
        margin-bottom: 2px;
    }

    /* 이미지 영역: 가로 배치 */
    .cafe-images {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 8px;
        margin-top: 8px;
    }

    img.cafe-img {
        width: 50%;          /* 기존 25%에서 2배로 확대 */
        height: auto;
        border-radius: 10px;
        display: block;
    }

    /* 회기역 섹션의 단일 이미지는 더 크게 (기존보다 2배 → 100%) */
    img.cafe-img-large {
        width: 100%;
        height: auto;
        border-radius: 10px;
        display: block;
    }

    .btn-row {
        margin-top: 10px;
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
    }

    .btn-map {
        display: inline-block;
        font-size: 13px;
        padding: 6px 10px;
        border-radius: 999px;
        text-decoration: none;
        border: 1px solid #ccc;
        background: #ffffff;
        color: var(--primary);
    }

    .btn-map:hover {
        background: #ecf3ff;
        border-color: #b3c5e6;
    }

    @media (max-width: 600px) {
        #title { font-size: 22px; }
        img.cafe-img { width: 100%; }  /* 모바일에서는 한 장씩 크게 */
    }
</style>
-->

<!-- 상단 메뉴바 -->
<nav class="nav-bar">
    <a href="#front-gate">정문 근처 카페</a>
    <a href="#back-gate">후문 근처 카페</a>
    <a href="#hoegi">회기역 근처 카페</a>
</nav>

<div class="page-wrap">

    <!-- 제목 섹션 -->
    <header class="section">
        <h1 id="title">시험기간 공부하기 좋은<br>경희대학교 주변 카페 추천</h1>
        <p class="subtitle">
            경희대 4학년이 직접 선정한 <span class="highlight">카공 성지 6곳</span><br>
            정문 · 후문 · 회기역 기준으로 정리해봤어요.
        </p>
    </header>

    <!-- 1. 정문 근처 -->
    <section class="section" id="front-gate">
        <h2>1. 정문 근처 추천 카페</h2>

        <div class="cafe-list">

            <!-- 브루앤바이트 -->
            <div class="cafe-card">
                <div class="cafe-name">📍 브루앤바이트</div>
                <div class="cafe-meta">정문 도보 3분</div>
                <ul>
                    <li>넓은 책상 + 1인석, 단체석(팀플도 여유롭게 가능)</li>
                    <li>콘센트 많음 → 장시간 공부에 최적</li>
                    <li>메뉴 다양해서 시험기간 내내 질리지 않음</li>
                    <li>추천: 핑크소금 커피, 젤라또</li>
                </ul>

                <div class="cafe-images">
                    <img class="cafe-img" src="https://ldb-phinf.pstatic.net/20250717_270/1752730481922lTEIy_PNG/Image_2025-07-17_13_58_34.png" alt="브루앤바이트 메뉴판 1">
                    <img class="cafe-img" src="https://ldb-phinf.pstatic.net/20250717_51/17527304738728fWtf_PNG/Image_2025-07-17_13_58_18.png" alt="브루앤바이트 메뉴판 2">
                </div>

                <div class="btn-row">
                    <a class="btn-map" href="https://map.naver.com/p/search/브루앤바이트%20경희대" target="_blank">네이버 지도에서 위치 보기</a>
                </div>
            </div>

            <!-- 투썸플레이스 경희대점 -->
            <div class="cafe-card">
                <div class="cafe-name">📍 투썸플레이스 경희대점</div>
                <div class="cafe-meta">정문 도보 2분 · 새벽 2시까지</div>
                <ul>
                    <li>콘센트 풍부해서 노트북 공부하기 좋음</li>
                    <li>적당한 백색소음으로 집중 + 편안함 공존</li>
                    <li>새벽까지 열려서 벼락치기 할 때 필수 스팟</li>
                    <li>추천: 아이스크림 카페라떼, 떠먹는 스트로베리 초콜릿 생크림</li>
                </ul>

                <div class="cafe-images">
                    <img class="cafe-img" src="https://ldb-phinf.pstatic.net/20170614_284/1497422994392LUmmG_JPEG/18-1.jpg" alt="투썸플레이스 메뉴판 1">
                    <img class="cafe-img" src="https://ldb-phinf.pstatic.net/20170614_27/1497422994531DvuE9_JPEG/18-2.jpg" alt="투썸플레이스 메뉴판 2">
                    <img class="cafe-img" src="https://ldb-phinf.pstatic.net/20170614_279/1497422994695Rg5Wb_JPEG/18-3.jpg" alt="투썸플레이스 메뉴판 3">
                </div>

                <div class="btn-row">
                    <a class="btn-map" href="https://map.naver.com/p/search/투썸플레이스%20경희대점" target="_blank">네이버 지도에서 위치 보기</a>
                </div>
            </div>

        </div>
    </section>

    <!-- 2. 후문 근처 -->
    <section class="section" id="back-gate">
        <h2>2. 후문 근처 추천 카페</h2>

        <div class="cafe-list">

            <!-- 컴플리트커피 -->
            <div class="cafe-card">
                <div class="cafe-name">📍 컴플리트커피</div>
                <div class="cafe-meta">후문 도보 3분</div>
                <ul>
                    <li>밝고 조용한 분위기 → 집중 잘 됨</li>
