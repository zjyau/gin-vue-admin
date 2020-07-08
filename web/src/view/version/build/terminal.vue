<template>
  <div class="console" id="terminal"></div>
</template>
<script>
import Terminal from "./xterm";
export default {
  name: "Console",
  props: {
    terminal: {
      type: Object,
      default: {}
    }
  },
  data() {
    return {
      term: null,
      terminalSocket: null
    };
  },
  methods: {
    runRealTerminal() {
      console.log("webSocket is finished");
    },
    errorRealTerminal() {
      console.log("error");
    },
    closeRealTerminal() {
      console.log("close");
    }
  },
  mounted() {
    let terminalContainer = document.getElementById("terminal");
    this.term = new Terminal({
      cols: 180
    });
    this.term.open(terminalContainer);
    let i = 0;
    this.term.write(`Log ...`);
    i++;
    // open websocket
    // this.terminalSocket = new WebSocket("ws://127.0.0.1:3000/terminals/");
    // this.terminalSocket.onopen = this.runRealTerminal;
    // this.terminalSocket.onclose = this.closeRealTerminal;
    // this.terminalSocket.onerror = this.errorRealTerminal;
    // this.term.attach(this.terminalSocket);
    // this.term._initialized = true;
    // console.log("mounted is going on");
  },
  beforeDestroy() {
    this.terminalSocket.close();
    this.term.destroy();
  }
};
</script>