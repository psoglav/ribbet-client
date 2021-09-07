<template>
  <div class="input-container">
    <div class="input" :class="{ focused, empty: !value }" :placeholder="name">
      <input
        @focus="focused = true"
        @blur="focused = false"
        v-model="value"
        spellcheck="false"
        :type="secure ? 'password' : 'text'"
        :class="{ secure }"
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  name: String,
  secure: Boolean,
});

const focused = ref(false);
const value = ref("");

defineExpose({
  focused,
  value,
});
</script>

<style lang="scss" scoped>
$W: 250px;
$H: 35px;
$accent: #b1acff;

.input-container {
  width: $W + 5px;
  height: $H + 5px;
  display: flex;
  align-items: center;
  justify-content: center;

  .input {
    width: $W;
    height: $H;
    border-radius: 18px;
    background-color: #efefef;
    overflow: hidden;
    position: relative;
    box-sizing: content-box;
    transition: height 0.2s ease, box-shadow 0.3s 0.1s ease;

    &.focused {
      border-radius: 25px;
      background-color: #f9f9f9;
      box-shadow: 0 0 5px 8px #efefef, 5px 5px 5px rgba(0, 0, 0, 0.24) inset;
      border: 2px $accent solid;
    }

    &:not(.empty) {
      height: 50px;

      &[placeholder]::after {
        transform: scale(0.7) translateX($W - 280px); // TODO needs to be recalculated
        top: 10%;
      }

      input {
        filter: none;
        top: 33%;
        height: $H;

        &.secure {
          filter: blur(3px);
          letter-spacing: 0.1rem;
        }
      }
    }

    &[placeholder]::after {
      content: attr(placeholder);
      text-align: left;
      pointer-events: none;
      transition: transform 0.1s ease;
      transform: translateX(18px);
      color: #b8b8b8;
      top: 20%;
      left: 0;
      position: absolute;
      font-size: large;
      width: 100%;
      height: 30%;
      filter: none;
      font-weight: 700;
      border: none;
    }

    input {
      position: absolute;
      top: 0;
      left: 0;
      font-family: Glory, sans-serif;
      font-size: 20px;
      text-indent: 1rem;
      padding-right: 0.5rem;
      font-weight: 600;
      background: 0;
      width: 100%;
      height: 100%;
      border: 0;

      &::selection {
        background-color: transparentize(#8e9bc7, 0.6);
      }

      &:focus {
        &::selection {
          background-color: transparentize($accent, 0.3);
        }
        outline: 0;
      }
    }
  }
}
</style>
