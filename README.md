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



### flex children

#### align-self

> flex container에 높이 설정 필요.

: `align-items`와 비슷한 역할(`cross-axis`)

- `align-self: center` : `wrapper` 높이의 중간으로 위치(해당 item만)

- `align-items: flex-end` : 해당 item만 맨 아래로 위치



#### order

: html을 변경할 수 없을때 item의 순서 변경

> `order`의 default 값은 0이다.

- `order: 1`



### ※ 가운데 위치시키기

```css
.box{
    display: flex;
    justify-content: center;
    align-items: center;
}
```





### flex wrap

> wrap 설정 없이는 flex는 width를 무시하더라도 한줄에 유지한다.

```html
<div class="fater">
    <div class="child">1</div>
    <div class="child">2</div>
    <div class="child">3</div>
    <div class="child">4</div>
    <div class="child">5</div>
    <div class="child">6</div>
</div>
```

```css
.father {
    display: flex;
    justify-content: space-around;
    height: 100vh;
    flex-wrap: wrap; // default:nowrap
}
```

: `child`의 크기를 유지



#### align-content

: `line` - `cross axis`수정

- `align-content : flex-start` : `line`이 없어진다.
-  `align-content : around` : default 값.



### flex-shrink, flex-grow(child)

```css
.father {
	display: flex;
    flex-direction: row; // default
}
.child {
    width: 100px;
    height: 100px;
    background: red;
}
.child:nth-child(2){
    flex-shrink: 2; // defulat: 1
    // 2배로 flexbox의 넓이가 줄어든다.
}
.child:nth-child(3){
    flex-gorw: 1; // default:0
    //공간을 차지할수있는만큼 늘어난다.
}
```

```html
<div class="father">
    <div class="child">1</div>
    <div class="child">2</div>
    <div class="child">3</div>
</div>
```



###  flex-basis(child)

```css
.child {
    flex-basis: 300px;
}
```

: element에게 **처음 크기**를 지정한다.

- `flex-direction`이 row일때는  `width`
- `flex-direction`이 column일때는 `height`



## GRID

```html
<div class="father">
    <div class="child">1</div>
    <div class="child">2</div>
    <div class="child">3</div>
    <div class="child">4</div>
</div>
```

```css
.father {
    display: grid;
    grid-template-colums: 20px 55px 89px 100px; // column 크기
    column-gap: 10px; // column 사이의 공간
    row-gap: 10px; // row 사이의 공간
    // gap: 10px; → column, row 사이 공간
    grid-template-rows: 100px 50px 300px; // row 크기
}

```



### Grid Template Areas

```html
<div class="grid">
    <div class="header"></div>
    <div class="content"></div>
    <div class="nav"></div>
    <div class="footer"></div>
</div>
```

```css
.grid{
    display: grid;
    grid-template-columns: repeat(4, 200px); // → 200px 200px 200px 200px → auto 200px
    grid-template-rows: 100px repeat(2, 200px) 100px;
    grid-template-ares:
        "header header header header"
        "content content content nav"
        "content content content nav"
        "footer footer footer footer";
}
.header{
    background-color: yellow;
    grid-area:"header";
}
.content{
    background-color: blue;
     grid-area:"content";
}
.nav{
 	background-color: green;   
     grid-area:"nav";
}
.footer{
    background-color: red;
     grid-area:"footer";
}
```



### Rows and Columns

```css
.grid {
    display: grid;
    gap: 10px
    grid-template-columns: repeat(4, 100px);
    grid-template-rows: repeat(4, 100px);
}
.header{
    background-color: yellow;
    grid-column-start: 1; // line을 뜻한다.
    gird-column-end: 5;
}
.content{
    background-color: blue;
   	grid-column-start: 1;
    grid-column-end: 4;
    grid-row-start: 2;
    grid-row-start: 4;
}
.nav{
 	background-color: green;
        grid-row-start: 2;
    grid-row-start: 4;
}
.footer{
    background-color: red;
    grid-column-start: 1;
    grid-column-end: 5;
}
```

