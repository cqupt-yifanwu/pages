# pages利用原生js实现分页功能的函数插件

### 介绍

<p>改插件完全利用原生js写成，在演示中我将数据固定在html文件中（实际项目中可以从服务端获取），该插件中集成了原生ajax的函数以便支持有后端交互的需求。
</p>

### 使用

* 插件是page-plug.js文件
* 在你需要使用的html中引入page-plug.js，然后在你的js文件中使用pageControl函数即可，参数等格式参照下面的注意事项内容。

### 注意

* 在此插件中需要的参数个数比较多，所以我们采用配置参数的办法传参，参数的格式如下：
		obj = {  
			branches: number,  		// 含义：每页要展示的信息的条数
			pageNav: DOMObject, 	// 含义：分页下导航的容器，里面的按钮是插件自动生成的，可以为其添加样式
			ctsList: DOMObjects, 	// 含义：需要分页的总的内容的条数  注意：这里是数据确定的条件下需要的参数
			prev: DOMobject, 		// 含义：上一页按钮
			next: DOMobject, 		// 含义：下一页按钮
			url: url, 				// 含义：请求数据的地址（非必需）
			contentUl: DOMobject 	// 含义：包含信息的容器-ul元素（当数据需要从服务端获取的时候需要此参数）
 		 }
* 如果需要从服务端获取数据，该插件需要手动做一些改变：
	1. 将第27行从服务端获取数据的函数从注释中打开
	2. 然后将第46行-100行放入37行的函数中（ajax的成功回调函数）
* 服务端需要遵循的数据格式为：
		[{
			text: ...内容...
		},
		{
			text: ...内容...
		}]

### ES6等模块化

* 需要将函数export出去然后利用import引入我们需要使用的地方