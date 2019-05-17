<template>
  <div class="flex justify-center items-center mb-10">
    <div
      v-for="tech in technologies"
      class="bubble mr-10 flex items-center justify-center"
      :class="{ big: tech.big, small: tech.small }"
      :key="tech.title"
    >
      <img :src="tech.img">
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    technologies: [
      {
        img: require('@/assets/icons/nodejs.svg'),
        title: 'NodeJS',
        big: true
      },
      {
        img: require('@/assets/icons/docker-original.svg'),
        title: 'Docker',
        small: true
      },
      {
        img: require('@/assets/icons/vuejs-original.svg'),
        title: 'VueJS',
        big: true
      },
      {
        img: require('@/assets/icons/python-plain.svg'),
        title: 'Python',
        small: true
      },
      {
        img: require('@/assets/icons/nginx-original.svg'),
        title: 'Nginx',
        big: true
      }
    ]
  })
}
</script>

<style lang="scss" scoped>
$bubbleSize: 65px;

.big.bubble {
  width: $bubbleSize * 1.2;
  height: $bubbleSize * 1.2;
}

.small.bubble {
  width: $bubbleSize * 0.8;
  height: $bubbleSize * 0.8;
}

.bubble {
  background-color: hsl(172, 17%, 98%);
  border-radius: 100%;
  width: $bubbleSize;
  height: $bubbleSize;

  // mine
  // box-shadow: rgba(0, 0, 0, 0.1) 1px 3px 10px;

  // Inspired from Stripe
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1), 1px 3px 10px rgba(0, 0, 0, 0.07);

  > img {
    height: $bubbleSize * 0.65;
  }

  // animation-name: bubbling;
  // animation-delay: 0;
  // animation-iteration-count: infinite;

  // animation: bubbling 20s both infinite;
}

@function fact($number) {
  $value: 1;
  @if $number > 0 {
    @for $i from 1 through $number {
      $value: $value * $i;
    }
  }
  @return $value;
}

@function pow($number, $exp) {
  $value: 1;
  @if $exp > 0 {
    @for $i from 1 through $exp {
      $value: $value * $number;
    }
  } @else if $exp < 0 {
    @for $i from 1 through -$exp {
      $value: $value / $number;
    }
  }
  @return $value;
}

@function pi() {
  @return 3.14159265359;
}

@function rad($angle) {
  $unit: unit($angle);
  $unitless: $angle / ($angle * 0 + 1);
  // If the angle has 'deg' as unit, convert to radians.
  @if $unit == deg {
    $unitless: $unitless / 180 * pi();
  }
  @return $unitless;
}

@function sin($angle) {
  $sin: 0;
  $angle: rad($angle);
  // Iterate a bunch of times.
  @for $i from 0 through 10 {
    $sin: $sin + pow(-1, $i) * pow($angle, (2 * $i + 1)) / fact(2 * $i + 1);
  }
  @return $sin;
}

@function cos($angle) {
  $cos: 0;
  $angle: rad($angle);
  // Iterate a bunch of times.
  @for $i from 0 through 10 {
    $cos: $cos + pow(-1, $i) * pow($angle, 2 * $i) / fact(2 * $i);
  }
  @return $cos;
}

@function tan($angle) {
  @return sin($angle) / cos($angle);
}

$radius: 40px;

$nbSteps: 8;

@keyframes bubbling {
  0% {
    transform: translate3D(0px, 0px, 0px);
  }

  #{100/$nbSteps *1%} {
    transform: translate3D(
      (cos(pi() / 4)) * $radius,
      sin(pi() / 4) * $radius,
      0
    );
  }

  #{100/$nbSteps * 2%} {
    transform: translate3D(cos(pi() / 2) * $radius, sin(pi() / 2) * $radius, 0);
  }

  #{100/$nbSteps *3%} {
    transform: translate3D(
      -(cos(pi() / 4)) * $radius,
      sin(pi() / 4) * $radius,
      0
    );
  }

  #{100/$nbSteps *4%} {
    transform: translate3D(-$radius, 0, 0);
  }

  #{100/$nbSteps *5%} {
    transform: translate3D(
      -(cos(pi() / 4)) * $radius,
      -(sin(pi() / 4)) * $radius,
      0
    );
  }

  #{100/$nbSteps *6%} {
    transform: translate3D(-(cos(pi() / 2)), -(sin(pi() / 2)) * $radius, 0);
  }

  #{100/$nbSteps *7%} {
    transform: translate3D(
      cos(pi() / 4) * $radius,
      -(sin(pi() / 4)) * $radius,
      0
    );
  }

  100% {
    transform: translate3D(0px, 0px, 0px);
  }
}
</style>
