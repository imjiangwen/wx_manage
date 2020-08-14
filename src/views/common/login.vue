<template>
  <div class="login-main" style="text-align:center;margin-top:15%;">
    <h3 class="login-title">授权登陆中...</h3>
  </div>
</template>

<script>
export default {
  mounted() {
    this.$router.replace({ name: "home" });
  },
};
</script>