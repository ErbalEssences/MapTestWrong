<template>
  <div id="app">
    <World />
  </div>
</template>

<script>
import World from './components/World.vue'

export default {
  name: 'App',
  components: {
    World
  }
}
</script>

<style scoped lang="scss">

$background-red: #ae0001;
$dark-red: #7e0607;
$land-red: #960202;



#app {
    background-color: $background-red;
    min-height: 100%;
    position: fixed;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    z-index: 10;
}
</style>


