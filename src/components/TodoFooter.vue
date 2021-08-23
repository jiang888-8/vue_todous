<template>
  <footer class="footer">
    <span class="todo-count">剩余<strong>：{{undoneList}}</strong></span>
    <ul class="filters">
      <li>
        <a :class="{selected:active === 'all'}" href="javascript:;" @click="$emit('setActive','all')">全部</a>
      </li>
      <li>
        <a :class="{selected:active === 'undone'}" href="javascript:;" @click="$emit('setActive','undone')">未完成</a>
      </li>
      <li>
        <a :class="{selected:active === 'done'}" href="javascript:;" @click="$emit('setActive','done')">已完成</a>
      </li>
    </ul>
    <button class="clear-completed" @click="clear">清除已完成</button>
  </footer>
</template>

<script>
export default {
  props: ['arr','active'],
  computed: {
    undoneList () {
      return this.arr.filter(item=>{
        return !item.isDone
      }).length
    }
  },
  methods: {
    clear () {
      const undone = this.arr.filter(item=>{
        return !item.isDone
      })
      this.$emit('onClear',undone)
    }
  }
}
</script>