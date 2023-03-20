<template>
    <div class="status-bar-item clfix">
      <div class="status-bar-item-name">{{ name }}</div>
      <div class="status-bar-item-ability">
        <div :class="'percent percent-' + percent + ' percent-color-' + color">
          <span class="status-bar-item-percent">{{ percent }}%</span>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'StatusBarItem',
  props: {
    name: String,
    percent: Number,
    color: Number
  }
}
</script>
