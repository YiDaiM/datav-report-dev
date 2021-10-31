<template>
  <div>
    <common-card title="累计订单量" value="2,157,420">
      <template>
          <div id="total-order-chart" style="width: 100%;height: 100%"></div>
      </template>
      <template slot="footer">
        <div>
          <span>昨日订单量</span>
          <span class="emphasis">2,000,000</span>
        </div>
      </template>
    </common-card>
  </div>
</template>

<script>

import commonCardMixins from "../../Mixins/commonCardMixins";

export default {
  name: "index",
  mixins: [commonCardMixins],
  mounted() {
    const chartDom = document.getElementById('total-order-chart')
    const chart = this.$echarts.init(chartDom)
    chart.setOption({
      xAxis: {
        type: 'category',
        //x轴不写data，那x轴就不会显示了
        show: false,
        boundaryGap: false//让图左右两边都伸展开,默认时，x轴坐标两边都有类似于padding的内边距
      },
      yAxis: {
        show: false//隐藏y轴
      },
      grid: {
        top: 0,
        left: 0,
        right: 0,
        bottom: 0
      },
      series: [{
        type: 'line',
        data: [620,432,220,534,790,430,220,320,532,320,834,690,530,220,620],
        areaStyle: {
          color: 'purple'//添加区域面积
        },
        lineStyle: {
          width: 0 // 让线条消失
        },
        itemStyle: {
          opacity: 0 // 让每个坐标点去掉，item就是坐标点
        },
        smooth: true  //让线条更加平滑
      }]
    })
  }
}
</script>

<style scoped lang="scss">
  #total-order-chart {
    width: 100%;
    height: 100%;
  }
</style>
