<template>
  <div class="container">
    <my-terminal :terminal="terminal"></my-terminal>
  </div>
</template>

<script>
import Console from "./terminal";
export default {
  name: "VersionControl",
  data() {
    return {
      terminal: {
        pid: 1,
        name: "terminal",
        cols: 800,
        rows: 800
      }
    };
  },
  components: {
    "my-terminal": Console
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>