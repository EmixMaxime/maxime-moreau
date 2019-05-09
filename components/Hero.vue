<template>
  <section class="hero flex">
    <div class="container mx-auto flex items-center">
      <div class="flex flex-wrap -mx-6">
        <div class="w-full lg:w-1/2 px-6">
          <!-- <p class="mb-6 text-xl font-bold" id="test">Explorer. Créer. Ensemble.</p> -->
          <p class="mb-6 text-xl font-bold" id="test">Explore. Create. Together.</p>
          <h1 class="mb-6">Concepteur de solution numériques</h1>
          <p>Développement de solutions pour répondre aux besoins émergents des entreprises.</p>
        </div>
        <div class="w-full lg:w-1/2 px-6 w-1/2 flex flex-col items-center">
          <tech-bubble/>
          <img src="~assets/undraw_hello.svg" alt="illustration">
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
// $from: hsl(187, 59%, 27%);
// $to: #4acfc8;

.hero {
  min-height: 700px;
  /**
  * Adding a subtle shadow to white text when on a bright background
  * not only makes it more legible but helps it * 'pop' more
  * Thanks: @steveschoger (tweet: https://twitter.com/steveschoger/status/880449411150753792)
  */
  text-shadow: 0px 1px 2px rgba(0, 0, 0, 0.2);
  color: hsl(172, 17%, 97%);
  // color: #fff;
}

#test {
  transform: translateY(0);
  transition: transform 0.3s cubic-bezier(0.2, 0, 0.2, 1);
}
</style>

<script>
import TechBubble from '~/components/header/TechBubble.vue'

export default {
  components: {
    TechBubble
  }
}
</script>

