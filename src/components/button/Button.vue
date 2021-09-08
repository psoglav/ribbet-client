<template>
  <div class="button">{{ value }}</div>
</template>

<script setup>
defineProps({
  value: String,
});
</script>

<style lang="scss">
.button {
  width: 130px;
  height: 35px;
  color: white;
  font-family: Nunito;
  font-weight: 700;
  letter-spacing: 0.05rem;
  background-color: #000;
  display: grid;
  align-content: center;
  font-size: 1.1rem;
  border-radius: 25px;
  position: relative;
  overflow: hidden;
  cursor: pointer;
  filter: blur(0.7px);
  user-select: none;
  transition: box-shadow 1s ease;

  &:hover {
    filter: blur(0px);
    &::before,
    &::after {
      transition: none;
      opacity: 0.5;
    }
  }

  &:active {
    box-shadow: 0 0 15px black;
    filter: blur(0px);
    transition: none;
    &::before,
    &::after {
      transition: opacity 0.4s ease !important;
      opacity: 0;
    }
  }

  &::before,
  &::after {
    transition: opacity 0.05s ease, transform 0.2s ease;
    position: absolute;
    content: "";
    border-radius: 40px;
    opacity: 0.3;
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
