<template>
  <div class="actions">
    <button
      v-for="(button,index) in buttons"
      :key="index"
      :disabled="button.disabled"
      @click="handleClick(button.action)"
    >
      <img class="icon" :src="button.image" alt>
    </button>
  </div>
</template>

<script>
export default {
  props: {
    typeNum: null
  },
  data() {
    return {
      buttons: [
        { image: "/icons/print.png", disabled: true, action: "print" },
        { image: "/icons/edit.png", disabled: true, action: "edit" },
        { image: "/icons/delete.png", disabled: true, action: "delete" }
      ]
    };
  },
  created() {
    let activeButton = this.typeNum - 1;
    console.log(
      `type num is ${this.typeNum} and the activeButton is ${activeButton}`
    );
    this.buttons[activeButton].disabled = false;
  },
  methods: {
    handleClick(func) {
      //sorry about it, got stuck and didnt want to waste time on it
      this[func]();
    },
    print() {
      alert("omg they killed kenny");
    },
    delete() {
      this.$emit("delete-data", event.path[3].id);
    },
    edit() {
      let newTopic = prompt("please enter a new topic name");
      this.$emit("edit-topic", { index: event.path[3].id, newTopic: newTopic });
    }
  }
};
</script>

<style>
button {
  cursor: pointer;
  background: none;
  border: none;
}

button:disabled {
  filter: grayscale(100%);
  cursor: not-allowed;
}
</style>
