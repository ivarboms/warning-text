<template>
  <div>
    <div class="text" contenteditable>
      enter text here
    </div>
    <button @click="enterFullscreen">Enter fullscreen</button>
  </div>
</template>

<script>
export default {
  mounted() {
    addEventListener('dblclick', () => {
      this.enterFullscreen();
    });
  },
  methods: {
    enterFullscreen() {
      document.body.requestFullscreen();
    },
  },
}
</script>

<style>
body, ::backdrop {
  margin: 0;
  background-color: #1d1e21;
}
.text {
  width: 100vw;
  height: 10vh;
  text-align: center;
  padding-bottom: 10px;
  outline: none !important;
  color: #bbb;
}
:fullscreen .text {
  --font-size: 10vh;
  font-size: 10vw;
  position: absolute;
  transform: translateY(var(--font-size));
}
:fullscreen button {
  display: none;
}
button {
  font-size: 20px;
  color: rgba(0, 214, 252, 0.5);
  background: none;
  border: solid 1px rgba(0, 214, 252, 0.5);
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  border: solid 1px rgba(0, 214, 252, 0.8);
  color: rgba(0, 214, 252, 0.8);
}
</style>
