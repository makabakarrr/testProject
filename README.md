# testProject
learning
1111111


问题：
报错：在div元素上设置了aria-hidden=true，不能在焦点元素或其祖先元素上添加。
场景：chrome，版本127之后，其他浏览器没有这个问题
相关概念：
aria-hidden=true：这个属性用来标识需要对无障碍技术隐藏的内容。在创建DOM树之后，浏览器会根据DOM树中的创建无障碍树，设置了aria-hidden=true的元素及其子元素不会添加到树里，屏幕阅读器的api会根据无障碍树进行工作。一般将其添加到装饰作用的元素、需要隐藏的元素上
焦点元素：一些可以进行用户交互的元素，比如表单元素
gmd-modal中有两个div使用了aria-hidden=true， 但是在控制台上看到这两个div里并没有内容
<div tabindex="0" aria-hidden="true" style="width: 0px; height: 0px; overflow: hidden;"></div>
tabindex属性用来标识元素是否可以使用tab键聚焦，值0-可通过tab键聚焦，负值可聚焦但不能通过tab健聚焦，正值表示顺序

解决办法：移除aria-hidden
1）官方：手动在modal组件源码中移除aria-hidden=true
2）定义全局指令，在需要移除aria-hidden的组件上使用（获取dom，移除属性）