<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <h1>{{ header }}</h1>
      <p>{{ text }} - {{ arr[0] }} * {{ arr[1] }}</p>
      <slot>Default content - only shows if we don't pass the slot</slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  props: ["header", "text", "arr", "theme"],
  methods: {
    closeModal() {
      this.$emit("closeEvent");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}
.modal h1 {
  color: aqua;
}
.modal .actions {
  text-align: center;
  margin: 30px 0 10px 0;
}
.modal .actions a {
  color: #333;
  padding: 8px;
  border: 1px solid white;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}
.modal.sale {
  background: crimson;
  color: aliceblue;
}
.modal.sale h1 {
  color: white;
}
.modal.sale .actions {
  color: aliceblue;
}
.modal.sale .actions a {
  color: white;
}
</style>
