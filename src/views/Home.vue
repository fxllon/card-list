<template>
  <div class="home">
    <app-bar title="写个标题" left="search" right="crosshairs" />
    <tab-list />
    <div>这是底部a</div>
  </div>
</template>

<script>
import AppBar from '../components/AppBar.vue'
import TabList from '../components/TabList.vue'
export default {
  name: 'home',
  components: {
    AppBar,
    TabList
  }
}
</script>

<style lang="scss">
.home {
  height: 100%;
  width: 100%;
  overflow: hidden;
  color: white;
  background-image: linear-gradient(to top, #99acbe 5%, #a8b3bf 20%, #cfd7dd);
}
</style>