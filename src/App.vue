<template>
  <div>
    <div class="text" contenteditable>
      ⚠ Warning: There is a bear 🐻
    </div>
    <button @click="enterFullscreen">Fullscreen</button>
  </div>
</template>

<script>
export default {
  mounted() {
    window.addEventListener('dblclick', () => {
      this.enterFullscreen();
    });
  },
  methods: {
    enterFullscreen() {
      if (document.fullscreenElement) {
        if (screen.orientation.unlock) {
          screen.orientation.unlock();
        }
        document.exitFullscreen();
      } else {
        document.body.requestFullscreen();
        if (screen.orientation.lock) {
          screen.orientation.lock('landscape');
        }
      }
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
  display: block;
  position: absolute;
  left: 0;
  top: 0;
  transform: translateX(50vw) translateY(90vh);
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
