<template>
  <div class="input-container">
    <div class="input" :class="{ focused, empty: !value }" :placeholder="name">
      <input
        @focus="focused = true"
        @blur="focused = false"
        v-model="value"
        :autofocus="autofocus"
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
  autofocus: Boolean,
});

const focused = ref(false);
const value = ref("");

defineExpose({
  focused,
  value,
});
</script>

<style lang="scss" scoped>
@import "@/scss/colors.scss";

$H: 35px;

.input-container {
  width: calc(100% + 5px);
  height: auto;
  display: flex;
  align-items: center;
  justify-content: center;

  .input {
    width: 100%;
    height: $H;
    border-radius: 18px;
    background-color: $low-gray;
    overflow: hidden;
    position: relative;
    box-sizing: content-box;
    transition: height 0.2s ease, box-shadow 0.3s 0.1s ease,
      border-radius 0.3s 0.3s ease;
    border: 2px $lowest-gray solid;

    &:hover {
      border: 2px $mid-gray solid;
    }

    &.focused {
      background-color: #f9f9f9;
      box-shadow: 0 0 5px 8px $low-gray, 5px 5px 5px rgba(0, 0, 0, 0.24) inset;
      border: 2px $accent solid;
    }

    &:not(.empty) {
      height: 50px;

      &[placeholder]::after {
        font-size: 0.8rem;
        top: 15%;
        text-transform: uppercase;
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
      color: $highest-gray;
      text-indent: 1rem;
      top: 20%;
      position: absolute;
      font-size: large;
      width: 100%;
      height: 30%;
      font-weight: 700;
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
