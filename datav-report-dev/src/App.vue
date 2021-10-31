<template>
  <div id="app">
    <div>
      <home />
    </div>

  </div>
</template>

<script>
import Home from './views/Home'
export default {
  name: 'app',
  components: {
    Home
  }
}
</script>

<style>
 html, body, #app {
   width: 100%;
   height: 100%;
   margin: 0;
   padding: 0;
 }
</style>
