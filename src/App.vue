<template>
  <div id="app">
    <div>
      <p>选择了：{{selected.title}}</p>
      <TreeDrag :getChild="getChild" @on-select="handlerSelect" @on-drag="handlerDrag" titleKey="name"/>
    </div>
    <div>
      <p>拖拽历史</p>
      <p v-for="(json, index) in dragHis" :key="index">
        ID: {{json.from.id}}({{json.from.title}}) --->> ID: {{json.to.id}}({{json.to.title}})
        <strong>Position: {{json.position}}</strong>
      </p>
    </div>
  </div>
</template>

<script>
import TreeDrag from './components/tree-drag'
export default {
  name: 'app',
  components: { TreeDrag },
  data () {
    return {
      split: 0.5,
      selected: {},
      dragHis: []
    }
  },
  methods: {
    getChild (node) {
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          const data = []
          // 接口获取数据加载子节点
          for (let i = 0; i < 10; i++) {
            const child = {
              name: `测试节点${node.nodeKey}-${i}`,
              id: `${node.nodeKey}${i}`,
              loading: false,
              children: []
            }
            if (i >= 5) {
              delete child.loading
              delete child.children
            }
            data.push(child)
          }
          resolve(data)
        }, 1000)
      })
    },
    handlerSelect (node) {
      this.selected = node
    },
    handlerDrag (from, to, position, e) {
      this.dragHis.push({
        from, to, position, e
      })
    }
  }
}
</script>
<style lang="less">
html, body{
  height: 100%;
  width: 100%;
  margin: 0;
}
#app {
  height: 100%;
  width: 100%;
  &>div{
    display: inline-block;
    width: 49%;
    min-height: 100%;
    vertical-align: top;
    padding: 50px;
  }
  &>div:first-child{
    border-right: 1px solid #dcdee2;
  }
  *{
    font-size: 18px;
  }
}
</style>
