# MVVM

手写一个简单的MVVM框架

**不同的MVVM框架中，实现双向数据绑定的技术有所不同。目前一些主流的前端框架实现数据绑定的方式大致有以下几种**
- 数据劫持 (Vue)
- 发布-订阅模式 (Knockout、Backbone)
- 脏值检查 (Angular)

今天我们就来看看Vue怎么实现的

1. Object.defineProperty() 实现数据拦截

- Object.defineProperty()方法会直接在一个对象上定义一个新属性,或者修改一个对象现有属性

语法:
```
Object.defineProperty(obj, prop, description)
+ obj: 目标对象  prop: 要定义的属性  des: 属性描述符

var obj = {}

Object.defineProperty(obj, intro, {
	configerable: false,  // 能否通过delete删除属性从而重新定义属性
	enumerable: false,  // 能否通过for-in循环返回属性
	writeable: false,  // 能否修改属性的值  数据描述符
	value: 'yym'   // 属性的数据值   数据描述符
})
// get set 与 value writeable 不能同时存在
Object.defineProperty(obj, age, {
	configerable: false,  // 能否通过delete删除属性从而重新定义属性
	enumerable: false,  // 能否通过for-in循环返回属性

	get: function(){  // 存取描述符

	},
	set: function(val){// 存取描述符

	}

})
```

2. MVVM

- MVVM(Modal View ViewModal)是一种用于把数据和UI分离的一种模式

Modal表示应用程序使用的数据,Modal保存信息,但通常不处理行为,不会对信息再次加工

View是与用户交流的桥梁

ViewModal充当数据转换器, 将Modal信息转换为View信息, 将命令从View传到Modal

3. 单项绑定
- 观察数据
- 解析模板,替换为对应的值
- 解析到对应值时,创建一个观察者,观察属性



