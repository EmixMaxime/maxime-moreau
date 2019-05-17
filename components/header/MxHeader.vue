<template>
  <header>
    <header class="topbar container mx-auto" id="topbar">
      <nav class="flex items-center justify-between flex-wrap pt-10" role="navigation">
        <ul class="list-reset w-full block flex-grow lg:flex lg:items-center lg:w-auto">
          <li>
            <a class="text-white pr-8 font-bold text-lg">Maxime Moreau</a>
          </li>
          <li v-for="item in links" :key="item.link">
            <a
              :href="item.link"
              class="block mt-4 lg:inline-block lg:mt-0 text-teal-200 hover:text-white mr-4"
            >{{ item.txt }}</a>
          </li>
        </ul>
      </nav>
    </header>
  </header>
</template>

<script>
export default {
  data: () => ({
    links: [
      { link: '#home', txt: 'Home' },
      { link: '#presentation', txt: 'Presentation' },
      { link: '#skills', txt: 'Skills' },
      { link: '#creations', txt: 'Creations' },
      { link: '#education', txt: 'Education' }
    ]
  })
}
</script>

<style>
</style>
