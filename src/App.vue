<template>
  <div id="app">
    <div class="space"></div>
    <div class="content">
      <todo-input @todoAdded="addNew"></todo-input>
      <todo-list>
        <todo-item 
          v-for="item in items" :key="item.id" 
          :item="item" 
          @updateTodo="updateTodo"
          @deleteTodo="deleteTodo"
          @itemCheck="itemCheck" 
          />
      </todo-list>
    </div>
    <div class="space"></div>
  </div>
</template>

<script>
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoItem from './components/TodoItem.vue';
export default {
  components: {
    TodoInput,
    TodoList,
    TodoItem
  },
  data () {
    return {
      items: [
        {
          id: 1,
          todo: "Learning Vue.js",
          completed: false
        },
        {
          id: 2,
          todo: "Buildning Todo App",
          completed: true
        }
      ]
     
    }
  },
  computed: {
    itemLength(){
      return this.items.length;
    },
    getId(){
      if(this.items.length) {
        return this.items[this.itemLength - 1].id + 1;
      }
      return 1; 
    }
  },
  methods: {
      addNew(todo) {
        this.items.push({
          id: this.getId,
          todo,
          completed: false,
        })
      },
      itemCheck(Id) {
        this.items = this.items.map( item => {
          if(item.id === Id) {
            return {...item,completed : !item.completed};
          }
          return item;
        })
      },
      deleteTodo(Id) {
       this.items = this.items.filter(item => item.id !== Id);
      },
      updateTodo(todo) {
        this.items = this.items.map(item => {
          if(item.id == todo.id){
            return {
              ...todo
            } 
          } return item;
        })
      }
    },
}
</script>

<style scoped>
  #app {
    margin: 50px auto;
    width: 800px;
    padding: 50px 40px;
    background-color: rgb(230, 230, 230);
  }
</style>
