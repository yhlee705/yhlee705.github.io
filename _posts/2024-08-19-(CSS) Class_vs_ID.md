---
categories: 
 - CSS
layout: single
title: "(CSS) Class와 ID의 차이"
---

`class`와 `id`는 HTML 요소에 스타일을 적용하기 위해 사용하는 두 가지 중요한 속성입니다. 둘 다 CSS에서 선택자로 사용되지만, 목적과 사용 방법에서 차이가 있습니다.

### 1. **용도**

- **`class`**: 여러 요소에 동일한 스타일을 적용하고자 할 때 사용됩니다. 하나의 `class`는 여러 요소에서 반복적으로 사용될 수 있습니다. 따라서 재사용성이 높습니다.
  
- **`id`**: 문서 내에서 특정한 하나의 요소에만 스타일을 적용할 때 사용됩니다. 각 `id`는 문서에서 고유해야 하며, 하나의 요소에만 적용될 수 있습니다.

### 2. **선택자 표기법**

- **`class`**: CSS에서 클래스 선택자는 `.` (점)을 사용하여 정의합니다.
  ```css
  .my-class {
    color: blue;
  }
  ```
  HTML에서는 `class` 속성을 통해 적용합니다.
  ```html
  <div class="my-class">Hello, World!</div>
  ```

- **`id`**: CSS에서 아이디 선택자는 `#` (샵)을 사용하여 정의합니다.
  ```css
  #my-id {
    color: red;
  }
  ```
  HTML에서는 `id` 속성을 통해 적용합니다.
  ```html
  <div id="my-id">Hello, World!</div>
  ```

### 3. **적용 대상**

- **`class`**: 동일한 클래스를 여러 요소에 사용할 수 있습니다. 예를 들어, 여러 `<div>`, `<p>`, `<span>` 요소에 같은 `class`를 지정할 수 있습니다.
  ```html
  <div class="my-class">First</div>
  <p class="my-class">Second</p>
  <span class="my-class">Third</span>
  ```

- **`id`**: 하나의 `id`는 문서에서 유일해야 합니다. 동일한 `id`를 여러 요소에 사용하면 HTML 문서가 유효하지 않게 됩니다.
  ```html
  <div id="unique-id">This is unique</div>
  ```

### 4. **우선순위 (Specificity)**

CSS에서 동일한 요소에 대해 `class`와 `id` 선택자가 동시에 적용될 경우, **`id` 선택자**가 더 높은 우선순위를 가집니다. 따라서 `id`로 정의된 스타일이 우선 적용됩니다.

- **우선순위 예시**
  ```css
  .my-class {
    color: blue;
  }

  #my-id {
    color: red;
  }
  ```
  ```html
  <div id="my-id" class="my-class">This text will be red</div>
  ```
  이 경우, `id`가 더 높은 우선순위를 가지므로 텍스트 색상은 빨간색이 됩니다.

### 5. **사용 시 고려 사항**

- **`class`**: 재사용 가능한 스타일을 정의할 때 사용합니다. 다양한 요소에 동일한 스타일을 적용하고자 할 때 유용합니다.

- **`id`**: 특정 요소를 고유하게 식별해야 할 때 사용합니다. 예를 들어, 자바스크립트에서 특정 요소를 선택하거나, 앵커 링크와 같이 문서 내에서 특정 위치로 이동할 때 사용됩니다.

### 6. **예시**
#### `class` 사용 예시
```css
.button {
  background-color: green;
  color: white;
  padding: 10px;
}
```
```html
<button class="button">Click me</button>
<button class="button">Submit</button>
```

#### `id` 사용 예시
```css
#main-header {
  font-size: 24px;
  color: blue;
}
```
```html
<h1 id="main-header">Welcome to My Website</h1>
```

### 결론
- **`class`**는 여러 요소에 동일한 스타일을 적용할 때 사용되고, 문서 내에서 여러 번 사용될 수 있습니다.
- **`id`**는 특정한 하나의 요소에만 스타일을 적용할 때 사용되며, 문서 내에서 고유해야 합니다.
- 우선순위 측면에서 `id`는 `class`보다 더 높은 우선순위를 가집니다. 

따라서 상황에 따라 적절하게 `class`와 `id`를 선택해 사용하는 것이 중요합니다.