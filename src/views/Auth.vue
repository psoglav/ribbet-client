<template>
  <div class="page">
    <SignInForm />
  </div>
</template>

<script>
import SignInForm from "@/components/auth/SignInForm.vue";

export default {
  components: {
    SignInForm,
  },

  setup() {},
};
</script>

<style lang="scss" scoped>
.page {
  background: url("../assets/img/bg.svg");
  height: 100vh;
  display: grid;
  align-content: center;
  justify-items: start;
  padding: 20px 150px;
  gap: 10px;
  box-sizing: content-box;
}
</style>
