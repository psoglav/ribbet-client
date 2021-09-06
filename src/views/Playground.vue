<template>
  <div class="playground">
    <Input placeholder="Email" />
    <Input placeholder="Password" secure />
  </div>
</template>

<script setup>
import Input from "@/components/input/Input";
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
