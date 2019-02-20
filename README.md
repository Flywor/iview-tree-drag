# iview-tree-drag
基于iview的tree组件拓展了拖拽功能和远程加载

###
[在线演示](https://flywor.github.io/iview-tree-drag/dist/index.html " 在线演示")

###
* 参数
```
  // 接收返回Promise的方法
  getChild: {
  type: Function,
  default: null
  }
```

* 事件
```javascript
  // 节点选择触发
  // node 选择的树节点
  on-select(node)
```
```javascript
  // 拖拽完成触发
  // dragNode 拖拽的树节点
  // dropNode 拖拽至目标的树节点
  // position 拖拽到目标节点的位置('before' 'inner' 'after')
  // event 拖拽结束事件本身
  on-drag(dragNode, dropNode, position, event)
```

* 如果你喜欢的话帮忙点个star表示支持
* 谢谢

联系方式
QQ和邮箱： 244406664
