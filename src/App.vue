<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
    name: "App"
};
</script>

<style> 
html,
body {
    min-width:1280px;
    height: 100%;
    box-sizing: border-box;
    padding: 0px;
    margin: 0px;
    background: #E6E6E6;
}
#app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    widows: 100%;
    height: 100%;
}
*{
  padding: 0;
  margin: 0;
}
</style>
