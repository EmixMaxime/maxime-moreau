<template>
  <div class="whatido">
    <mx-section class="flex flex-col justify-center">
      <div class="flex flex-col items-center">
        <h2 class="title-test">What I do</h2>
        <p class="mt-5">The big picture</p>
      </div>

      <ol class="flex flex-wrap -mx-6 mt-10" style="position: relative">
        <!-- <span class="dashing"></span> -->
        <li class="px-6 w-full lg:w-1/3" v-for="(item, index) in whatIDo" :key="item.title">
          <div
            class="bg-white h-full flex flex-col rounded shadow-lg px-6 py-6 pb-10"
            :class="cardClass(index)"
          >
            <div class="flex justify-center -mx-6 mb-6">
              <img class="illustration" :src="item.illustration" :alt="item.title">
            </div>
            <p class="card-title text-xl mb-6 font-bold">{{ item.title }}</p>
            <p class="mb-6">{{ item.description }}</p>

            <figure class="text-center mt-auto text-gray-700">
              <blockquote>“{{ item.citation.txt }}” — {{ item.citation.author }}</blockquote>
            </figure>
          </div>
        </li>
      </ol>
    </mx-section>
  </div>
</template>

<script>
import MxSection from '../Section'
import WhatIDo from './WhatIDo'

export default {
  components: {
    WhatIDo,
    MxSection
  },
  methods: {
    cardClass(index) {
      return `card-item card-item--${index}`
    }
  },
  data: () => ({
    whatIDo: [
      {
        illustration: require('@/assets/undraw_brainstorming.svg'),
        title: 'Explore',
        citation: {
          txt:
            'The sooner you start to code, the longer the program will take.',
          author: 'Roy Carlson'
        },
        description:
          'Lorem ipsum dolor sit amet, consectetur adipisicing elit. adipisicing elit. adipisicing elit. adipisicing elit. adipisicing elit. adipisicing elit. adipisicing elit. adipisicing elit. Cumque fugit voluptatibus, nostrum atque illo sapiente, adipisci aut, quibusdam deleniti similique ex ducimus libero id aperiam hic! Possimus, quam aperiam. Ipsam!'
      },
      {
        illustration: require('@/assets/undraw_building.svg'),
        title: 'Create',
        citation: {
          txt: 'Codes are a puzzle. A game, just like any other game.',
          author: 'Alan Turing'
        },
        description:
          'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cumque fugit voluptatibus, nostrum atque illo sapiente, adipisci aut, quibusdam deleniti similique ex ducimus libero id aperiam hic! Possimus, quam aperiam. Ipsam!'
      },
      {
        // illustration: require('@/assets/undraw_outer_space.svg'),
        illustration: require('@/assets/undraw_launching.svg'),
        title: 'Bring it to the world',
        citation: {
          txt: 'Codes are a puzzle. A game, just like any other game.',
          author: 'Alan Turing'
        },
        description:
          'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Cumque fugit voluptatibus, nostrum atque illo sapiente, adipisci aut, quibusdam deleniti similique ex ducimus libero id aperiam hic! Possimus, quam aperiam. Ipsam!'
      }
    ]
  })
}
</script>

<style lang="scss" scoped>
.whatido {
  background: url(~assets/formes.svg) no-repeat center;
  background-size: contain;
  background-attachment: fixed;
}

.card-item--0 {
  border-top-style: solid;
  border-top-color: theme('colors.orange.500');
  .card-title {
    color: theme('colors.orange');
  }
}

.card-item--1 {
  border-top-style: solid;
  border-top-color: theme('colors.purple.500');
  .card-title {
    color: theme('colors.purple');
  }
}

.card-item--2 {
  border-top-style: solid;
  border-top-color: theme('colors.blue.500');
  .card-title {
    color: theme('colors.blue');
  }
}

.card-item {
  .illustration {
    transition: fill 0.15s;
  }

  &:hover {
    .illustration {
      filter: grayscale(1);
    }
  }
}

.dashing {
  position: absolute;
  top: 50%;
  height: 5px;
  width: 50px;
  background-color: red;
  // margin-right: -1.5rem;
  // margin-left: -1.5rem;
  z-index: -1;
  animation: move 2s linear infinite;
}

@keyframes move {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(100%);
  }
}

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
    bottom: 1px;
    height: 20%;
    width: 90%;
    background-color: #30e3ca;
    opacity: 0.5;
  }
}

// ol {
//   counter-reset: li;
//   margin-left: 0;
//   padding-left: 0;
// }

// ol > li {
//   position: relative;
//   list-style: none;
// }

// ol > li::before {
//   content: counter(li);
//   counter-increment: li;
//   position: absolute;
//   top: -10px;
//   left: 0px;

//   border-radius: 100%;
//   width: 40px;
//   height: 40px;
//   line-height: 40px;
//   text-align: center;
//   color: #fff;
//   background: black;
// }
</style>
