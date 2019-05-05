<template>
  <mx-section class="flex flex-col justify-center">
    <div class="flex flex-col">
      <h2 class="title-test">What I do</h2>
      <p class="mt-5">The big picture</p>
    </div>

    <div class="px-6 mt-10">
      <ol class="flex -mx-6">
        <li class="px-6 w-1/3" v-for="item in whatIDo" :key="item.title">
          <div class="item bg-white rounded overflow-hidden shadow-lg px-6 py-6">
            <div class="flex justify-center mb-6">
              <img class="illustration" :src="item.illustration" :alt="item.title">
            </div>
            <p class="text-xl mb-5 font-bold">{{ item.title }}</p>
            <p>{{ item.description }}</p>
          </div>
        </li>
      </ol>
    </div>
  </mx-section>
</template>

<script>
import MxSection from '../Section'

export default {
  components: {
    WhatIDoItem,
    MxSection
  },
  data: () => ({
    whatIDo: [
      {
        illustration: require('@/assets/undraw_brainstorming.svg'),
        title: 'Explore',
        description:
          'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cumque fugit voluptatibus, nostrum atque illo sapiente, adipisci aut, quibusdam deleniti similique ex ducimus libero id aperiam hic! Possimus, quam aperiam. Ipsam!'
      },
      {
        illustration: require('@/assets/undraw_building.svg'),
        title: 'Create',
        description:
          'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cumque fugit voluptatibus, nostrum atque illo sapiente, adipisci aut, quibusdam deleniti similique ex ducimus libero id aperiam hic! Possimus, quam aperiam. Ipsam!'
      },
      {
        illustration: require('@/assets/undraw_outer_space.svg'),
        title: 'Bring it to the world',
        description:
          'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cumque fugit voluptatibus, nostrum atque illo sapiente, adipisci aut, quibusdam deleniti similique ex ducimus libero id aperiam hic! Possimus, quam aperiam. Ipsam!'
      }
    ]
  })
}
</script>

<style lang="scss">
.illustration {
  height: 200px;
}

.title-test {
  position: relative;

  &::after {
    content: '';
    position: absolute;
    z-index: -1;
    left: -15px;
    bottom: -4px;
    height: 50%;
    width: 90%;
    background-color: #30e3ca;
    opacity: 0.5;
  }
}

ol {
  counter-reset: li;
  margin-left: 0;
  padding-left: 0;
}

ol > li {
  position: relative;
  list-style: none;
}

ol > li::before {
  content: counter(li);
  counter-increment: li;
  position: absolute;
  top: -10px;
  left: 0px;

  border-radius: 100%;
  width: 40px;
  height: 40px;
  line-height: 40px;
  text-align: center;
  color: #fff;
  background: #30e3ca;
}
</style>
