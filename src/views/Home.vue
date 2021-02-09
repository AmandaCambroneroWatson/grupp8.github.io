<template>
  <div class="app" :class="mode">
    <Header :mode="mode" @toggle="toggle"/>
  </div>
</template>

<script>
import Header from "../components/Header";

export default {
  name: "app",
  data() {
    return {
      mode: "dark",
    };
  },
  components: {
    Header,
  },
  methods:{
    toggle(){
      if(this.mode ==="dark"){
        this.mode ="light"
      } else{
        this.mode = "dark"
      }
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family:inter ui
}

.app {
  width: 100vw;
  min-height: 100vh;
  background-color:#ffffff;
  color: #000000;
  transition:background 0.3s ease-in-out;
}

.dark {
  background: #000000;
  color: #bdbdbd;
}
</style>