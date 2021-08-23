<template>
  <ul class="todo-list">
    <!-- completed: 完成的类名 -->
    <li :class="{completed:item.isDone}" v-for="(item) in arr" :key="item.id">
      <div class="view">
        <input v-model="item.isDone" class="toggle" type="checkbox" />
        <label>{{item.name}}</label>
        <button class="destroy" @click="del(item.id)"></button>
      </div>
    </li>
  </ul>
  
</template>

<script>
export default {
  props: ['arr'],

  methods: {
    del (id) {
      this.$emit('delItem',id)
      
    }
  }
}
</script>