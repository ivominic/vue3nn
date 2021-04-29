<template>
  <h1>{{ title }}</h1>
  <p></p>
  <input type="text" ref="name" />
  <button @click="toggleModal">Click me</button>
  <div class="" v-if="showModal">
    <Modal :header="header" :text="text" :arr="['first element', 4]" theme="sale" @closeEvent="toggleModal">
      <template v-slot:links>
        <a href="#">sign up</a>
        <a href="#">more info</a>
        <a href="#">about</a>
      </template>
      <h1>Slot title</h1>
      <p class="">Slot text</p>
    </Modal>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "My First Vue App",
      header: "This is value passed as prop",
      text: "Another prop value for text",
      showModal: false,
    };
  },
  methods: {
    toggleModal() {
      //console.log(this.$refs.name); //this.$refs provides access to any field with ref attribute
      //console.log(this.$refs.name.value);
      //this.$refs.name.classList.add("active");
      //this.$refs.name.focus();
      this.showModal = !this.showModal;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
