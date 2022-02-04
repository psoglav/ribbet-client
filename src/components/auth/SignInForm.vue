<template>
  <div class="signin-form smooth-card">
    <div class="signin-form__title blurry-heading">!!! croak !!!</div>
    <div class="signin-form__form">
      <Input :name="t('form.email')" autofocus />
      <Input :name="t('form.password')" secure />
      <a class="forgot-password" href="#">Forgot password?</a>
    </div>
    <Button :value="t('auth.signin')" @click="signin" />
  </div>
</template>

<script>
import Input from "@/components/input/Input";
import Button from "@/components/button/Button";

import { useI18n } from "vue-i18n";

export default {
  components: {
    Input,
    Button,
  },
  setup() {
    const { t, locale } = useI18n();
    locale.value = "en";

    function signin(e) {
      e.wait(
        new Promise((resolve) => {
          setTimeout(resolve, 3000);
        })
      );
    }

    return {
      t,
      signin,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/scss/ui/elements.scss";
@import "@/scss/typography.scss";

.signin-form {
  gap: 20px;
  width: 20em;
  display: grid;
  overflow: hidden;
  position: relative;
  
  &__title {
    text-align: center;
    // text-indent: 1rem;
  }

  &__form {
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding: 5px 0;

    .forgot-password {
      text-align: left;
      text-indent: 12px;
      color: #121214;
      font-size: 12px;
      text-decoration: none;
      font-weight: 800;
      padding: 5px;
      border-radius: 15px;

      &:hover {
        background: rgb(245, 245, 245);
      }
    }
  }
}
</style>
