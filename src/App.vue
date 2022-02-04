<template>
  <div id="app">
    <div id="nav"></div>
    <router-view />
  </div>
</template>

<script>
export default {
  mounted() {
    window.addEventListener("keypress", (e) => {
      console.log(String.fromCharCode(e.keyCode));
    });
  },
};
</script>
