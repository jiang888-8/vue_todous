<template>
  <div class="todoapp">
    <todo-header @addend='add' :arr='list'></todo-header>
    <todo-main @delItem='delItems' :arr='filterList'></todo-main>
    <todo-footer @setActive='onSetActive' @onClear='del' :arr='list' :active='isActive'></todo-footer>
  </div>
</template>

<script>

import TodoHeader from './components/TodoHeader.vue'
import TodoMain from './components/TodoMain.vue'
import TodoFooter from './components/TodoFooter.vue'
export default {
  data () {
    return {
      isActive:'undone',// all 全部  undone 未完成  done 已完成
      list: JSON.parse(localStorage.getItem('listStr')) || [],
    }
  },

  watch: {
    list:{
      deep:true,
      handler () {
        localStorage.setItem('listStr',JSON.stringify(this.list))
      }
    }
  },

  components: {
    TodoHeader,
    TodoMain,
    TodoFooter
    
  },

  created () {

  },

  methods: {
    add (val) {
      const filg = this.list.some(item=>item.name === val)
      if(filg) return alert('任务已存在！')
      const id = this.list.length > 0 ? this.list[this.list.length-1].id + 1 : 100
      this.list.push({
        id:id,
        name:val,
        isDone:false
      })

    },

    del (undone) {
      this.list = undone
    },

    onSetActive (val) {
      this.isActive = val
    },

    delItems (id) {
      const index = this.list.findIndex(item=>{
        return item.id === id
      })
      this.list.splice(index,1)
    },
 },

  computed: {
    filterList () {
      if(this.isActive === 'undone') {
        return this.list.filter(item=>{
          return !item.isDone
        })
      }
      if(this.isActive === 'done') {
        return this.list.filter(item=>{
          return item.isDone
        })
      }
      return this.list
    }
  },
}

</script>

<style scoped>

</style>

