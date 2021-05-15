 <template>
  <div>
    <div id="divTxt">
      <textarea id="txt" cols="10" rows="8" v-model="innerMessage"></textarea>
    </div>
    <div v-show="innerSaved" id="divButton">
      <button @click="deleteData(innerId)">delete</button>
      <br />
      <div v-if="innerMark === false">
        <button @click="markData">mark as done</button>
      </div>
      <div v-else>
        <button @click="markData" style="background: green">
          mark as done
        </button>
      </div>
    </div>
    <br />
    <button @click="saveData(innerId, innerMessage)">save</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      innerMessage: this.message,
      innerId: this.id,
      innerMark: this.mark,
      innerSaved: this.saved,
    };
  },
  methods: {
    /**************************** */
    setConsole(message) {
      console.log(message);
    },
    /**************************** */
    saveData(i, m) {
      this.innerSaved = true;
      this.$emit("saveToParent", i, m);
    },
    deleteData(i) {
      this.$emit("deleteToParent", i);
    },
    markData() {
      this.innerMark = !this.innerMark;
      this.$emit("markToParent", this.innerId, this.innerMark);
    },
  },
  props: ["message", "id", "mark", "saved"],
};
</script>

<style>
#divTxt {
  display: inline-flex;
}
#divButton {
  display: inline-flex;
}
</style>
