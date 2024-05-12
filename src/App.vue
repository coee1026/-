<template>
  <!-- 主体区域 -->
  <section id="app">
    <!-- 输入框 -->
    <todoHeaderVue @addEvent="add"></todoHeaderVue>

    <!-- 列表区域 -->
    <todoMainVue :list="list" @delEvent="del"></todoMainVue>
    
    <!-- 统计和清空 -->
    <todoFooterVue :list="list" @clearEvent="clear"></todoFooterVue>
  </section>
</template>

<script>
import todoFooterVue from './components/todoFooter.vue'
import todoHeaderVue from './components/todoHeader.vue'
import todoMainVue from './components/todoMain.vue'
// import todoFooterVue
export default {
  // todoHeaderVue,
  components: {
    todoHeaderVue,
    todoMainVue,
    todoFooterVue
  },
  data () {
    return {
      list: JSON.parse(localStorage.getItem('todoList')) || [{id: 1, name: '跑步'}, {id: 2, name: '学习'}]
    }
  },
  methods: {
    add (name) {
      this.list.push({di: +new Date(), name})
      
    },
    clear () {
      this.list = []
    },
    del (id) {
      this.list = this.list.filter(item => item.id !== id)
    }
  },
  watch: {
    list: {
      deep: true,
      handler (newvalue) {
        console.log(111);
        console.log(newvalue);
        localStorage.setItem('todoList', JSON.stringify(newvalue))
      }
    }
  }
}
</script>

<style>

</style>
