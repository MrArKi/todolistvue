<template>
  <div>
    <div>
      <input v-model="inputValue"/>
      <button @click="handleSumbit">提交</button>
    </div>
    <ul>
      <todo-item v-for="(item,index) of list"
                 :key="index"
                 :content="item"
                 :index="index"
                 @delete="handle"
      ></todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem'

export default {
  name: 'App',
  components: {
    'todo-item': TodoItem
  },
  data () {
    return {
      inputValue: '',
      list: []
    }
  },
  methods: {
    handleSumbit: function () {
      this.list.push(this.inputValue)
      this.inputValue = ''
    },
    handle: function (index) {
      this.list.splice(index, 1)
    }
  }
}
</script>

<style>

</style>
