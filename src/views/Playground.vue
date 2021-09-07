<template>
  <div class="playground">
    <div class="container">
      <h2>Ribbet.</h2>
      <Input :name="t('form.email')" />
      <Input :name="t('form.password')" secure />
    </div>
  </div>
</template>

<script setup>
import Input from "@/components/input/Input";

import { useI18n } from "vue-i18n";

const { t, locale } = useI18n({
  useScope: "global",
});

locale.value = "en";

defineExpose({
  t,
});
</script>

<style lang="scss">
.playground {
  background: url("../assets/img/bg.svg");
  height: 100vh;
  display: grid;
  align-content: center;
  justify-items: start;
  padding: 150px;

  .container {
    gap: 25px;
    display: grid;
    padding: 30px;
    background-color: #fff;
    border: 2px rgb(241, 241, 241) solid;
    border-radius: 35px;
    padding-bottom: 40px;
  }

  h2 {
    font-family: Poppins;
    text-align: left;
    text-indent: 1rem;
    height: 40px;
    display: grid;
    align-content: end;
  }
}
</style>
