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
   	grid-column-start: 1; → grid-column: 1/ 4
    grid-column-end: 4;
    grid-row-start: 2; → grid-row: 2/  4
    grid-row-start: 4;
    → grid-row: sapn 2 / span 2;
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
    → grid-column 1 / -1; // 처음부터 끝까지
    → grid-column: span 4;
}
```



### Grid Template

```html
<div class="grid">
    <div class="header"></div>
    <div class="content"></div>
    <div class="nav"></div>
    <div class="footer"></div>
</div>
```

```css
.grid {
    display: grid;
    gap: 10px;
    height: 50vh;
    grid-template-columns: repeat(4, 1fr);  // 1fraction→ 사용가능한 공간
    grid-template-rows: repeat(4, 1fr); // 사용하기 위해선 height를 지정해줘야 함.
    /////
    grid-template:
        "header header header header" 1fr → row 높이
        "content content content nav" 2fr
        "footer footer footer footer" 1fr / 1fr 1fr 1fr 1fr  → column 각각의 넓이 지정, repeat 불가능
        ;
}
.header{
    background-color: yellow;
	grid-area: header;
}
.content{
    background-color: blue;
	grid-area: content;
}
.nav{
 	background-color: green;
	grid-area: nav;
}
.footer{
    background-color: red;
	grid-area: footer;
}
```



### Place Items

```html
<div class="grid">
    <div class="header">header</div>
    <div class="content">content</div>
    <div class="nav">nav</div>
    <div class="footer">footer</div>
</div>
```

```css
.grid {
    display: grid;
    gap: 10px;
    height: 50vh;
    grid-template-columns: repeat(4, 1fr);  // 1fraction → 사용가능한 공간
    grid-template-rows: repeat(4, 1fr); // 사용하기 위해선 height를 지정해줘야 함.
    justify-items: strecth; // default
}
.header{
    background-color: yellow;
}
.content{
    background-color: blue;
}
.nav{
 	background-color: green;
}
.footer{
    background-color: red;
}
```

#### justify-items - 수평, align-items - 수직

- `justify-items: stretch;` : 넓이만큼 늘린 상태, default 세팅
- `justify-items: start;` : 시작점부터 item의 넓이만큼
- `justify-items: center;` : 가운데 위치

#### place-items: y  x  → align-items justify-items



### Place Content

: **align-content justify-content**



### Place Self

: 개별 아이템에 직접 적용 align-self justify-self



### Auto Columns and Rows

```html
<div class="grid">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
    <div class="item">7</div>
    <div class="item">8</div>
    <div class="item">9</div>
    <div class="item">10</div>
    <div class="item">11</div>
    <div class="item">12</div>
    <div class="item">13</div>
    <div class="item">14</div>
    <div class="item">15</div>
    <div class="item">16</div>
    <div class="item">17</div>
    <div class="item">18</div>
    <div class="item">19</div>
    <div class="item">20</div>
</div>
```

```css
.grid {
    display: grid;
    gap: 10px;
    grid-template-columns: repeat(4, 100px);
    grid-auto-rows: 100px;
}
item:nth-child(odd) {
	background-color: blue;        
}
item:nth-child(even) {
    background-color: green;
}
```

#### grid-auto-rows 

: 지정한 row보다 더 많은 content가 있을 때 따로 row를 지정해주지 않아도 자동으로 row를 생성 

#### grid-auto-flow: column

: 지정한 방향으로 설정해놓은것보다 많은 element를 가질때 (달력을 만들수도)



### minmax

: element를 얼마나 작고 얼마나 크게 될수있는지 지정해준다

```html
<div class="grid">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
</div>
```

```css
.grid {
    display: grid;
    gap: 10px;
    grid-template-columns: repeat(5, minmax(100px, 1fr));
    grid-template-rows: repeat(4, 100px);
    grid-auto-columns: 100px;
}
item:nth-child(odd) {
	background-color: blue;        
}
item:nth-child(even) {
    background-color: green;
}
```



### auto-fill auto-fit

```html
<body>
    auto-fill
    <div class="grid">
        <div class="item">1</div>
   		<div class="item">2</div>
    	<div class="item">3</div>
    	<div class="item">4</div>
    	<div class="item">5</div>
    </div>
    auto-fit
    <div class="grid">
        <div class="item">1</div>
   		<div class="item">2</div>
    	<div class="item">3</div>
    	<div class="item">4</div>
    	<div class="item">5</div>
    </div>
</body>
```

```css
.grid:first-child{
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
}
.grid:last-child{
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}
```

#### auto-fill

: 가능한 많이 column을 만들어준다 주어진 size에서(row를 채워준다)

#### auto-fit

: 현재의 element를 늘려서 row에 맞게 해준다.



### min-content, max-content

```html
<div class="grid">
    <div class="item">This is a very long text</div>
    <div class="item">This is a very long text</div>
</div>
```

```css
.grid {
    color: white;
    display: grid;
    gap: 5px;
    grid-template-columns: max-content min-content;
    grid-template-columns: repeat(5, minmax(max-content, 1fr));
    grid-auto-rows: 100px;
    margin-bottom: 30px;
}
item:nth-child(odd) {
	background-color: blue;        
}
item:nth-child(even) {
    background-color: green;
}
```

#### min-content

: content가 작아질 수 있는 만큼 작게 만든다

### max-content

: content가 커질수 있는 만큼 커지게 만든다.





## SCSS

: css preprocessor, 



### Variables

```scss
$bg: #e7473c;


/// styles.scss
@import "_variables.scss";

body {
    background: $bg;4
}
```



### Nesting

```html
<body>
    <h2>Title</h2>
    <div class="box">
    	<h2>Another Title</h2>
        <button>Hello</button>
    </div>
    <button>Bye Bye</button>
</body>
```

```scss
h2{
    color: $bg
}

.box {
    margin-top: 20px;
    h2 {
        color: blue;
    }
    button {
        color: red;
    }
    &:hover {
        background-color: green;
    }
}
```



### Mixins

> 상황에 따라 다르게 코딩을 하고 싶을때 사용

```scss
// _mixins.scss
@mixin Title($color) {
	color: $color;
    font-size: 30px;
    margin-bottom: 12px;
    // if/else 문도 사용 가능.
    @if $word == 'odd' {
        
    } @else {
        
    }
}

// styles.scss
@import "_mixins";

h1{
    &:nth-child(odd) {
   	 @include Title(blue);
	}
    &::nth-child(even) {
    	@include Title(red);
    }
}
```



### Extends

>  같은 코드를 중복하고 싶지 않을때 사용

```html
<a href='#'>Log In</a>
<button>
    Log Out
</button>
```

```scss
// _button.scss
%button {
    border-radius: 7px;
    font-size: 12px;
    text-transform: uppercase;
    padding: 5px 10px;
    background-color: peru;
    color: white;
    font-weight: 500;
}

// styles.scss
@import "_button";

a {
    @extend %button;
    text-decoration: none;
}
button{
    @extend %button;
    border: none;
}
```



### Responsive Mixins

```scss
// _mixins.scss
$minIphone: 500px;
$maxIphone: 690x;
$minTablet: $maxIphone + 1;
$maxTablet: 1120px;

@mixin responsive($device) {
    @if $device == 'iphone' {
        @media screen and (min-width: $minIphone) and  (max-width: $maxIphone) {
            @content;
        }
    } @else if $device == 'tablet' {
        @media screen and (min-width: $minTablet) and (max-width: $maxTablet){
            @content;
        }
    } @else if $device == 'iphone-l' {
        @media screen and (min-width: $minIphone) and (max-width: $maxIphone) and (orientation: landscape){
            @content;
        }
    } @else if $device == 'ipad-l' {
        @media screen and (min-width: $minTablet) and (max-width: $maxTablet) and (orientation: landscape){
            @content;
        }
    } 
    color: blue;
    @contnet;
}

// styles.scss
@import "_mixins";

h1 {
    color: red;
    @include responsive('iphone') {
        color: yellow;
    }
    @include responsive('iphone-l'){
        font-size: 60px;
    }
    @include responsive('tablet'){
        color: green;
    }
    
}
```



