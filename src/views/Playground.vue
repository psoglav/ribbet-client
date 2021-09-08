<template>
  <div class="playground">
    <Input :name="t('form.email')" autofocus />
    <Input :name="t('form.password')" secure />
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
  gap: 25px;
  align-content: center;
  justify-items: center;
}
</style>
