<template>
  <div id="modal">
    <div id="modal-container">
      <h2>
        Picked Names
        <span @click="close">
          &times;
        </span>
      </h2>
      
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    close() {
      this.$emit('close');
    }
  }
}
</script>

<style scoped>
h2 {
  border-bottom: 2px solid yellow;
  padding: 10px;
  display:flex;
  justify-content: space-between;
}

h2 span {
  cursor: pointer;
}
#modal {
  position: fixed;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100vh;
  font-size: 22px;
  border-radius:5px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: black;
  opacity: 0.9;
}

#modal-container {
  width: 500px;
  min-height: 100px;
  background: purple;
  border-top: 10px solid orange;
  padding: 20px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  margin: 10px;
}
@media screen and (max-width: 600px) {
  /* #modal-container {
    width: 100%;
    box-sizing: border-box;
  } */
}
</style>