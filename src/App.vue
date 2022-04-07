<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <VideoPlayer />
</template>

<script>
  import VideoPlayer from './components/VideoPlayer.vue'

  export default {
    name: 'App',
    components: {
      VideoPlayer
    }
  }
</script>

<style>
  :root {
    --Primary: #343a40;
    /* --Primary: #43DDE6; */
    --White: #ffffff; 
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  body {
    color: var(--White);
    background-color: var(--Primary);
  }
</style>
