<template>
  <div class="window">
    <template v-if="isValidGuest">
      <iframe
        id="invite-frame"
        :src="iframeSrc"
        frameborder="0"
        allowfullscreen
      ></iframe>
    </template>
    <template v-else>
      <div class="unauthorized">
        <h1>🚫 Invitation Not Found</h1>
        <p>
          The name <strong>{{ honors }}</strong> is not on the guest list.
        </p>
      </div>
    </template>
  </div>
</template>
<script setup>
const route = useRoute();
const guest = route.query.honors ?? "Guest";

useHead({
  title: `Invitation for ${guest}`,
});
</script>


<script>
export default {
  data() {
    return {
      honors: "",
      iframeSrc: "",
      isValidGuest: false,
      allowedGuests: [
        "Alan Raihan",
        "Siti Nurhaliza",
        "John Smith",
        "Jane Doe",
        "Pak Budi",
        "Bu Ani",
        // Add more...
      ],
    };
  },
  mounted() {
    const params = new URLSearchParams(window.location.search);
    this.honors = params.get("honors") || "";

    const isListed = this.allowedGuests.some(
      (name) => name.toLowerCase() === this.honors.toLowerCase()
    );
    // isListed
    if (true) {
      this.isValidGuest = true;
      this.iframeSrc = `https://mengoendang.com/julythirteen?to=${encodeURIComponent(this.honors)}`;
    } else {
      this.isValidGuest = false;
    }

    document.title = this.isValidGuest
      ? `Invitation for ${this.honors}`
      : "Unauthorized Guest";

    const favicon = document.querySelector("link[rel~='icon']");
    if (favicon) {
      favicon.href = this.isValidGuest ? "/rings.png" : "/rings.png";
    } else {
      const link = document.createElement("link");
      link.rel = "icon";
      link.href = this.isValidGuest ? "/rings.png" : "/rings.png";
      document.head.appendChild(link);
    }

    // Optional: Responsive iframe logic
    const iframe = document.getElementById("invite-frame");
    if (iframe) {
      const resize = () => {
        iframe.style.width = window.innerWidth + "px";
        iframe.style.height = window.innerHeight + "px";
      };
      resize();
      window.addEventListener("resize", resize);
    }
  },
};
</script>

<style lang="scss">
html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
  overflow: hidden;
  font-family: sans-serif;
}

.window {
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  background: #000;

  iframe {
    width: 100%;
    height: 100%;
    border: none;
    display: block;
  }

  .unauthorized {
    width: 100%;
    height: 100%;
    display: grid;
    place-content: center;
    text-align: center;
    background: #f8d7da;
    color: #721c24;
  }
}

// When in landscape, lock iframe in a centered portrait container
@media (orientation: landscape) {
  .window {
    display: flex;
    justify-content: center;
    align-items: center;

    iframe {
      width: 375px; // iPhone X width
      height: 667px; // iPhone X height
      border: 1px solid #ccc;
      border-radius: 16px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
    }
  }

  .window .unauthorized {
    width: 375px;
    height: 667px;
    border-radius: 16px;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
  }
}
</style>
