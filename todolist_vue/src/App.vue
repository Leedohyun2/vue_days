<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoFooter from './components/TodoFooter.vue';
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';

export default {
  props: ['propsdata'],
  data() {
    return {
      todoItems: []
    }
  },

  created() {
        if(localStorage.length > 0) {
            for(var i = 0; i < localStorage.length; i++) {
                this.todoItems.push(localStorage.key(i));
            }
        }
    },

  methods: {
    addTodo() {
      // 로컬 스토리지에 데이터 추가하는 로직
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },

    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    }
  },

  components: {
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter
  }
}
</script>

<style>
body {
  text-align: center;
  background: #F6F6F8;
}

input {
  border-style: groove;
  width: 200px;
}

button {
  border-style: groove;
}

.shadow {
  box-shadow: 5px 10px 10px rgba(0,0,0,0.03);
}
</style>
