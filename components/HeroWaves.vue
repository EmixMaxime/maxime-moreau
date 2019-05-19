<template>
  <!-- Inspiration: https://codepen.io/candra-shalahuddin/pen/vQqzyB -->
  <svg
    class="editorial"
    xmlns="http://www.w3.org/2000/svg"
    xmlns:xlink="http://www.w3.org/1999/xlink"
    viewBox="0 24 150 28 "
    preserveAspectRatio="none"
  >
    <defs>
      <path
        id="gentle-wave"
        d="M-160 44c30 0
    58-18 88-18s
    58 18 88 18
    58-18 88-18
    58 18 88 18
    v44h-352z"
      ></path>
    </defs>
    <g class="parallax2">
      <use xlink:href="#gentle-wave" x="50" y="0"></use>
    </g>
    <g class="parallax4">
      <use xlink:href="#gentle-wave" x="50" y="6"></use>
    </g>
  </svg>
</template>

<style lang="scss" scoped>
svg.editorial {
  display: block;
  width: 100%;
  height: 60px;
  max-height: 60px;
  margin: 0;
  z-index: 5;
}

.parallax2 > use {
  fill: theme('colors.gray.200');

  animation: move-forever2 8s linear infinite;
  &:nth-child(1) {
    animation-delay: -2s;
  }
}

.parallax4 > use {
  fill: theme('colors.white');

  animation: move-forever4 4s linear infinite;
  &:nth-child(1) {
    animation-delay: -2s;
  }
}

@keyframes move-forever2 {
  0% {
    transform: translate(-90px, 0%);
  }
  100% {
    transform: translate(85px, 0%);
  }
}

@keyframes move-forever4 {
  0% {
    transform: translate(-90px, 0%);
  }
  100% {
    transform: translate(85px, 0%);
  }
}
</style>

