<template>
  <div id="app">
    <input type="number" v-model="num1">
    <span>+</span>
    <input type="number" v-model="num2">
    <span>= {{sum}}</span>
    <hr>
    <a :href="link">google</a>
    <hr>

    {{multiply}}

    <p v-html="link"></p>

  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      num1:0,
      num2:0,
      link:'<a href:"https://google.com">google</a>'
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
}
</script>