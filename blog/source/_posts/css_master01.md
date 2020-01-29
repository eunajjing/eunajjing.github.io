# CSS 마스터 클래스

> 해당 게시글은 노마드코더의 [CSS 마스터 클래스](https://academy.nomadcoders.co/courses/enrolled/360503) 강의를 듣고 요약한 것입니다. 저작권 문제가 발생할 시 삭제될 수 있습니다.

## `Flexbox`

> 다시 듣기

### `flex-container`

`display` 속성이 `flex`이며, 자식 요소인 `flex-item`의 제어권을 지닌다. **자손 요소까지 영향을 끼치지 못한다**

```css
body {
	display : flex;
}
```

#### `justify-content` : 수평

사용하려면 충분한 `width`를 가지고 있어야 한다

- `space-between`
  - `flex-items`을 같은 간격으로 떨어트린다
  - 기본적으로 반응형 디자인을 지닌다

- `flex-start`
  - 디폴트 값. 좌측부터 `flex-items`이 시작
- `flex-end`
  - 우측부터 `flex-items`이 붙는다
- `space-around`
  - `flex-items` 주변에 간격을 만든다
  - `marginLeft`와 `marginRight`가 있는 것과 비슷

#### `align-items` : 수직

사용하려면 충분한 `height`를 가지고 있어야 한다

- `center`
- `flex-start`
- `flex-end`

#### `flex-direction`

기본적으로 `row` 값을 지니고 있으며, 만약 `column`으로 값을 변경하게 되면 기준 축이 바뀌며 수직 축과 수평 축이 서로 변경

### `flex-wrap`

안에 있는 `flex-items`가 서로 겹칠 때 사용한다. 기본적으로 `flex-items`는 공간이 부족하면 `item`을 찌그러트리는 성질을 지니고 있다. 

#### `no-wrap`

`flex-wrap`의 기본 값으로 공간이 부족하면 아이템을 찌그러트린다

#### `wrap`

아이템이 일그러지는 것을 막는다

### `flex-direction`

#### `row reverse`

`flex-items`의 순서를 바꾼다. 이 때 `start`의 값은 우측이 되며, `end`의 값은 좌측이 된다.

#### `column-reverse`

`flex-items`의 순서를 바꾼다. 이 때 `top`의 값은 하단이 되며, `bottom`의 값은 상단이 된다.

### `align-self`

`display`에 `flex`를 지닌 엘리먼트에 주는 속성이 아니라, 직접 `items`에 옵션을 주는 특이한 속성

## CSS Grid

### `display : grid`

- `grid-template-columns`

- `grid-template-rows`

  ```css
  .someDiv {
    display : grid;
    grid-template-columns : 30px 50px;
    grid-template-rows : 30px 12px;
    /** 30px 정사각형 하나와 가로 50px, 세로 12px의 직사각형이 만들어진다 **/
  }
  ```
  
- `grid-gap` : `.box`의 사이를 띄운다

- `gride-template-areas`

  ```css
  .beforeDiv {
    display: grid;
    grid-auto-rows : 200px;
    /* 한 줄에 세로 길이가 어느 정도를 차지할 것인지
    	원한다면 각각의 class에 크기를 넣어도 무방*/
    grid-template-areas:
      "header header header"
      "content content sidebar"
      "content content sidebar"
      "footer footer footer";
  }
  
  .aaa {
    grid-area : header
    /* 위의 grid-template-areas에서 지정한 이름을 써줘야 함 */
  }
  ```

#### `grid-area`

인자로 `grid-template-areas`의 이름을 받거나, `row start line`, `column start line`, `row end line`, `column end line`를 정해줄 수 있다. `line`은 좌측 상단부터, `1`부터 시작한다.

```css
.someDiv {
  grid-area : span 4 / span 4
}
```

위와 같은 경우, 좌측을 `row`로, 우측을 `column`으로 인식한다.

#### `fr`

최대한 공간을 차지하라는 의미의 **단위**

```css
.someDiv {
  display : grid;
	grid-template-columns : 2fr 1fr 2fr 1fr
  /* 한 줄로 정렬된 div 박스 4개가 나오며,
    첫 div는 두 번째 div보다 두 배가 큰 모양새
    총 6개로 나뉜 그리드 내에 위치한 div들을 생각*/
}
```

#### `repeat`

`column`을 반복하는 `CSS` 함수

```css
.someDiv {
  display : grid;
  grid-template-columns : repeat(5, 1fr) 4fr;
  /* 5번 반복의 1fr를 만들고 이후 4fr의 것을 붙이겠다 */
}
```

#### `minmax`

`object`가 가져야 하는 최소, 최대 크기를 지정할 수 있는 함수. 즉 **반응형 시에도 줄어들지 않는다**

```css
.someDiv {
  display : grid;
	grid-template-columns : minmax(400px, 2fr) ...
  /* 최소 크기는 400px이며, 최대 2fr까지 늘어난다 */
}
```

#### `max-content`

가질 수 있는 최대한의 크기를 가지게 하는 속성

```css
.someDiv {
  display : grid;
	grid-template-columns : max-content
}
```

#### `min-content`

가질 수 있는 가장 최소한의 크기를 가지게 하는 속성

```css
.someDiv {
  display : grid;
	grid-template-columns : min-content	
}
```

#### `auto-fit`

```css
.someDiv {
  display : grid;
  grid-template-columns : repeat(auto-fit, 50px)
}
```

가질 수 있는 가장 많은 `column`을 가지되, 각 `column`의 크기는 `50px`로 한다.

> 프론트 단에서 얼마나 많은 수의 `div`가 만들어져야 하는지 모르는 경우 유용하게 사용할 수 있으며,
>
> > DB에서 불러오는 경우 등
>
> 보통 `minmax`와 함께 쓰며 유연성을 보완한다
>
> ```css
> .someDiv {
>   display : grid;
>   grid-template-columns : repeat(auto-fit, minmax(350px, 1fx))
> }
> ```

#### `auto-fill`

기존에 있는 `layout`을 `cell`로 채워나가며, `cell`이 없는 경우 `ghost grid`로 채워짐

```css
.someDiv {
  display : grid;
  grid-template-columns : repeat(auto-fill, minmax(350px, 1fx))
}
```

#### `grid-auto-flow`

```css
.someDiv {
  display : grid;
	grid-auto-flow : row dense;
  /* 한 줄에 비어있는 것이 없도록 가득 채운다,
  즉 ghost item이 존재하지 않는다
  또 다른 값으로는 row 대신 column을 넣을 수도 있다 */
}
```

## `content`와 `item`의 차이

### `content`

만들어놓은 그리드 자체를 옮긴다.

#### `justify-content`

```css
.someDiv {
  display : grid;
  justify-content : center;
  /* 여러 개의 자식 요소들이 상단 중앙으로 정렬된다
  값으로는 start, end가 있으며 이는 flex와 유사하게 보인다 */
}
```

#### `align-content`

```css
.someDiv {
  display : grid;
  align-content : center;
  /* 여러 개의 자식 요소들이 세로 축을 기준으로 중앙으로 정렬된다
  값으로는 start, end가 있으며 이는 flex와 유사하게 보인다 */
  height : 100vh;
  /* height 값이 필요 */
}
```

#### `place-content`

인자로 두 개를 받으며, 첫 인자는 `align-content`, 두 번째 인자로 `justify-content`를 받는다.

```css
.someDiv {
  place-content : center center
}
```

### `item`

`items`을 움직이게 한다. 만약 `justify`나 `align`을 하지 않았을 때 `default` 값은 `item` 확장 상태

#### `justify-items`

```css
.someDiv {
	display : grid;
  grid-auto-rows : 100px;
  grid-template-colums : repeat(5, 100px);
  /* 100px 정사각형 box를 만들고 */
  justify-items : center;
  /* box 안, column 안에서 가로 축을 기준으로 center 정렬
  값으로는 start, end도 있다*/
}
```

#### `align-item`

```css
.someDiv {
	display : grid;
  grid-auto-rows : 100px;
  grid-template-colums : repeat(5, 100px);
  /* 100px 정사각형 box를 만들고 */
  align-item : center;
  /* box 안, column 안에서 세로 축을 기준으로 center 정렬
  값으로는 start, end도 있다*/
}
```

#### `place-item`

인자로 두 개를 받으며, 첫 인자는 `align-item`, 두 번째 인자로 `justify-item`를 받는다.

```css
.someDiv {
	display : grid;
  grid-auto-rows : 100px;
  grid-template-colums : repeat(5, 100px);
  place-item : center center;
}
```

#### `justify-self`, `align-self`, `place-self`

해당 요소에만 정렬 적용



## `flexbox`와 `css grid` 합치기

```css
.father {
  display: grid;
  grid-gap: 10px;
  grid-auto-rows: 100px;
	grid-template-columns: repeat(5, 1fr);
}

.box {
  display: flex;
  place-item : center center;
}

/* 부모 요소의 자식들은 그리드를 따르며, 안에 있는 자식 요소는 flex 속성을 지닌다.
	정렬은 중앙 정렬로 한다 */
```

### `grid-column`, `grid-row`

부모 요소 `Div`에 작성하지 않고, 자식 요소  `Div`에 작성

```css
.box:first-child {
  grid-column-start: 1;
  grid-column-end: 5;
  /* 1번째 line부터 시작해서 5번째 line까지
  칼럼으로 친다면 첫 칼럼부터 4 칼럼(5-1)까지 */
}

/* 이렇게도 쓸 수 있다 */
.box:first-child {
  grid-column : 1 / 5;
  /* 매한가지로 grid-row도 적용이 가능하다 */
}
```

> **-1**
>
> 자동적으로 제일 마지막 `line`을 택할 때 쓴다. 마지막 `line`이 몇 번째인지 모를 때 사용
>
> #### `span`
>
> `x`번 째부터 `y`번 째를 정해줄 필요 없이 단순히 그 칼럼이 가져야 하는 수를 지정할 때 사용

### `line Naming`

```css
.someDiv {
	grid-template-columns:
    [first-line] 1fr
    [second-line] 1fr
    [third-line] 1fr
    [fourth-line] 1fr
    [fifth-line] 1fr
    [sixth-line];
  /* 이름은 반드시 `-`로 이어져 있어야 하고, 배열 형태여야 한다. */
}

.box:first-child {
  grid-column-start : second-line;
  grid-column-end : fourth-line;
}
```

#### 어떨 때 쓰나

```css
.someDiv {
  display : grid;
  grid-auto-rows : 100px;
  grid-template-columns : [first-line] repeat(5, 1fr) [last-line]
}

.box:first-child {
  grid-column-start : first-line;
  grid-column-end : last-line;
}
```

