<h1 style="text-align:center">React学习</h1>
###基本结构
	<html>
	  <head>
	    <title>Hello React</title>
	    <script src="http://fb.me/react-0.13.0.js"></script>
	    <script src="http://fb.me/JSXTransformer-0.13.0.js"></script>
	    <script src="http://code.jquery.com/jquery-1.10.0.min.js"></script>
	  </head>
	  <body>
	    <div id="content"></div>
	    <script type="text/jsx">
	      // Your code here
	    </script>
	  </body>
	</html>
	
>注意： jQuery对 React 并不是必须的。


创建React组件：
React.createClass(),其中最重要的方法是 render ，该方法返回一颗 React 组件树，这棵树最终将会渲染成 HTML 。
ReactDOM.render() 实例化根组件，启动框架，把标记注入到第二个参数指定的原生的 DOM 元素中。
React 的 JSX 里约定分别使用首字母大、小写来区分本地组件的类和 HTML 标签。

使用属性：props
该组件依赖于从父级传入的数据。从父组件传入的数据会做为子组件的 属性（ property ） ，这些 属性（ properties ） 可以通过 this.props 访问到。
我们通过 this.props 来访问传入组件的数据，键名就是对应的命名属性，也可以通过 this.props.children 访问组件内嵌的任何元素。


this.props.children 的值有三种可能：如果当前组件没有子节点，它就是 undefined ;如果有一个子节点，数据类型是 object ；如果有多个子节点，数据类型就是 array 。所以，处理 this.props.children 的时候要小心。


dangerouslySetInnerHTML 插入原始的html




从服务器获取数据 


响应状态变化：
props 是不可变的：它们从父组件传递过来，“属于”父组件。在组件初始化时渲染自己。
this.state 是组件私有的，可以通过调用 this.setState() 来改变它。当 state 更新之后，组件就会重新渲染自己。

render() 方法依赖于 this.props 和 this.state ，框架会确保渲染出来的 UI 界面总是与输入（ this.props 和 this.state ）保持一致。


绑定事件：
React 使用驼峰命名规范的方式给组件绑定事件处理器，例如onClick、onSubmit


Refs:
我们利用 ref 属性给子组件命名，通过 this.refs 引用 DOM 节点。


组件的生命周期与事件处理:
在React中，每一个组件都包含一个 this.state 属性，当通过 this.setState() 方法设置组件的状态之后，React都会调用Render方法重绘组件。而在这个过程中React将会通过diff算法比较虚拟的DOM树与实际的DOM并且只变更之间差异的部分，从而保证高性能的局部刷新。

组件生命周期：
Mounting： 组件将要插入到DOM当中； 
对应的处理函数：
getInitialState()：object在组件mounted之前调用，返回组件的初始状态
componentWillMount()
componentDidMount()
Updating：组件在重绘render时(必要时)；
componentWillReceiveProps()
shouldComponentUpdate()
componentWillUpdate()
componentDidUpdate()
Unmounting：组件将会从DOM中移除时；
componentWillUnmount