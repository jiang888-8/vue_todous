<template>
  <div class="todoapp">
    <todo-header></todo-header>
    <todo-main></todo-main>
    <todo-footer></todo-footer>
  </div>
</template>

<script>

import TodoHeader from './components/TodoHeader.vue'
import TodoMain from './components/TodoMain.vue'
import TodoFooter from './components/TodoFooter.vue'
export default {
  data () {
    return {
      
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

  }
}
</script>

<style scoped>

</style>

