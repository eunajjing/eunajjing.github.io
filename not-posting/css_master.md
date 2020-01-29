# CSS 마스터 클래스

> 해당 게시글은 노마드코더의 [CSS 마스터 클래스](https://academy.nomadcoders.co/courses/enrolled/360503) 강의를 듣고 요약한 것입니다. 저작권 문제가 발생할 시 삭제될 수 있습니다.

## `Flexbox`

### `flex-container`

`display` 속성이 `flex`이며, 자식 요소인 `flex-item`의 제어권을 지닌다. **자손 요소까지 영향을 끼치지 못한다**

```html
<style>
  body {
    display : flex;
  }
</style>
```

#### `justify-content` : 수평

사용하려면 충분한 `width`를 가지고 있어야 한다

- `space-between`
  - `flex-items`을 같은 간격으로 떨어트려 놓는다
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

기본적으로 `row` 값을 지니고 있으며, 만약 `colum`으로 값을 변경하게 되면 기준 축이 바뀌며 수직 축과 수평 축이 서로 변경

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

  ```html
  <style>
    .fater {
      display : grid;
      grid-template-columns : 30px 50px;
      grid-template-rows : 30px 12px;
      /** 30px 정사각형 하나와 가로 50px, 세로 12px의 직사각형이 만들어진다 **/
    }
    
    .box {
      background-color : yellow;
    }
  </style>
  ```

- `grid-gap` : `.box`의 사이를 띄운다

