<template>
  <div class="bubbles">
    <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
      <defs>
        <filter id="bubbles">
          <feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" />
          <feColorMatrix
            in="blur"
            mode="matrix"
            :values="`1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 ${blur} -10`"
            result="bubbles"
          />
          <feBlend in="SourceGraphic" in2="bubbles" operator="atop" />
        </filter>
      </defs>
    </svg>
    <div class="circle bubble-1"></div>
    <div class="circle bubble-2"></div>
    <div class="circle bubble-3"></div>
    <div class="circle bubble-4"></div>
    <div class="circle bubble-5"></div>
  </div>
</template>

<script>
export default {
  props: {
    blur: {
      default: () => 1555,
      type: Number,
    },
  },
};
</script>

<style lang="scss">
@keyframes bubble-up {
  to {
    transform: translateY(-50vh);
    opacity: 1;
  }
}

.bubbles {
  position: absolute;
}

.circle {
  border-radius: 100%;
  background-color: #eee;
  height: 50px;
  width: 50px;
  top: 20px;
  position: absolute;
  opacity: 0;
}

.bubble-1 {
  animation: bubble-up 1.3s ease-in forwards infinite;
  left: 10%;
}
.bubble-2 {
  animation: bubble-up 800ms 2s ease-in forwards infinite;
  left: 30%;
  width: 25px;
  height: 25px;
}
.bubble-3 {
  animation: bubble-up 2.3s 1s ease-in forwards infinite;
  left: 50%;
  width: 65px;
  height: 65px;
  top: 50px;
}
.bubble-4 {
  animation: bubble-up 1s ease-in forwards infinite;
  left: 60%;
  width: 15px;
  height: 15px;
}
.bubble-5 {
  animation: bubble-up 1.7s ease-in forwards infinite;
  left: 70%;
  width: 35px;
  height: 35px;
  top: 30px;
}
</style>
