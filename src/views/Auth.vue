<template>
  <img :src="require('@/assets/LOGO.svg')" class="logo" />
  <div class="page">
    <div class="container">
      <Bubbles />
      <!-- <Bubbles blur="70" /> -->
      <SignInForm />
    </div>
  </div>
</template>

<script>
import SignInForm from "@/components/auth/SignInForm.vue";
import Bubbles from "@/components/auth/Bubbles.vue";

export default {
  components: {
    SignInForm,
    Bubbles,
  },
  setup() {},
};
</script>

<style lang="scss" scoped>
@import "@/scss/ui/elements.scss";
@import "@/scss/typography.scss";
@import "@/scss/anime.scss";

@keyframes fade-in {
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
    filter: none;
  }
}

svg {
  height: 0px;
  width: 0px;
}

.logo {
  position: absolute;
  z-index: 10;
  top: 100px;
  left: 50%;
  width: 230px;
  height: 230px;
  transform: translateX(-50%);
}

.page {
  height: 100vh;
  display: grid;
  place-content: center;
  box-sizing: content-box;
  overflow: hidden;
  background: url("../assets/img/bg.svg");
  filter: url("#bubbles");

  .container {
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 15px;

    .signin-form {
      transform: translateY(20px);
      opacity: 0;
      animation: fade-in 2500ms ease forwards;
    }
  }
}
</style>
