<template>
  <div class="section-bg">
    <mx-section class="flex flex-col justify-center">
      <div class="flex flex-col mb-10">
        <h2 class="text-white">Experiences</h2>
        <p class="text-white mt-4">With who I've been working</p>
      </div>

      <div class>
        <ol class="flex flex-wrap -mx-6">
          <li class="px-6 w-full lg:w-1/2" v-for="item in experiences" :key="item.company">
            <div
              class="card-item bg-white rounded overflow-hidden shadow-lg px-6 py-6 flex flex-col"
            >
              <div class="flex">
                <div class="pr-5">
                  <img class="illustration" :src="item.logo" :alt="item.company">
                </div>
                <div class="content">
                  <div class="flex justify-between">
                    <p class="text-xl mb-5 font-bold flex items-center">
                      <span v-if="item.currently" class="bg-green currently mr-2"></span>
                      {{ item.company }}
                    </p>
                    <p>{{ item.duration }}</p>
                  </div>

                  <div class="flex justify-between pb-6">
                    <p>{{ item.jobTitle }}</p>
                    <span
                      v-if="item.apprentice"
                      class="text-sm bg-grey-lighter rounded-lg py-1 px-2"
                    >Apprentice</span>
                  </div>

                  <p>{{ item.description }}</p>
                </div>
              </div>

              <div class="self-end -my-6 -mx-6 pt-6" :class="cornerClass(item)">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                  <path
                    d="M16.172 9l-6.071-6.071 1.414-1.414L20 10l-.707.707-7.778 7.778-1.414-1.414L16.172 11H0V9z"
                  ></path>
                </svg>
              </div>
            </div>
          </li>
        </ol>
      </div>
    </mx-section>
  </div>
</template>

<script>
import MxSection from '../Section'

export default {
  components: {
    MxSection
  },
  methods: {
    cornerClass(item) {
      return `corner corner--${item.company.toLowerCase()}`
    }
  },
  data: () => ({
    experiences: [
      {
        company: 'Airbus',
        logo: require('@/assets/logos/a-airbus.svg'),
        description:
          'Leading aircraft manufacturer have propelled it to the forefront of the aviation and air transport industries.',
        jobTitle: 'Software engineer',
        technologies: ['python', 'pyspark', 'pandas', 'javascript', 'ui/ux'],
        apprentice: true,
        duration: 'Oct 2018 - currently',
        currently: true
      },
      {
        company: 'Viously',
        logo: require('@/assets/logos/viously.svg'),
        description:
          'Video technologies for media, influencers and online merchants to significantly develop their business.',
        jobTitle: 'Web developer',
        technologies: ['nginx', 'javascript', 'nodejs', 'ui/ux'],
        apprentice: true,
        duration: '2017 - 2018'
      }
    ]
  })
}
</script>

<style lang="scss">
.section-bg {
  background-color: hsl(202, 99%, 14%);
}

.card-item {
  transition: color 0.1s ease;
  transition-duration: 0.15s;
  transition-property: color, background-color, box-shadow, transform;
  cursor: pointer;
}

.card-item:hover {
  transform: translateY(-2px);

  .corner > svg {
    transform: translateX(5px);
  }
}

.corner {
  position: relative;
  border-color: transparent transparent config('colors.grey-lighter');

  border-style: solid;
  width: 0;
  height: 0;
  transition: opacity 0.3s ease-in-out;

  border-width: 0 0 60px 60px;

  > svg {
    width: 17px;
    height: 17px;
    fill: config('colors.grey-dark');
    position: absolute;
    left: -30px;
    top: 60px;
    transform: translateX(0);
    transition: transform 0.2s ease-in-out;
  }
}

$airbusColor: hsl(219, 100%, 18%);
.corner--airbus {
  border-color: transparent transparent hsl(219, 50%, 90%);

  > svg {
    fill: hsl(219, 50%, 60%);
  }
}

$viouslyColor: hsl(184, 100%, 34%);
.corner--viously {
  border-color: transparent transparent hsl(184, 50%, 90%);

  > svg {
    fill: hsl(184, 50%, 60%);
  }
}

.currently {
  height: 0.6em;
  width: 0.6em;
  border-radius: 100%;
}

ol {
  margin-left: 0;
  padding-left: 0;
}

li {
  position: relative;
  list-style: none;
}
</style>
