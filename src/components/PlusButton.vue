<template>
  <button class="addTaskButton" @click="openOverlay"></button>
</template>

<script>
  export default {
    methods: {
      openOverlay() {
        this.$emit('openOverlay')
      }
    }
  }
</script>

<style scoped>
  .addTaskButton {
    position: relative;
    bottom: -48px;
    background-image: Url('~@/assets/Plus.svg');
    background-position-x: center;
    background-position-y: center;
    background-repeat: no-repeat;
    border-radius: 30px;
    background-color: #5db075;
    border: none;
    height: 58px;
    width: 58px;
  }
  #Button {
    bottom: 80px;
    right: 30px;
    position: fixed;
  }
  @media only screen and (min-device-width: 1000px) {
    .addTaskButton {
      position: static;
      background-image: Url('~@/assets/Plus.svg');
      background-position-x: center;
      background-position-y: center;
      background-repeat: no-repeat;
      border-radius: 30px;
      background-color: #5db075;
      border: none;
      height: 58px;
      width: 58px;
    }
  }
</style>
