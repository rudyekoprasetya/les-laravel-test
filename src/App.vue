<template>
  <div id="app">
      <!-- navbar  -->
      <NavBar />
      <!-- navbar  -->
    <!-- content  -->
    <div class="container">
      <router-view/>
    </div>
    <!-- content  -->
     
  </div>
</template>
 
<script>
  import NavBar from "@/components/NavBar.vue"
  export default {
    name: "App",
    components: {
      NavBar,
    }
  }
</script>
 
<style>
 
</style>