<template>
  <div>
    <h1>简易Todolist</h1>
    <input v-model="inputValue"/>
    <button v-on:click = "handleSubmit">提交</button>
    <ul>
      <todo-item  
          v-for="(item, index) of list" 
          :key="index"
          :content="item"
          :index="index"
          @delete="handleDelete"
          >
      </todo-item>
    </ul>
  </div>
</template>

<script>
/*使用小组件 */
import TodoItem from './components/TodoItem'


export default {
  /*将局部组件绑定到该标签之上*/
  components: {
    'todo-item':TodoItem
  },
  data: function () {
    return {
      inputValue: '',
      list: []
    }
  },
  methods: {
    handleSubmit () {
      this.list.push(this.inputValue);
      this.inputValue = '';
    },
    handleDelete (index) {
      this.list.splice(index, 1)
    }
  }
}
</script>

<style>

</style>
