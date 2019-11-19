### 移动端的布局单位
rem,百分比,vw,vh
### Position 的几个属性

position: sticky 粘性定位
粘性定位，该定位基于用户滚动的位置。
它的行为就像 position:relative; 而当页面滚动超出目标区域时，它的表现就像 position:fixed;，它会固定在目标位置。

### flex 布局，两边固定，中间自适应，中间里面的内容是一个表格，内容超出了怎么办？
### flex布局的一些属性
#### 设在容器上的
- flex-direction
- flex-wrap
- flex-flow(direction和wrap的简写方式)
- justify-content
- align-itmes
- align-content(多根轴线)
#### 项目的属性
- order
- flex-grow
- flex-shink
- flex-basis
- flex
- align-self
### less 和 scss 差别
### 使用less写一个函数
```less
/**设计图稿换算rem*/
.rem(@name,@px) {
  @{name}: unit(@px / 100, rem);
}
.root[time="1565257240441"]{
  .listview{
    padding-left: 0.24rem;
    .title{
        font-size: 0.3rem;
    }
  >div{
      height: 1.08rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
      .rem(border-bottom, 2);
      border-style: solid;
      border-color: #eee;
  }
}
```
```less
.lineCamp(@n) {
  overflow : hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: @n;
  -webkit-box-orient: vertical;
}
```
### transition 和 animation 的区别

### C3 实现绕着一个点旋转

animation:circleRoate 5s infinite linear ;
@keyframes circleRoate{
from{transform： rotate(0deg)}
to{transform: rotate(360deg)}
}

### display: none和visiblity的区别（重排和重绘）【from：心有灵犀】
### 字体小于10px,1px边框
用transform:scale()实现
### rem布局原理
js查询屏幕宽度动态设置html的fontsize