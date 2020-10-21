<template>
  <div id="todo-item">
      <span :class="{grey:item.completed}">{{ item.todo }}</span> <a href="#"> {{ item.id }} </a> <br>
      <input type="checkbox" :checked="item.completed" @click="check">
  </div>
</template>

<script>
export default {
    props: ['item'],
  data () {
    return {
     
    }
  },
  methods: {
      check(){
          this.$emit('itemCheck', this.item.id);
      }
  },
}
</script>

<style>
#todo-item{
    margin-left: 10px !important;
    background-color: olivedrab;
    font-family: 'Roboto', sans-serif;
    color: #fff;
    padding: 20px 15px;
    position: relative;
}

#todo-item a {
    position: absolute;
    top: 1px;
    right: 1px;
    color: orangered;
    text-decoration: none;
    background-color: papayawhip;
    padding: 3px 7px;
    font-size: 12px;
}
#todo-item input {
    margin-top: 15px;
}

.grey {
    color: rgb(163, 163, 163);
}

</style>
