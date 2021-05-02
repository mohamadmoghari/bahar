<template>
  <div id="app">
    
    
  </div>
</template>

<script>

import TodoItem from './components/todoItem';

export default {
  name: 'App',
  data() {
    return {
      num1:0,
      num2:0,
      link:"https://google.com",
      link2:'<a href="https://google.com">google</a>',
      counter:0,
    }
  },
  computed: {
    sum() {
      return parseInt(this.num1)+parseInt(this.num2);
    },
    multiply()
    {
      return parseInt(this.num1)* parseInt(this.num2);
    }
  },
  methods: {
    showAlert(message) {
      alert(message);
    },
    divClick(){
        return this.counter++;
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