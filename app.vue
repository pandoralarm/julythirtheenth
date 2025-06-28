<!-- app.vue -->
<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
<script setup>
useHead({
  titleTemplate: (title) =>
    title ? `${title} | Wedding Invitation` : "Wedding Invitation Berlin & Alan",
  meta: [
    { charset: "utf-8" },
    {
      name: "viewport",
      content:
        "width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, shrink-to-fit=no",
    },
    { name: "apple-mobile-web-app-capable", content: "yes" },
    { name: "description", content: "Wedding Invitation Berlin & Alan" },
    { name: "twitter:card", content: "summary_large_image" },
    { name: "twitter:description", content: "Wedding Invitation Berlin & Alan" },
    { name: "csrf-token", content: "1mLgHcy8ZqdHwLO9YTBOghB7yvr690VmNirmSrRs" },
    {
      name: "twitter:image",
      content:
        "https://s3.ap-southeast-1.wasabisys.com/ajakan-user/photo/icon_wa/icon_wa_1821863_1750575720.jpg",
    },
    { property: "og:site_name", content: "Wedding Invitation Berlin & Alan" },
    { property: "og:title", content: "Wedding Invitation Berlin & Alan" },
    { property: "og:description", content: "Wedding Invitation Berlin & Alan" },
    { property: "og:url", content: "https://julythirteen.com/" },
    { property: "og:type", content: "website" },
    {
      property: "og:image",
      content:
        "https://s3.ap-southeast-1.wasabisys.com/ajakan-user/photo/icon_wa/icon_wa_1821863_1750575720.jpg",
    },
    { property: "og:image:width", content: "256" },
    { property: "og:image:height", content: "256" },
    { property: "og:image:type", content: "image/jpeg" },
  ],
});
</script>
