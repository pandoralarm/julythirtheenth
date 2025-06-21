<template>
  <div class="window">
    <iframe
      id="invite-frame"
      src="https://mengoendang.com/testertester"
      frameborder="0"
      allowfullscreen
    ></iframe>
  </div>
</template>

<script>
export default {
  mounted() {
    // Optional: adjust iframe dynamically if needed
    const iframe = document.getElementById('invite-frame');
    const resize = () => {
      iframe.style.width = window.innerWidth + 'px';
      iframe.style.height = window.innerHeight + 'px';
    };
    resize();
    window.addEventListener('resize', resize);
  },
};
</script>

<style lang="scss">
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  overflow: hidden;
}

.window {
  width: 100vw;
  height: 100vh;
  overflow: hidden;

  iframe {
    width: 100%;
    height: 100%;
    border: none;
    display: block;
  }
}
</style>
