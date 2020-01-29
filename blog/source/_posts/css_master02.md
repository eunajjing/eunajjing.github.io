# CSS 마스터 클래스02

> 해당 게시글은 노마드코더의 [CSS 마스터 클래스](https://academy.nomadcoders.co/courses/enrolled/360503) 강의를 듣고 요약한 것입니다. 저작권 문제가 발생할 시 삭제될 수 있습니다.

## `PostCSS`

`parcel-bundler`를 글로벌로 깔아준 상황에서 프로젝트 작업

```json
{
  "name": "postCSS",
  "version": "1.0.0",
  "license": "MIT",
  "scripts": {
    "start": "parcel index.html"
  },
  "dependencies": {
    "postcss-preset-env": "^6.7.0"
  },
  "postcss": {
    "plugins": {
      "postcss-preset-env": {
        "stage": 2
      }
    }
  }
}
```

> Vscode 상에서는 `postcss-language` 확장프로그램을 깔았다.

### `matches`

```css
li:matches(:nth-child(even), .target) {
  /* l1 태그의 짝수 태그와 target 클래스 이름을 가지고 있는 대상에게 적용
    만약 대상이 짝수가 아니더라도 적용 된다 */
  background-color: blue;
}
```

### `not`

```css
li:not(.target) {
  /* li 태그에게 적용하되 클래스 이름이 target이 아닌 대상에게 적용 */
  background-color: blue;
}
```

### `CSS Variables`

`CSS` 내 변수처럼 `CSS` 스타일이 지정이 가능

```css
:root {
  --awesomeColor: 1px solid red;
}

li:first-child a {
  border: var(--awesomeColor);
}
```

### `@custom-selector`

```css
@custom-selector :--headers h1, h2, h3, h4, h5, h6;
/* h1, h2, h3, h4, h5, h6를 --headers라는 이름으로 지정하고 */

:--headers {
  color: purple;
}
/* 부른다 */
```

### `@custom-media`

```css
@custom-media --ipad-size (450px < width <= 850px);
/* 정의하고*/

@media (--ipad-size) {
  body {
    background-color: red;
  }
}
/* 사용 */
```

### `color-mod`

색을 바꿀 때 사용

```css
a {
  color: yellow;
}

a:hover {
  color: color-mod(yellow /* 쓸 수 있는 키워드 삽입 */);
}
```

### `gray()`

```css
h1 {
  color: gray(100);
  /* 얼마나 회색 빛을 띄게 하고 싶은지를 %로 적는다
  	0이 완전한 검정색 */
}
```

### `system-ui`

`OS`에 자동으로 설정되어 있는 값을 지정

```css
p {
  font-family: system-ui;
}
```

### `Nesting Rules`

#### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Advanced CSS</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <main>
      <section>
        <li><a href="/">hello world</a></li>
      </section>
    </main>
  </body>
</html>
```

#### `styles.css`

```css
main {
  /* main 관련 css 적고 */
  & section {
    /* section 관련 css 적고 */
    & li {
      /* li 관련 css 적고 */
      & a {
        /* a 관련 css 적고 */
        &:hover {
          /* hover 되었을 때 css 적기 */
        }
      }
    }
  }
}
```

## [`CSS grid kiss`](https://sylvainpolletvillard.github.io/grid-kiss-playground/#basic-layout)

```shell
yarn add postcss-grid-kiss --dev
```

### `index.html`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Advanced CSS</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <header>
      Header
    </header>

    <aside class="sidebar">
      Sidebar
    </aside>

    <main>
      Main content
    </main>

    <footer>
      Footer
    </footer>
  </body>
</html>
```

### `styles.css`

```css
body {
  grid-kiss: "+------------------------------+      "
    "|           header ↑           | 120px"
    "+------------------------------+      "
    "                                      "
    "+--150px---+  +----- auto -----+      "
    "| .sidebar |  |      main      | auto "
    "+----------+  +----------------+      "
    "                                      "
    "+------------------------------+      "
    "|              ↓               |      "
    "|         → footer ←           | 60px "
    "+------------------------------+      ";
}

header {
  background: cyan;
}
.sidebar {
  background: lime;
}
main {
  background: yellow;
}
```
