<template>
  <div id="q-app">
    <router-view />
  </div>
</template>
<script>
export default {
  name: 'App'
}
</script>

<style>
#q-app {
  margin:auto;
  background-repeat: repeat;
  background: url("assets/zzz.png"), rgb(14, 14, 14);
  background-blend-mode: multiply;
  z-index:-1;
}
</style>