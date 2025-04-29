#  CSS Position, Float, Clear, 기타 속성 정리

##  Position 속성

- **한 요소에 두 개의 `position` 속성 동시 적용 불가**

###  relative
- 자기 자신 기준으로 이동 (원래 위치를 기준)
- 부모가 없으면 뷰포트 기준 이동
- 부모가 이동하면, 자식은 이동한 부모를 기준으로 움직임

```css
.parent {
  position: relative;
  top: 10px;
  left: 10px;
}
.child {
  position: relative;
  top: 10px;
  left: 10px;
}
```

---

###  absolute
- 가장 가까운 **relative/absolute/fixed**를 가진 조상 기준
- 조상이 없으면 **뷰포트** 기준
- 조상에 `height` 설정 필요
- 문서 흐름에서 제거되며, 부모 요소가 자식 크기를 인식하지 못해 **높이 0** 됨 (테두리는 보임)

---

###  fixed
- **뷰포트** 기준 절대 위치
- `width` 지정 필요 (예: `width: 100%`)

---

###  static
- 기본값 (특별한 위치 지정 없음)

---

###  z-index
- `position` 또는 `flex item`에서만 적용 가능
- 수치가 클수록 위에 위치
- 양수, 음수 모두 가능

---

##  flex item
- `display: flex` 또는 `display: inline-flex` 설정된 부모의 자식 요소

---

##  Float

| 속성  | 설명 |
|-------|------|
| `left`, `right` | 요소를 왼쪽 또는 오른쪽으로 띄움 |

###  주의사항
- **너비 자동 조정**: 콘텐츠 크기만큼
- **너비 초과 주의**: 부모 너비 초과 금지
- **높이**: 퍼센트 단위 사용 시 부모에 높이 설정 필요

---

##  Clear (플로트 해제)

### 1. 다음 요소에 clear 적용
```css
.clear { clear: both; }
```

### 2. 부모에 overflow:hidden 적용
```css
.parent { overflow: hidden; }
```

### 3. clearfix 해킹 (추천)
```css
.clear::after {
  content: '';
  display: block;
  clear: both;
}
```
→ 부모에 `.clear` 클래스를 주어 적용

---

##  ul 관련
- 리스트 스타일 제거 시 불릿 사라짐
- **padding도 제거해야** 여백 사라짐

```css
ul {
  list-style: none;
  padding: 0;
}
```

---

## 🔹 a 태그 스타일링

- 하이퍼링크 표시 제거

```css
a {
  text-decoration: none;
  color: inherit; /* 또는 원하는 색 지정 */
}
```

- `a` 태그에 `padding` 적용 시
  → 인라인이라 겹침 → `display: block;`으로 변경

---

##  nav 태그
- **메뉴 영역을 감싸는 블록 태그**
- 메뉴를 고정할 때는 `ul`에 직접 `fixed` 주지 말고 `nav`에 줘야 함

---

##  box-shadow

```css
box-shadow: 가로거리 세로거리 흐림정도 번짐정도 색상;
```
예시:
```css
box-shadow: 2px 4px 6px 0 rgba(0,0,0,0.2);
```

---

##  a 태그 상태별 CSS 순서

```css
a:link { }    /* 방문 전 */
a:visited { } /* 방문 후 */
a:hover { }   /* 마우스 오버 */
a:active { }  /* 클릭 순간 */
```

---

