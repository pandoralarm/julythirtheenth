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
useHead({
  title: 'Wedding Invitation Berlin & Alan',
  meta: [
    { charset: 'utf-8' },
    { name: 'viewport', content: 'width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, shrink-to-fit=no' },
    { name: 'apple-mobile-web-app-capable', content: 'yes' },
    { name: 'csrf-token', content: '1mLgHcy8ZqdHwLO9YTBOghB7yvr690VmNirmSrRs' },

    { name: 'description', content: 'Wedding Invitation Berlin & Alan' },

    // Open Graph
    { property: 'og:site_name', content: 'Wedding Invitation Berlin & Alan' },
    { property: 'og:title', content: 'Wedding Invitation Berlin & Alan' },
    { property: 'og:description', content: 'Wedding Invitation Berlin & Alan' },
    { property: 'og:url', content: 'https://mengoendang.com/julythirteen' },
    { property: 'og:image', content: 'https://s3.ap-southeast-1.wasabisys.com/ajakan-user/photo/icon_wa/icon_wa_1821863_1750575720.jpg' },
    { property: 'og:image:width', content: '256' },
    { property: 'og:image:height', content: '256' },
    { property: 'og:image:type', content: 'image/jpeg' },
    { property: 'og:type', content: 'website' },
    { property: 'og:updated_time', content: '1750520440' },

    // Twitter
    { name: 'twitter:card', content: 'summary_large_image' },
    { name: 'twitter:description', content: 'Wedding Invitation Berlin & Alan' },
    { name: 'twitter:image', content: 'https://s3.ap-southeast-1.wasabisys.com/ajakan-user/photo/icon_wa/icon_wa_1821863_1750575720.jpg' }
  ]
})
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
      favicon.href = this.isValidGuest
        ? "/rings.png"
        : "/rings.png";
    } else {
      const link = document.createElement("link");
      link.rel = "icon";
      link.href = this.isValidGuest
        ? "/rings.png"
        : "/rings.png";
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
