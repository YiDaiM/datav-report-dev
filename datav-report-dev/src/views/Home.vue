<template>
  <div class="home">
    <top-view />
    <sale-view />
    <bottom-view />
    <map-view />
  </div>
</template>

<script>
import TopView from '../components/TopView/index'
import SaleView from '../components/SaleView/index'
import MapView from '../components/MapView/index'
import BottomView from '../components/BottomView/index'
export default {
  name: 'Home',
  components: {
    TopView,
    SaleView,
    MapView,
    BottomView
  }
}
</script>
<style>
  .home {
    width: 100%;
    height: 100%;
    padding: 20px;
    background: #eee;
    box-sizing: border-box;
  }
</style>
