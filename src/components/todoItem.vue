 <template>
  <div>
      <textarea id="txt" cols="30" rows="10" v-model="message"></textarea>
      <br>
      <button @click="saveData(id,message)">save</button>
    </div>
</template>

<script>
export default {
  methods: {
    saveData(id,message) {
console.log(id +'   '+ message);

      this.$emit('saveData',{id,message})
    }
  },
props: ["message","id"]

}
</script>

<style>

</style>