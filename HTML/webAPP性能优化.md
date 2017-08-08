# 性能优化
## 1.加载优化
* 合并CSS、Javascript
* 合并小图片，使用CSS Sprite，减少了http请求次数
* 缓存一切可缓存的资源
* 使用长Cache
* 使用外联式引用CSS、Javascript
* 压缩HTML、CSS、Javascript
* 启用GZip
* 使用首屏加载，按需加载和滚屏加载
* 通过Media Query加载
* 增加Loading进度条
* 减少Cookie
* 避免重定向，异步加载第三方资源
## 2.CSS优化
* CSS写在头部，Javascript写在尾部或者异步
* 避免图片和iFrame等存在空的src
* 尽量避免重设图片大小，图片尽量避免使用DataURL
* 尽量避免在HTML标签中写Style属性
* 避免CSS表达式
* 标准化各种浏览器前缀
* 不声明过多的font-size
* 值为0时不需要任何单位
## 3.图片优化
* 使用（CSS3、SVG、IconFont）代替图片
* PNG8优于GIF，webP优于JPG
## 4.Javasript优化
* 减少重绘和回流
* 缓存Dom选择与计算
* 尽量使用事件代理，避免批量绑定事件
* 尽量使用ID选择器
* 使用touchstart、touchend代替click
## 5.Render优化
* HTML使用Viewport
* 减少Dom节点
* 尽量使用CSS3动画
* Touchmove、Scroll事件会导致多次渲染
* 使用CSS3 transitions、CSS3 3D transforms、Opacity、Canvas、WebGL来触发GPU渲染
