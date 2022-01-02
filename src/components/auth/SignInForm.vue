<template>
  <div class="signin-form">
    <h2 class="signin-form__title">Ribbet.</h2>
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
    const { t, locale } = useI18n({locale: 'en'});
    locale.value = 'en'

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
.signin-form {
  box-shadow: 12px 12px 13px rgba(0, 0, 0, 0.075) inset;
  gap: 25px;
  display: grid;
  padding: 30px;
  background-color: rgb(255, 255, 255);
  border: 2px rgb(241, 241, 241) solid;
  border-radius: 35px;
  padding-bottom: 30px;
  overflow: hidden;
  position: relative;

  &__title {
    font-family: Poppins;
    text-align: left;
    text-indent: 1rem;
    height: 40px;
    display: grid;
    align-content: flex-end;
    // justify-self: center;
    display: flex;
    text-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  }

  &__form {
    display: flex;
    flex-direction: column;
    gap: 21px;
    padding: 5px 0;

    .forgot-password {
      text-align: left;
      text-indent: 12px;
      margin-top: -5px;
      color: black;
      font-size: 12px;
      text-decoration: none;
      font-weight: 800;
      padding: 3px;
      border-radius: 15px;

      &:hover {
        background: rgb(245, 245, 245);
      }
    }
  }
}
</style>
