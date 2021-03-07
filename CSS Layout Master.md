# CSS Layout Master

> course in nomadcoder



##  #1 Flexbox

### flex container

박스들을 가로로 놓고 싶을때:

```css
.wrapper {
	display: flex;
    flex-direction: row; // default
}
.box {
    width: 100px;
    height: 100px;
    background: red;
}
```

```html
<div class="wrapper">
    <div class="box">1</div>
    <div class="box">2</div>
    <div class="box">3</div>
</div>
```



#### main axis

default : **row**(가로)

#### cross axis

default: **column**(세로)



#### justify-content

: `main axis`에 있는 flex children의 위치를 변경한다.

```css
.wrapper {
	display: flex;
    justify-content: center;
}
```

- `justify-content: center` : 요소들을 중간으로 위치
- `justify-content: space-between` : box 사이에 공간을 만든다.
- `justify-content: space-around` : box 사이 공간을 같게 만든다.



#### align-items

: `cross axis` 방향으로 item을 옮길때 사용한다.

```css
.wrapper {
	display: flex;
    justify-content: center;
    align-items: center;
    height:100vh;
}
```

- `align-items: center` : `wrapper` 높이의 중간으로 위치
- `align-items: stretch` : `wrapper` 높이까지 늘어난다.
- `align-items: flex-end` : item들을 맨 아래로 위치
- `align-items: flex-start` : item들을 맨 위로 위치