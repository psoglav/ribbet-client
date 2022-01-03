<template>
  <div class="page">
    <div class="container">
      <Bubbles />
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

.page {
  background: url("../assets/img/bg.svg");
  height: 100vh;
  display: grid;
  place-content: center;
  box-sizing: content-box;
  overflow: hidden;
  filter: url("#bubbles");

  .container {
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 15px;

    .signin-form {
      transform: translateY(20px);
      animation: fade-in 500ms ease forwards;
    }
  }
}
</style>
