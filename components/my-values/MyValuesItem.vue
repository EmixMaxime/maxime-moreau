<template>
  <div class="chart-item">
    <div class="chart-item-baton">
      <span class="chart-item-text">{{ title }}</span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: { type: String, required: true },
    percentage: { type: Number, required: true }
  }
}
</script>

