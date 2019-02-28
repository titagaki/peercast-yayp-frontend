<template>
  <div>
    <vs-navbar :color="colorx" class="nav-bar">
      <div slot="title">
        <vs-navbar-title>
          Hello world
        </vs-navbar-title>
      </div>
    </vs-navbar>
  </div>
</template>

<script>
  export default {
    data: ()=>({
      colorx:'#1db952',
    })
  }
</script>

<style lang="stylus" scoped>
  .nav-bar
    color rgb(255,255,255)
</style>