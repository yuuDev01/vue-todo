<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data(){
    return{
      //todoItems 데이터 속성
      todoItems:[]
    }
  },
  created(){
        if(localStorage.length>0){
            // 로컬저장소가 비어있지 않는 경우 todoItems에 저장
            for(var i = 0; i<localStorage.length; i++){
                if(localStorage.key(i) != "loglevel:webpack-dev-server")
                this.todoItems.push(localStorage.key(i));

            }
        }
    },
  methods:{
    addTodo(todoItem){ //todoItem : input컴포넌트에서 인자값으로 보낸 value
      //localStorge에 데이터 추가
      localStorage.setItem(todoItem,todoItem);
      //todoItems에 데이터 추가
      this.todoItems.push(todoItem)

    },
    clearAll(){
      localStorage.clear();
      this.todoItems=[];
    },
    removeTodo(todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    }
  },
  components :{
    'TodoHeader' : TodoHeader,
    'TodoInput' : TodoInput,
    'TodoList' : TodoList,
    'TodoFooter' : TodoFooter
  }
}
</script>

<style>
  body {
    text-align: center;
    background-color: #F6F6F8;
  }
  input {
    border-style: groove;
    width: 200px;
  }
  button{
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
  }
</style>
