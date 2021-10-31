<template>
  <div class="common-card">
    <div class="title">{{title}}</div>
    <div class="value">{{value}}</div>
    <div class="chart">
      <slot></slot>
    </div>
    <div class="line"></div>
    <div class="total">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "index",
  props: {
    title: String,
    value: String
  }
}
</script>

<style scoped lang="scss">
  .title {
    font-size: 12px;
    color: #999;
  }
  .value {
    margin-top: 5px;
    font-size: 25px;
    color: #000;
    letter-spacing: 1px;
  }
  .chart {
    height: 50px;
  }
  .line {
    margin: 10px 0;
    border-top: 1px solid #eee;
  }
  .total {
    font-size: 12px;
    color: #666;
  }
</style>
<style lang="scss">
.emphasis {
  margin-left: 5px;
  color: #333;
  font-weight: 700
}
.increase {
  width: 0;
  height: 0;
  margin: 0 0 3px 5px;
  border: 4px solid transparent;
  border-bottom-color: red;
}
.decrease {
  width: 0;
  height: 0;
  margin: 3px 0 0 5px;
  border: 4px solid transparent;
  border-top-color: green;
}
</style>
