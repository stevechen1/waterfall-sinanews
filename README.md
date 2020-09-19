##懒加载与瀑布流
链接：https://stevenchen7500.github.io/waterfall-sinanews/

## 懒加载原理
懒加载是用来减轻浏览器的压力，原理就是通过ajax先加载一部分资源，剩余的资源可以通过页面上的事件来触发，
这个事件就是判断一个元素是否在窗口内，如果解决了这个问题，懒加载的问题就可以迎刃而解，我们通过一张图来解释页面元素在窗口中的距离关系
https://github.com/stevenchen7500/waterfall-sinanews/blob/master/1.png
这样通过判定当$(node).offset().top < $s(window).scrollTop() + $(window).height()的时候元素就出现在了窗口中，这个时候加载图片。
## 瀑布流原理
瀑布流的关键点是，图片的宽度是固定的，所以可以通过将每一张图片在窗口中并列排放，这个时候就要用到绝对定位，通过在每张图片加载过后第一列元素列，找到其中最低的一项，将第二排的第一个元素放在这项的下面，绝对定位的值是{left: idx * width , top: $el.height}，就可与达到瀑布流的排列效果。

## 实现原理
