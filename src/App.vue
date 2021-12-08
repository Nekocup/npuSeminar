<template>
  <div id="app">
    <Header />
    <MainContain />
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/header.vue";
import MainContain from "@/components/mainContain.vue";
import Footer from "@/components/footer.vue";
export default {
  name: "App",
  components: {
    Header: Header,
    MainContain: MainContain,
    Footer: Footer,
  },
};
</script>

<style lang="scss">
@import "@/assets/css/all.scss";
</style>
