<template>
  <div>
    <div class="header">
      <img
        src="@/assets/image/logo.png"
        alt="logo"
        id="logo"
        @click="goHome()"
      />
      <div class="logoTitle" @click="goHome()">
        <p>第二十屆離島資訊</p>
        <p>技術與應用研討會</p>
      </div>
      <a href="https://itaoi2022.npu.edu.tw/index.html">回首頁</a>
    </div>
  </div>
</template>
<script>
export default {
  methods: {
    goHome() {
      location.href = "https://itaoi2022.npu.edu.tw/index.html";
    },
  },
};
</script>
<style lang="scss"></style>
