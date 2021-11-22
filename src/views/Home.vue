<template>
  <div class="home">
<!--    <img alt="Vue logo" src="../assets/logo.png">-->
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
<!--    <Date/>-->
    <Calculate/>
    <a href="https://beian.miit.gov.cn/" target="_blank" class="beian">京ICP备2021025191号</a>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
// import Date from '@/components/Date'
import Calculate from "@/components/Calculate";
export default {
  name: 'Home',
  components: {
    Calculate,
    // HelloWorld
    // Date
  }
}
</script>
<style>
  .beian{
    position: fixed;
    bottom: 0;
    right: 45%;
  }
</style>
