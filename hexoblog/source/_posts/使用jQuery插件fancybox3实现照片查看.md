---
layout: photo
title: 使用jQuery插件fancybox3实现照片查看
comments: true
photos:
  - http://imglf2.nosdn.127.net/img/T29DNkRBMFB6cXFmc1J3cjNCYVQzNUJzMk9KMjVFVUZRcGdGRmV0bERReHBSY0pzaCtIZW1BPT0.jpg?imageView&thumbnail=1680x0&quality=96&stripmeta=0&type=jpg%7Cwatermark&type=2&text=wqkg6Jyc57OW5bCP5aeQa2l0aWMgLyBraXRpYy5sb2Z0ZXIuY29t&font=bXN5aA==&gravity=southwest&dissolve=30&fontsize=340&dx=16&dy=20&stripmeta=0
  - http://imglf1.nosdn.127.net/img/TlB1TFBnUkQ0WEM4dUlXUUZzS0kxSjdTRWpDZndpRXBRV1lPcFFDT3o1RVBMVEFWTXVTVTR3PT0.jpg?imageView&thumbnail=1680x0&quality=96&stripmeta=0&type=jpg
  - http://imglf0.nosdn.127.net/img/M01RMXowVys0Y2NFNE96MkMxalJDZStZSVlMVVVXaWxPdnM2eUJTN1dwdkx3UmljS29FdUd3PT0.jpg?imageView&thumbnail=1680x0&quality=96&stripmeta=0&type=jpg
date: 2017-04-20 14:32:51
updated:
tags:  
  - fancyBox
  - jQuery
  - 插件
  - 图片
categories: 前端技术
---
我们总会有在网页中插播图片的想法，jQuery Fancybox就是一个十分不错的插件，内容丰富，使用方便（看你怎么理解方便了）

<!-- more -->

---

<a href="http://imglf0.nosdn.127.net/img/M01RMXowVys0Y2NFNE96MkMxalJDZStZSVlMVVVXaWxPdnM2eUJTN1dwdkx3UmljS29FdUd3PT0.jpg?imageView&thumbnail=1680x0&quality=96&stripmeta=0&type=jpg" data-fancybox="same" data-caption="cat" data-height="1365">
	<img src="http://imglf0.nosdn.127.net/img/M01RMXowVys0Y2NFNE96MkMxalJDZStZSVlMVVVXaWxPdnM2eUJTN1dwdkx3UmljS29FdUd3PT0.jpg?imageView&thumbnail=150x0&quality=96&stripmeta=0&type=jpg" alt="猫" height="150" />
</a>
<a href="http://imglf.nosdn.127.net/img/SHRxWGk2NHYvc3Z0UkZ4ZHJka2d1emVBcmJKY2JXZFNxakJmSThkVm00cDR2azhiTXZYWVBnPT0.jpg?imageView&thumbnail=1680x0&quality=96&stripmeta=0&type=jpg" data-fancybox="same" data-caption="scenery" data-height="1365">
	<img src="http://imglf.nosdn.127.net/img/SHRxWGk2NHYvc3Z0UkZ4ZHJka2d1emVBcmJKY2JXZFNxakJmSThkVm00cDR2azhiTXZYWVBnPT0.jpg?imageView&thumbnail=150x0&quality=96&stripmeta=0&type=jpg" alt="风景" height="150" />
</a>
<a href="http://imglf2.nosdn.127.net/img/SHRxWGk2NHYvc3RCZ01FV01GcDBtK3Rrc2hGNzBicGxCeWF0N04rWVhiejA1THd3M04wN0RRPT0.jpg?imageView&thumbnail=1680x0&quality=96&stripmeta=0&type=jpg" data-fancybox="same" data-caption="white swan" data-height="1365">
	<img src="http://imglf2.nosdn.127.net/img/SHRxWGk2NHYvc3RCZ01FV01GcDBtK3Rrc2hGNzBicGxCeWF0N04rWVhiejA1THd3M04wN0RRPT0.jpg?imageView&thumbnail=150x0&quality=96&stripmeta=0&type=jpg" alt="白天鹅" height="150" />
</a>
<a href="http://imglf1.nosdn.127.net/img/SHRxWGk2NHYvc3Z2OXI0TGNHYW5XN0tTZ0hwSVd5K3BDcnNUcG96aW9YK1J4SC80OEN3TWlnPT0.jpg?imageView&thumbnail=1680x0&quality=96&stripmeta=0&type=jpg" data-fancybox="same" data-caption="three white swans" data-height="1365">
    <img src="http://imglf1.nosdn.127.net/img/SHRxWGk2NHYvc3Z2OXI0TGNHYW5XN0tTZ0hwSVd5K3BDcnNUcG96aW9YK1J4SC80OEN3TWlnPT0.jpg?imageView&thumbnail=150x0&quality=96&stripmeta=0&type=jpg" alt="白天鹅" height="150" />
</a>

[fancybox](http://fancybox.net/)的主页是：http://fancybox.net/

[fancyBox3](http://fancyapps.com/fancybox/3/)的主页是：http://fancyapps.com/fancybox/3/

fancyBox3加入了手机端的适应性

**我使用的是fancyBox3，以下均为fancyBox3的安装使用方法，这是我对着官网文档的学习记录，许多翻译自官网文档，所以如果你有什么不明白的请参考官网文档。如果你是想学更高阶的用法，那这篇文章不是很适合你。**

# 安装方法

1. 进入fancyBox3的主页，下载fancyBox3的压缩包。
2. 解压缩到当前项目，具体位置无所谓，但是要能够访问到。
3. 安装完成，就是这么的简单。

# 初始化导入

1. 连接fancyBox3的.css文件和.js文件到页面，当然，在链接.js页面之前需要先链接jQuery库函数
```html
<link rel="stylesheet" type="text/css" href="jquery.fancybox.min.css">
<script src="//code.jquery.com/jquery-3.2.1.min.js"></script>
<script src="jquery.fancybox.min.js"></script>
```
2. 之后编写导入图片文件就可以了。
3. 任何元素都可以绑定fancyBox3的事件，只需要使用jQuery选择器选择元素并且调用`fancyBox3`方法就行了。
```html
<script type="text/javascript">
	$("[data-fancybox]").fancybox({
		// Options will go here
	});
</script>
```

# 使用方法

1. 基本使用-基本：
```html
<a href="image.jpg" data-fancybox data-caption="My caption">
	<img src="thumbnail.jpg" alt="" />
</a>
```
其中，`image.jpg`是点击后显示的大图，`thumbnail.jpg`是点击前显示的缩略图，`data-caption`是图片的主题名称，点开大图后会在大图页面显示
2. 基本使用-同一组图片：
```html
<a href="image_1.jpg" data-fancybox="group" data-caption="Caption #1">
	<img src="thumbnail_1.jpg" alt="" />
</a>
<a href="image_2.jpg" data-fancybox="group" data-caption="Caption #2">
	<img src="thumbnail_2.jpg" alt="" />
</a>
```
如果你有同一组图片（想要将几张图片作为一组显示），你可以指定他们相同的`data-fancybox`的值，这样就能够为他们创建一个画廊（官网说法，听着好高端的样子）。每一组图片的`data-fancybox`的值必须是唯一的。上面就是一个典型的例子。

**注意**：fancyBox3会自动识别传入数据的类型，如果传入数据无法别识别，也可以通过`data-type`属性手动指定类型。下面是一个例子。
```html
<a href="images.php?id=123" data-type="image" data-caption="Caption">
	Show image
</a>
```
3. fancyBox3可以在Javascript的任何一点被激活，因此并不需要一个触发元素。一个显示简单信息的例子如下所示：
```html
$.fancybox.open('<div class="message"><h2>Hello!</h2><p>You are awesome!</p></div>');
```
查看[API(此连接连接到官网)](http://fancyapps.com/fancybox/3/docs/#api)获得更多信息。

# 媒体类型
### 图片
1. 最基本的使用方法就是使用缩略图链接到一个大图。
```html
<a href="image.jpg" data-fancybox="images" data-caption="My caption">
	<img src="thumbnail.jpg" alt="" />
</a>
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/jyEGGG/?editors=1000)
2. 默认情况下，fancyBox3在显示前需要完全预加载图像。你也可以选择立即显示图像，只要收到数据就可以直接渲染显示图像，当然，这样做需要设定一些属性。
	- data-width - 图片真实的宽度
	- data-height - 图片真实的高度
```html
<a href="image.jpg" data-fancybox="images" data-width="2048" data-height="1365">
    <img src="thumbnail.jpg" />
</a>
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/wgBrXd?editors=1000)
3. fancyBox支持“scrset”，可以根据视窗宽度显示不同的图像。使用它可以改善移动用户的下载时间，并节省时间节省带宽。
```html
<a href="medium.jpg" data-fancybox="images" data-srcset="large.jpg 1600w, medium.jpg 1200w, small.jpg 640w">
	<img src="thumbnail.jpg" />
</a>
```
[点击这里，查看案例](https://codepen.io/fancyapps/pen/bqbpbO?editors=1000)
4. 可以禁用右键功能来保护图像不被下载。然而这并不能阻止所有用户，你的大多数文件不应该使用这个功能（虽然不明白为什么，但是既然有这句话，说明还是有一定道理的。）
```html
$('[data-fancybox]').fancybox({
	image : {
		protect: true
	}
});
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/RKKqLx?editors=1010)
### 内联样式
对于一个内联的HTML，你必须将DIV容器放入页面的内容中，比如：
```
<div style="display: none;" id="hidden-content">
	<h2>Hello</h2>
	<p>You are awesome.</p>
</div>
```
然后简单的使用`data-src`属性创建一个链接，该属性与要打开元素的CSS id选择器匹配（本例中为`#hidden-content`）：
```html
<a data-fancybox data-src="#hidden-content" href="javascript:;">
	Hidden div
</a>
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/RKKqLx?editors=1010)
### Ajax
要通过AJAX加载内容，需要在你的链接中添加一个`data-type=“ajax”`属性：
```html
<a data-fancybox data-type="ajax" data-src="my_page.com/path/to/ajax/" href="javascript:;">
	AJAX content
</a>
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/JEoOvK?editors=1100)

另外，可以使用`data-selector`属性定义一个选择器，用来显示一部分响应。选择器可以是任何的字符串，只要是一个有效的jQuery选择器就可以
```html
<a data-fancybox data-type="ajax" data-src="my_page.com/path/to/ajax/" data-selector="#two" href="javascript:;">
	AJAX content
</a>
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/MJwWKz?editors=1100)
### Iframe
如果内容可以在页面上显示，并且iframe并不会被页面的脚本或安全配置阻止，可以在fancyBox3中显示：
```html
<a data-fancybox data-src="http://codepen.io/fancyapps/full/jyEGGG/" href="javascript:;">
	Webpage
</a>
<a data-fancybox data-src="http://www.adobe.com/content/dam/Adobe/en/devnet/acrobat/pdfs/pdf_open_parameters.pdf" href="javascript:;">
	Sample PDF
</a>
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/BpymvO?editors=1000)
在iframe内的父窗口中访问和控制fancyBox。
```html
// Adjust iframe height according to the contents
parent.jQuery.fancybox.getInstance().update();
// Close current fancyBox instance
parent.jQuery.fancybox.getInstance().close();
```
iframe尺寸可以通过CSS控制。
```html
.fancybox-slide--iframe .fancybox-content {
	width  : 800px;
	height : 600px;
	max-width  : 80%;
	max-height : 80%;
	margin: 0;
}
```
必要情况下，这些CSS规则可以被JS覆盖：
```html
$("[data-fancybox]").fancybox({
	iframe : {
		css : {
			width : '600px'
		}
	}
});
```
如果你尚未禁用iframe预加载（使用“预加载”选项），则脚本将尝试计算内容维度，并会根据内容调整iframe的宽度/高度。请记住，由于相同的源策略，这会有一些限制。
# 嵌入
支持只提供网址URL就可以使用fancyBox3显示网站：
```html
<a data-fancybox href="https://www.youtube.com/watch?v=_sI_Ps7JSEk">
  YouTube video
</a>
<a data-fancybox href="https://vimeo.com/191947042">
  Vimeo video
</a>
<a data-fancybox href="https://www.google.com/maps/place/Googleplex/@37.4220041,-122.0833494,17z/data=!4m5!3m4!1s0x0:0x6c296c66619367e0!8m2!3d37.4219998!4d-122.0840572">
	Google Map
</a>
<a data-fancybox href="https://www.instagram.com/p/BNXYW8-goPI/?taken-by=jamesrelfdyer" data-caption="<span title=&quot;Edited&quot;>balloon rides at dawn ✨������<br>was such a magical experience floating over napa valley as the golden light hit the hills.<br><a href=&quot;https://www.instagram.com/jamesrelfdyer/&quot;>@jamesrelfdyer</a></span>">
	Instagram photo
</a>
```
[点击这里，查看案例（由于伟大的墙，不一定能显示，只能领会精神）](http://codepen.io/fancyapps/pen/LxEOwL?editors=1000)
### 视频尺寸
使用以下CSS设置调整视频显示大小：
```html
.fancybox-slide--video .fancybox-content {
	width  : 800px;
	height : 600px;
	max-width  : 80%;
	max-height : 80%;
}
```
[点击这里，查看案例（由于伟大的墙，不一定能显示，只能领会精神）](http://codepen.io/fancyapps/pen/PWZrzw?editors=1100)
显然，您可以选择您喜欢的任何尺寸，任何最小/最大值的组合。

视频的长宽比没有锁定，但是如果您希望有，您可以使用此代码段。
### 视频参数
通过URL参数控制视频：
```html
<a data-fancybox href="https://www.youtube.com/watch?v=_sI_Ps7JSEk&amp;autoplay=1&amp;rel=0&amp;controls=0&amp;showinfo=0">
  YouTube video - hide controls and info
</a>
<a data-fancybox href="https://vimeo.com/191947042?color=f00">
  Vimeo video - custom color
</a>
```
[点击这里，查看案例（由于伟大的墙，不一定能显示，只能领会精神）](http://codepen.io/fancyapps/pen/mRVNyO?editors=1000)
通过JavaScript控制视频：
```html
$('[data-fancybox]').fancybox({
	youtube : {
		controls : 0,
		showinfo : 0
	},
	vimeo : {
		color : 'f00'
	}
});
```
[点击这里，查看案例（由于伟大的墙，不一定能显示，只能领会精神）](http://codepen.io/fancyapps/pen/Qdyeyr?editors=1010)
# 选项
下面是可用的选项。

```html
defaults = {

	// Animation duration in ms
	speed : 330,

	// Enable infinite gallery navigation
	loop : true,

	// Should zoom animation change opacity, too
	// If opacity is 'auto', then fade-out if image and thumbnail have different aspect ratios
	opacity : 'auto',

	// Space around image, ignored if zoomed-in or viewport smaller than 800px
	margin : [44, 0],

	// Horizontal space between slides
	gutter : 30,

	// Should display toolbars
	infobar : true,
	buttons : true,

	// What buttons should appear in the toolbar
	slideShow  : true,
	fullScreen : true,
	thumbs     : true,
	closeBtn   : true,

	// Should apply small close button at top right corner of the content
	// If 'auto' - will be set for content having type 'html', 'inline' or 'ajax'
	smallBtn : 'auto',

	image : {

		// Wait for images to load before displaying
		// Requires predefined image dimensions
		// If 'auto' - will zoom in thumbnail if 'width' and 'height' attributes are found
		preload : "auto",

		// Protect an image from downloading by right-click
		protect : false

	},

	ajax : {

		// Object containing settings for ajax request
		settings : {

			// This helps to indicate that request comes from the modal
			// Feel free to change naming
			data : {
				fancybox : true
			}
		}

	},

	iframe : {

		// Iframe template
		tpl : '<iframe id="fancybox-frame{rnd}" name="fancybox-frame{rnd}" class="fancybox-iframe" frameborder="0" vspace="0" hspace="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen allowtransparency="true" src=""></iframe>',

		// Preload iframe before displaying it
		// This allows to calculate iframe content width and height
		// (note: Due to "Same Origin Policy", you can't get cross domain data).
		preload : true,

		// Scrolling attribute for iframe tag
		scrolling : 'no',

		// Custom CSS styling for iframe wrapping element
		css : {}

	},

	// Custom CSS class for layout
	baseClass : '',

	// Custom CSS class for slide element
	slideClass : '',

	// Base template for layout
	baseTpl	: '<div class="fancybox-container" role="dialog" tabindex="-1">' +
			'<div class="fancybox-bg"></div>' +
			'<div class="fancybox-controls">' +
				'<div class="fancybox-infobar">' +
					'<button data-fancybox-previous class="fancybox-button fancybox-button--left" title="Previous"></button>' +
					'<div class="fancybox-infobar__body">' +
						'<span class="js-fancybox-index"></span>&nbsp;/&nbsp;<span class="js-fancybox-count"></span>' +
					'</div>' +
					'<button data-fancybox-next class="fancybox-button fancybox-button--right" title="Next"></button>' +
				'</div>' +
				'<div class="fancybox-buttons">' +
					'<button data-fancybox-close class="fancybox-button fancybox-button--close" title="Close (Esc)"></button>' +
				'</div>' +
			'</div>' +
			'<div class="fancybox-slider-wrap">' +
				'<div class="fancybox-slider"></div>' +
			'</div>' +
			'<div class="fancybox-caption-wrap"><div class="fancybox-caption"></div></div>' +
		'</div>',

	// Loading indicator template
	spinnerTpl : '<div class="fancybox-loading"></div>',

	// Error message template
	errorTpl : '<div class="fancybox-error"><p>The requested content cannot be loaded. <br /> Please try again later.<p></div>',

	// This will be appended to html content, if "smallBtn" option is not set to false
	closeTpl : '<button data-fancybox-close class="fancybox-close-small"></button>',

	// Container is injected into this element
	parentEl : 'body',

	// Enable gestures (tap, zoom, pan and pinch)
	touch : true,

	// Enable keyboard navigation
	keyboard : true,

	// Try to focus on first focusable element after opening
	focus : true,

	// Close when clicked outside of the content
	closeClickOutside : true,

	// Callbacks; See Documentation/API/Events for description and samples
	beforeLoad	 : $.noop,
	afterLoad    : $.noop,
	beforeMove 	 : $.noop,
	afterMove    : $.noop,
	onComplete	 : $.noop,

	onInit       : $.noop,
	beforeClose	 : $.noop,
	afterClose	 : $.noop,
	onActivate   : $.noop,
	onDeactivate : $.noop
}
```
通过将有效对象传递给`fancybox()`方法来设置实例选项：
```html
$("[data-fancybox]").fancybox({
	image : {
		protect : true
	}
});
```
插件选项/默认值存放在`$.fancybox.defaults`的命名空间中，所以您可以轻松地在全局范围内进行调整：
```html
$.fancybox.defaults.speed = 600;
```
可以通过添加`data-options`属性对每一个元素自定义选项。此属性应包含正确格式的JSON对象：
```html
<a data-fancybox data-options='{"caption" : "My caption", "src : "iframe.html"}' href="javascript:;">
	Open external page using iframe
</a>
```
# API
fancyBox3 API提供了几种控制fancyBox3的方法。 这使的fancyBox3能够扩展插件并将其与其他Web应用程序组件集成。
### 内核方法
内核方法是影响/处理实例的方法：
```html
// Close only the currently active or all fancyBox instances
$.fancybox.close( all );

// Open the fancyBox right away
$.fancybox.open( items, opts, index );
```
当手动调用fancyBox时，每个组项应遵循以下模式：
```html
{
	src  : '' // Source of the content
	type : '' // Content type: image|inline|ajax|iframe|html (optional)
	opts : {} // Object containing item options (optional)
}
```
例如打开一个照片画廊：
```html
$.fancybox.open([
	{
		src  : '1_b.jpg',
		opts : {
			caption : 'First caption'
		}
	},
	{
		src  : '2_b.jpg',
		opts : {
			caption : 'Second caption'
		}
	}
], {
	loop : false
});
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/wgZXzz?editors=1010)

也可以只传递一个对象。例如打开一个内联内容。
```html
$.fancybox.open({
	src  : '#hidden-content',
	type : 'inline',
	opts : {
		onComplete : function() {
			console.info('done!');
		}
	}
});
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/JEVLgN?editors=1011)

如果希望显示一些html内容（例如，一条消息），则可以使用更简单的语法。 建议您在您的内容周围使用包装。
```html
$.fancybox.open('<div class="message"><h2>Hello!</h2><p>You are awesome!</p></div>');
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/VPNBaK)
### 实例方法
为了使用这些方法，需要一个插件对象的实例：
```html
var $instance = $.fancybox.getInstance();
```
或者使用fancyBox构造函数：
```html
var $instance = $("[data-fancybox]").fancybox();
```
一旦引用了fancyBox实例，就可以使用以下方法：
```html
// Go to next gallery item
$instance.next( duration );

// Go to previous gallery item
$instance.previous( duration );

// Switch to the other gallery item; accepts integer argument (an index of the desired item)
$instance.jumpTo( index, duration );

// Check if current image dimensions are smaller than actual
$instance.isScaledDown();

// Scale image to the actual size of the image
$instance.scaleToActual( x, y, duration );

// Check if image dimensions exceed parent element
$instance.canPan();

// Scale image to fit inside parent element
$instance.scaleToFit( duration );

// Move slider to current position
// Update all slides (and their content) if needed
$instance.update( andSlides, andContent, duration );

// Update slide position and make content fit in slide if needed
$instance.updateSlide( slide, andContent );

// Update infobar values, navigation button states and reveal caption
$instance.updateControls( force );

// Load custom content into the slide
$instance.setContent( slide, content );

// Try to find and focus on the first focusable element
$instance.focus();

// Activates current instance, brings it to the front
$instance.activate();

// Close instance
$instance.close();
```
你也可以这样做：
```html
$.fancybox.getInstance().jumpTo(1);
```
or simply:
```html
$.fancybox.getInstance('jumpTo', 1);
```
### 事件
fancyBox3可以触发以下几个事件。
```html
beforeLoad	 : Before the content of a slide is being loaded
afterLoad    : When the content of a slide is done loading
beforeMove 	 : Before slide change transition starts
afterMove    : After slide change transition is complete
onComplete	 : When slide change is complete and content has been loaded

onInit	 	 : When instance has been initialized
beforeClose	 : Before instance is closed
afterClose	 : After instance has been closed
onActivate   : When instance is brought to front
onDeactivate : When other instance has been activated
```
事件回调可以设置为options对象的函数属性传递给fancyBox初始化函数。
```html
<script type="text/javascript">
	$("[data-fancybox]").fancybox({
		onComplete: function( instance, slide ) {

			// Tip: Each event passes useful information within the event object:

			// Object containing references to interface elements
			// (background, buttons, caption, etc)
			// console.info( instance.$refs );

			// Current slide options
			// console.info( slide.opts );

			// Clicked element
			// console.info( slide.opts.$orig );

			// Reference to DOM element of the slide
			// console.info( slide.$slide );

		}
	});
</script>
```
每个回调接收两个参数-当前fancyBox实例和当前画廊对象（如果存在）。

也可以为所有实例附加事件处理程序。

为了防止干扰其他脚本，这些事件已命名为.fb。这些处理程序会收到3个参数-事件，当前fancyBox实例和当前画廊对象。

以下是绑定到`onComplete`事件的示例：
```html
$(document).on('onComplete.fb', function( e, instance, slide ) {
	// Your code goes here
});
```
如果你想防止关闭模态，例如，如果表单不能验证，你可以使用beforeClose回调。 只要返回false：
```html
beforeClose : function( instance, current, e ) {
	if ( $('#my-field').val() == '' ) {
		return false;
	}
}
```
# 模块
fancyBox代码分为几个扩展核心功能的文件（模块）。 如果需要，您可以通过排除不必要的模块来构建自己的fancyBox版本。 每个人都有自己的js和/或css文件。

一些模块可以通过编程方式进行定制和控制。 列出所有可能的选项：
```html
slideShow : {
	speed : 3000 // Slideshow speed in ms
},
touch : {
	vertical : true // Allow vertical swipe
},
thumbs : {
	showOnStart   : false, // Display thumbnails on opening
	hideOnClosing : true   // Hide thumbnail grid when closing animation starts
},
fullScreen : {
	requestOnStart : false // Request fullscreen mode on opening
},
hash : false // Hash value
```
示例（开始时显示缩略图）：
```html
$('[data-fancybox="images"]').fancybox({
	thumbs : {
		showOnStart : true
	}
})
```
[点击这里，查看案例](https://codepen.io/fancyapps/pen/RKKVVa?editors=1010)

如果您检查fancyBox3实例对象，您会发现命名为ar标识的键-这些是每个模块对象的引用。另外,fancyBox使用常用的命名约定来为jQuery对象添加$。

下面是你如何访问缩略图网格元素的例子：
```html
$.fancybox.getInstance().Thumbs.$grid
```
此示例显示如何调用切换缩略图的方法：
```html
$.fancybox.getInstance().Thumbs.toggle();
```
列出可用的方法：
```html
Thumbs.focus()
Thumbs.close();
Thumbs.update();
Thumbs.hide();
Thumbs.show();
Thumbs.toggle();

FullScreen.request( elem );
FullScreen.exit();
FullScreen.toggle( elem );
FullScreen.isFullscreen();
FullScreen.enabled();

SlideShow.start();
SlideShow.stop();
SlideShow.toggle();
```
如果要禁用hash模块，请使用此片段（包含JS文件之后）：
```html
$.fancybox.defaults.hash = false;
```
# FAQ
### 开启/关闭导致固定元素跳动
简单的添加`compensate-for-scrollbar`CSS类到你的固定的元素。例如使用Bootstrap导航栏组件的示例：
```html
<nav class="navbar navbar-inverse navbar-fixed-top compensate-for-scrollbar">
	<div class="container">
		..
	</div>
</nav>
```
该脚本测量滚动条的宽度，并为`margin-right`属性创建使用`compensate-for-scrollbar`CSS类。因此，如果您的元素有定义`width:100%`，则应使用`left`和`right`属性来定位。例如：
```html
.navbar {
	position: fixed;
	top: 0;
	left: 0;
	right: 0;
}
```
### 如何自定义标题
您可以使用接受函数的`caption`选项，并为每个组元素调用。附加图片下载链接示例：
```html
$( '[data-fancybox]' ).fancybox({
	caption : function( instance, item ) {
		var caption, link;

		if ( item.type === 'image' ) {
			caption = $(this).data('caption');
			link    = '<a href="' + item.src + '">Download image</a>';

			return (caption ? caption + '<br />' : '') + link;
		}
	}
});
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/ygeYGx?editors=1010)

内部添加标题方法，这是指被点击的元素。

使用不同的标题来源的示例：
```html
$( '[data-fancybox]' ).fancybox({
	caption : function( instance, item ) {
		return $(this).find('figcaption').html();
	}
});
```
[点击这里，查看案例](https://codepen.io/fancyapps/pen/bgEQXo?editors=1010)
### 如何在工具栏中创建自定义按钮
使用回调函数访问工具栏元素并添加自定义按钮的示例：
```html
$( '[data-fancybox]' ).fancybox({
	onInit : function( instance ) {
		instance.$refs.downloadButton = $('<a class="fancybox-button fancybox-download"></a>')
			.appendTo( instance.$refs.buttons );
	},
	beforeMove: function( instance, current ) {
		instance.$refs.downloadButton.attr('href', current.src);
	}
});
```
[点击这里，查看案例](http://codepen.io/fancyapps/pen/dNGapJ)
### 如何重新定位缩略图网格
当前没有JS选项来更改缩略图网格位置。但是，fancyBox3的设计使您可以使用CSS来更改每个块（例如，内容区域，标题或缩略图网格）的位置或维度。 如果需要，这可以让您自由地完全改变模态窗口的外观和感觉。
[点击这里，查看案例](http://codepen.io/fancyapps/pen/vgRajd)
