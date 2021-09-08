<template>
  <div class="playground">
    <div class="container">
      <h2>Ribbet.</h2>
      <Input :name="t('form.email')" autofocus />
      <Input :name="t('form.password')" secure />
      <Button :value="t('auth.signin')" @click="signin" />
    </div>
  </div>
</template>

<script setup>
import Input from "@/components/input/Input";
import Button from "@/components/button/Button";

import { useI18n } from "vue-i18n";

const { t, locale } = useI18n({
  useScope: "global",
});

locale.value = "en";

function signin(e) {
  e.wait(
    new Promise((resolve) => {
      setTimeout(resolve, 3000);
    })
  );
}

defineExpose({
  t,
});
</script>

<style lang="scss" scoped>
.playground {
  background: url("../assets/img/bg.svg");
  height: 100vh;
  display: grid;
  align-content: center;
  justify-items: start;
  padding: 150px;

  .container {
    box-shadow: 12px 12px 13px rgba(0, 0, 0, 0.075) inset;
    gap: 25px;
    display: grid;
    padding: 30px;
    background-color: rgb(255, 255, 255);
    border: 2px rgb(241, 241, 241) solid;
    border-radius: 35px;
    padding-bottom: 40px;
    overflow: hidden;
  }

  h2 {
    font-family: Poppins;
    text-align: left;
    text-indent: 1rem;
    height: 40px;
    display: grid;
    align-content: end;
    display: flex;
    text-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  }
}
</style>
