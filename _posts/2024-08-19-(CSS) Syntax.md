---
categories: 
 - CSS
layout: single
title: "(CSS) 문법 요약"
---

CSS(Cascading Style Sheets)는 HTML이나 XML로 작성된 문서의 스타일을 정의하기 위한 언어입니다. CSS는 웹 페이지의 레이아웃, 색상, 폰트, 간격 등 시각적인 요소를 제어합니다. CSS 구문을 이해하기 위해서는 기본적인 구조와 개념을 잘 이해하는 것이 중요합니다. 아래는 CSS 구문에 대한 정리입니다.

### 1. 기본 구문
CSS 구문은 일반적으로 **선택자(selector)**와 **선언 블록(declaration block)**으로 구성됩니다.

- **선택자(Selector)**: 스타일을 적용할 HTML 요소를 선택합니다.
- **선언 블록(Declaration Block)**: 중괄호 `{}` 안에 속성(property)과 값(value)을 지정하여 스타일을 정의합니다.

#### 예시
```css
선택자 {
  속성1: 값1;
  속성2: 값2;
  ...
}
```

#### 예시 코드
```css
p {
  color: blue;
  font-size: 16px;
}
```
위 예제는 HTML 문서의 모든 `<p>` 요소에 대해 글자 색상을 파란색으로 하고 글자 크기를 16픽셀로 설정하는 CSS 규칙입니다.

### 2. 선택자(Selector)의 종류
CSS에는 다양한 선택자가 있습니다. 주요 선택자는 다음과 같습니다:

- **요소 선택자 (Element Selector)**: 특정 HTML 요소를 선택합니다.
  ```css
  h1 {
    color: red;
  }
  ```

- **클래스 선택자 (Class Selector)**: 특정 클래스 속성을 가진 요소를 선택합니다. 클래스 이름 앞에 `.`을 붙입니다.
  ```css
  .button {
    background-color: green;
  }
  ```

- **아이디 선택자 (ID Selector)**: 특정 아이디 속성을 가진 요소를 선택합니다. 아이디 이름 앞에 `#`을 붙입니다.
  ```css
  #header {
    font-size: 24px;
  }
  ```

- **자손 선택자 (Descendant Selector)**: 특정 요소의 자손인 요소를 선택합니다.
  ```css
  div p {
    color: black;
  }
  ```

- **속성 선택자 (Attribute Selector)**: 특정 속성을 가진 요소를 선택합니다.
  ```css
  input[type="text"] {
    border: 1px solid #000;
  }
  ```

### 3. CSS 속성(Property)와 값(Value)
CSS에서 속성은 스타일링하려는 요소의 특정 측면을 정의합니다. 각 속성은 값을 가질 수 있으며, 이는 해당 속성에 대한 특정 스타일링을 적용합니다.

#### 예시
```css
p {
  color: red;  /* 글자 색상을 빨간색으로 설정 */
  text-align: center;  /* 텍스트를 중앙 정렬 */
}
```

### 4. 상속(Inheritance)
CSS 속성 중 일부는 상위 요소로부터 하위 요소로 상속될 수 있습니다. 예를 들어, `font-family`나 `color` 속성은 상속됩니다.

```css
body {
  color: black;
  font-family: Arial, sans-serif;
}

p {
  font-size: 16px;
}
```
위의 예제에서, `<body>` 요소의 글자 색상과 폰트 설정은 하위 요소인 `<p>` 요소에도 상속됩니다.

### 5. 우선순위(Cascade)
CSS는 "Cascading"이라는 이름에서 알 수 있듯이, 우선순위 규칙에 따라 스타일을 적용합니다. 우선순위는 다음 요소에 의해 결정됩니다:

1. 인라인 스타일 (`style` 속성을 사용하여 HTML 요소에 직접 작성된 스타일)이 가장 높은 우선순위를 가집니다.
2. 아이디 선택자 (`#id`)의 우선순위가 높습니다.
3. 클래스 선택자 (`.class`), 속성 선택자(`[type="text"]`), 가상 클래스 선택자 (`:hover`)는 그 다음 우선순위를 가집니다.
4. 요소 선택자 (`element`)는 가장 낮은 우선순위를 가집니다.
5. 중요 선언 (`!important`)이 붙은 스타일은 무조건 최우선으로 적용됩니다.

### 6. 주석(Comment)
CSS 코드에서 주석은 `/* */` 사이에 작성됩니다. 주석은 브라우저에서 무시되며 코드의 가독성을 높이기 위해 사용됩니다.

```css
/* 이 부분은 주석입니다 */
p {
  color: blue; /* 글자 색상 설정 */
}
```

### 7. CSS 파일의 구조
보통 CSS는 별도의 파일로 작성되며, HTML 파일에서 `<link>` 태그를 사용해 연결합니다.

#### CSS 파일 (`styles.css`)
```css
body {
  background-color: #f0f0f0;
}

h1 {
  color: #333;
}
```

#### HTML 파일 (`index.html`)
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <h1>Hello World</h1>
</body>
</html>
```

### 8. 미디어 쿼리(Media Queries)
미디어 쿼리를 사용하면 디바이스의 특성에 따라 다른 스타일을 적용할 수 있습니다.

```css
@media (max-width: 600px) {
  body {
    background-color: lightblue;
  }
}
```
위 예제는 화면 너비가 600px 이하일 때 배경색을 라이트블루로 변경합니다.

### 결론
CSS는 웹 페이지의 시각적 표현을 담당하는 중요한 기술입니다. 선택자, 속성, 우선순위 등의 기본 개념을 잘 이해하면 더 복잡하고 아름다운 웹 페이지를 디자인할 수 있습니다.