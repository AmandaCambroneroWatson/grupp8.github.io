<template>
  <header>
    <h1>{{ mode }} Plamera</h1>
    <Toggle :mode="mode" @toggle="$emit('toggle')"/>
    <nav>
      <div class="nav-link">How it works</div>
      <div class="nav-link">About us</div>
      <div class="nav-link">Contact us</div>
      <div class="nav-link">Sign up detta ska vara en button</div>
    </nav>
  </header>
</template>

<script>
import Toggle from '@/components/Toggle'
export default {
  props: ["mode"],
  components:{
      Toggle,
  }
};
</script>

<style>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0px 25px;
  height: 60px;
  background: #ffffff;
  transition: background 0.3s ease-in-out;
  
}

.dark header{
    background: #000000;

}

header h1 {
  font-size: 30px;
  font-weight: 900;
}

header nav {
  display: flex;
  height: 60px;
}

header nav .nav-link {
  display: flex;
  align-items: center;
  padding: 0px 15px;
}

header nav .nav-link:hover{
    background:#F0F0F0;

}

.dark header nav .nav-link:hover{
    background: #464646;
}
</style>