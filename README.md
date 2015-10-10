#数字滚动组件

最近遇到一个数字模拟老虎机滚动的问题，以前有做过几次。但是都没有对它进行沉淀，这次觉得应该把这个东西沉淀一下，方便日后使用。本组件主要针对移动端面。如果是PC端可能在低版本浏览器下会出问题。

##使用方法

下载本项目的numbers.js。然后在需要的页面中引用本，在需要使用数字滚动的容器元素中添加一个叫`HALO-NUMBER-SCROLL`的属性值，并在容器内添加`<input type="hidden" value="" />`做为容器的第一个元素。如下：

```html
<div class="numbers" HALO-NUMBER-SCROLL>
	<input type="hidden" value="103450" />
</div>
```

简单的用法如下：

```html
<body ontouchstart>
<div class="numbers" HALO-NUMBER-SCROLL>
	<input type="hidden" value="103450" />
</div>
<div class="numbers" HALO-NUMBER-SCROLL>
    <input type="hidden" value="12345678" />
</div>
<script type="text/javascript" src="numberscroller.js"></script>
<script type="text/javascript">
	var NUMBERS=numbers();
	NUMBERS.scroll();
</script>
</body>
```
##定制滚动方式
可以针对具体情况，对数字滚动做定制。

定制可以分成两种形式：
- 统一定制
- 单独定制

###统一定制

一般在初始化滚动对象时，传入参数对象即可，如下：

```javascript
var NUMBERS=numbers(
	{
        round:3,//默认三圈
        duration: 1,//默认1s
        direction: 'alternate',//方向，有三个值，up,down,alternate。默认是alternate
        l2r:1,//滚动顺序，如果为1表示 从左到右 如果为0表示 从右到左
        delay: .3,//组之间的时间延迟，默认.3s
        groupNum:2,//默认2个一组
        diffrentiation:1,//差异化滚动，默认是差异化滚动
        undreg:'^xxx'//强制无差异化匹配 ^ooxx 表示开头第3，4为无差异化滚动 xxx$ 表示倒数的后三们为无差异滚动
    }
);
NUMBERS.scroll();//需要调用scroll方法后才可以触发数字滚动
```

也可以通过，滚动对象的set方法来后期定制，如下：

```javascript
var NUMBERS=numbers();
NUMBERS.set(
	{
        round:3,//默认三圈
        duration: 1,//默认1s
        direction: 'alternate',//方向，有三个值，up,down,alternate。默认是alternate
        l2r:1,//滚动顺序，如果为1表示 从左到右 如果为0表示 从右到左
        delay: .3,//组之间的时间延迟，默认.3s
        groupNum:2,//默认2个一组
        diffrentiation:1,//差异化滚动，默认是差异化滚动
        undreg:'^xxx'//强制无差异化匹配 ^ooxx 表示开头第3，4为无差异化滚动 xxx$ 表示倒数的后三们为无差异滚动
    }
);
NUMBERS.scroll();
```

###单独定制

有时候，一个页面内有多个数字滚动，并且每个滚动的具体定制不同，无法统一通过`NUMBERS.set(...)`来完成。numberscroller组件可以通过数字滚动容器的属性来完成单独定制。

如下：

```html
<div class="dataCounter" HALO-NUMBER-SCROLL diffrentiation="1" undreg="xxx$" l2r="1">
	<input type="hidden" value="12345678912" />
</div>
<div class="dataCounter" HALO-NUMBER-SCROLL diffrentiation="1" undreg="xxx$" l2r="0">
	<input type="hidden" value="12345678912" />
</div>
```

窗口的属性名与定制对象的成员名一致！！


具体使用方式，可以查看[DEMO.html](http://leeenx.github.io/numberscroller/DEMO.html)页面