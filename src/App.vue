<template>

  <div id="app">
    <div id="header">
      <button @click="addItem">Add New Item</button>
    </div>
    <div v-for="item in todoItems" :key="item.id">
    <todoItem  v-on:cildToParent="saveData" :key="item.id" :id="item.id" :message="item.message"/>
    </div>
  </div>
</template>

<script>

import TodoItem from './components/todoItem.vue';

export default {
  name: 'App',
  components: {
    todoItem:TodoItem,
  },
  data() {
    return {
      todoItems:[]
    }
  },
  methods: {
    addItem() {
      this.todoItems.push({
        id:this.todoItems.length+1,
        message:''
      });
    },
    saveData(id, message)
    {
     this.todoItems[id-1].message=message
    }
  },
}
</script>
<style scoped>
#div1{
width:50px;
height: 50px;
background-color: yellow;
}
</style>