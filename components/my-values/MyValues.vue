<template>
  <mx-section class="flex flex-col justify-center">
    <div class="l-container">
      <h1 class="h2 text-center">My values</h1>

      <div class="chart" id="chart">
        <div class="chart-legend chart-legend--left">
          <div class="chart-legend-title">
            <span>me</span>
          </div>
        </div>

        <div class="chart-legend chart-legend--right">
          <ul>
            <li class="chart-legend-item">Linus Torvlads</li>
            <li class="chart-legend-item">Very good</li>
            <li class="chart-legend-item">Good</li>
          </ul>
        </div>

        <div class="chart-items">
          <my-values-item
            v-for="item in items"
            :percentage="item.percentage"
            :title="item.title"
            :key="item.title"
          />
        </div>
      </div>
    </div>
  </mx-section>
</template>

<script>
import MyValuesItem from './MyValuesItem'
import MxSection from '~/components/Section'

export default {
  components: {
    MyValuesItem,
    MxSection
  },

  data: () => ({
    items: [
      {
        title: 'Leadership',
        percentage: '88'
      },
      {
        title: 'Kindly',
        percentage: 70
      },
      {
        title: 'Passionate',
        percentage: 80
      }
    ]
  })
}
</script>

<style lang="scss">
$line-color: theme('colors.gray.300');
$label-color: theme('colors.gray.600');
$blue: blue;

.chart {
  display: flex;
  justify-content: center;
  margin: 50px;
  position: relative;

  // Lignes horizontales
  &::before,
  &::after {
    content: '';
    position: absolute;
    height: 33.33%; // Il faut 3 "zones" 100/3
    // Une pour le before, une after et une entre 2
    width: 100%;
    border-top: 1px;
    border-bottom: 1px;
    border-left: 0;
    border-right: 0;
    border-style: dashed;
    border-color: $line-color;
  }

  &::after {
    bottom: 0;
  }
}

.chart-wrapper {
  display: flex;
}

.chart-legend {
  color: $label-color;
  ul {
    height: 100%;
  }

  li {
    height: 33.3333%;
    padding-top: 10px;
  }
}

.chart-items {
  display: flex;
  flex-basis: 60%;
}

// Placement des éléments du graph
.chart-legend--left {
  order: 1;
}

.chart-items {
  order: 2;
}

.chart-legend--right {
  order: 3;
}

.chart-item {
  position: relative;
  height: 300px;
  flex-basis: 100%;
  margin: 0 20px;
  display: flex;
  align-items: flex-end;
  justify-content: center;

  // Lignes verticales au milieux des batons
  &::before {
    content: '';
    position: absolute;
    z-index: 1; // Pour que la barre passe en dessous
    height: 100%;
    width: 1px;
    border: 1px dashed $line-color;
  }
}

.chart-item-baton {
  height: 80%;
  z-index: 2; // Pour que la barre passe en dessous

  background-color: $blue;
  background-image: linear-gradient(
    0deg,
    theme('colors.mxblue.300') 0%,
    theme('colors.mxblue.200') 100%
  );

  color: hsl(187, 58%, 95%);
  display: flex;
  flex-basis: 100%;
  align-items: center;
  justify-content: center;
  font-size: 1.3em;
}

.chart-item-text {
  transform: rotate(-90deg);
}

.chart-legend--left {
  display: flex;
}

// La barre du "moi"
.chart-legend-title {
  display: flex;
  border: 1px solid $label-color;
  border-right: none;
  justify-content: center;
  align-items: center;
  & span {
    text-transform: uppercase;
    font-size: 1.2em;
    display: inline-block;
    transform: rotate(-90deg);
  }
}
</style>
