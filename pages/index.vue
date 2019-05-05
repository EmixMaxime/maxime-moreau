<template>
  <div>
    <div class="header-wrapper">
      <mx-header/>
      <hero/>
    </div>

    <what-i-do/>
  </div>
</template>

<script>
import MxHeader from '~/components/header/MxHeader.vue'
import Hero from '~/components/Hero.vue'
import WhatIDo from '~/components/WhatIDo/WhatIDo.vue'

export default {
  components: {
    MxHeader,
    Hero,
    WhatIDo
  }
}
</script>

<style lang="scss">
$from: #11999e;
$to: #30e3ca;

.header-wrapper {
  color: config('colors.white');
  background-image: linear-gradient(90deg, $from 33%, $to 100%);
}

a {
  text-decoration: none;
}

::selection {
  color: #fff;
  background: $from;
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
