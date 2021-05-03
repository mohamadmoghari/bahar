 <template>
  <div>
      <textarea id="txt" cols="30" rows="10" v-model="innerMessage"></textarea>
      <br>
      <button @click="saveData(innerId,innerMessage)">save</button>
    </div>
</template>

<script>
export default {
  data() {
    return {
      innerMessage: this.message,
      innerId:this.id
    }
  },
  methods: {
    saveData(i,m) {
      
      this.$emit('cildToParent',i,m)
    }
  },
props: ["message","id"]

}
</script>

<style>

</style>