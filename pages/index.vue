<template>
  <div>
    <div class="header-wrapper">
      <mx-header/>
      <hero/>
    </div>

    <what-i-do/>
    <experiences/>
  </div>
</template>

<script>
import MxHeader from '~/components/header/MxHeader.vue'
import Hero from '~/components/Hero.vue'
import HeroWaves from '~/components/HeroWaves.vue'
import WhatIDo from '~/components/WhatIDo/WhatIDo.vue'
import Experiences from '~/components/experiences/Experiences.vue'

export default {
  components: {
    MxHeader,
    Hero,
    WhatIDo,
    Experiences
  }
}
</script>

<style lang="scss">
.header-wrapper {
  color: theme('colors.white');
  background-image: linear-gradient(
    90deg,
    theme('colors.mxblue.300') 33%,
    theme('colors.mxblue.200') 100%
  );
}

a {
  text-decoration: none;
}

::selection {
  color: #fff;
  background: theme('colors.mxblue.300');
  text-shadow: none;
}

/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
</style>
