<template>
  <div @click="handleClick" class="button" :class="{ loading }">
    {{ value }}
    <span class="button__loading-dots" :class="{ loading }">
      <span></span>
      <span></span>
      <span></span>
    </span>
  </div>
</template>

<script setup>
import { ref } from "vue";

defineProps({
  value: String,
});

const loading = ref(false);

const emit = defineEmits(["click"]);

function handleClick() {
  emit("click", {
    async wait(promise) {
      loading.value = true;
      promise.then(() => {
        loading.value = false;
      });
    },
  });
}

defineExpose({
  loading,
});
</script>

<style lang="scss">
.button {
  width: min-content;
  padding: 0 33px;
  white-space: nowrap;
  height: 35px;
  color: white;
  font-family: Nunito;
  font-weight: 700;
  letter-spacing: 0.05rem;
  background: #000;
  display: flex;
  align-items: center;
  font-size: 1.1rem;
  border-radius: 25px;
  position: relative;
  overflow: hidden;
  cursor: pointer;
  user-select: none;
  transition: box-shadow 1s ease;
  gap: 2px;
  // box-shadow: 0 0 0px calc(100vw / 2) black;
  transition: max-width 0.5s ease;

  &:active,
  &:hover {
    &::before,
    &::after {
      opacity: 0.5;
      transition: none;
    }
  }

  &:active {
    color: black;
    background: rgb(128, 128, 128);
  }

  &.loading {
    box-shadow: 0 0 15px black;
    filter: blur(0px);
    transition: box-shadow 1s ease;
    &::before,
    &::after {
      transition: opacity 0.4s ease;
      opacity: 0;
    }
  }

  &.loading {
    background-color: #000;
    color: white;
    cursor: progress;
  }

  &::before,
  &::after {
    opacity: 0;
    transition: opacity 0.05s ease, transform 0.2s ease;
    position: absolute;
    content: "";
    border-radius: 40px;
  }

  &::after {
    top: -30px;
    height: 50%;
    left: -10%;
    filter: blur(3px);
    width: calc(120% - 60px);
    border: 30px white solid;
  }

  &::before {
    top: 3px;
    height: 70%;
    left: 0;
    filter: blur(1px);
    width: calc(100% - 10px);
    border: 5px white solid;
  }
}
</style>
