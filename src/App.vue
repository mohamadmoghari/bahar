<template>
  <div id="app">
    <div id="header">
      <button @click="addItem">Add New Item</button>
    </div>
    <br />
    <div v-for="item in todoItems" :key="item.id">
      <todoItem
        v-on:saveToParent="saveData"
        v-on:deleteToParent="deleteData"
        v-on:markToParent="markItem"
        :key="item.id"
        :id="item.id"
        :mark="item.markAsDone"
        :message="item.message"
        :saved="item.saved"
      />
    </div>
  </div>
</template>

<script>
import TodoItem from "./components/todoItem.vue";

export default {
  name: "App",
  components: {
    todoItem: TodoItem,
  },
  data() {
    return {
      todoItems: [],
    };
  },
  methods: {
    /********************************* */
    setConsole(message) {
      console.log(message);
    },

    getGuid() {
      return Math.floor(Math.random() * 0x10000).toString(16);
    },
    getArrayIndex(id) {
      for (let index = 0; index < this.todoItems.length; index++) {
        if (this.todoItems[index].id === id) {
          return index;
        }
      }
      return -1;
    },

    /*********************************8 */

    addItem() {
      this.todoItems.push({
        id: this.getGuid(), //this.todoItems.length+1,
        message: "",
        markAsDone: false,
        saved:false
      });
    },
    saveData(id, message) {
      let index = this.getArrayIndex(id);
      if (index >= 0) {
        this.todoItems[index].message = message;
        this.todoItems[index].saved=true;
      }
    },
    deleteData(id) {
      let deletedIndex = this.getArrayIndex(id);
      this.setConsole(deletedIndex);
      if (deletedIndex >= 0) this.todoItems.splice(deletedIndex,1);
    },
    markItem(id, check) {
      let index = this.getArrayIndex(id);
      if (index >= 0) this.todoItems[index].markAsDone = check;
    },
  },
};
</script>
<style scoped>
#div1 {
  width: 50px;
  height: 50px;
  background-color: yellow;
}
</style>