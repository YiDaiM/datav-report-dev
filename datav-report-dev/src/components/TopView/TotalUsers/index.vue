<template>
  <div>
    <common-card title="累计用户数" value="1,087,503">
      <template>
        <div id="total-users-chart" style="height: 100%;width: 100%" />
      </template>
      <template slot="footer">
        <div class="total-user-footer">
          <span>日同比</span>
          <span class="emphasis">8.73%</span>
          <div class="increase"></div>
          <span class="month">月同比</span>
          <span class="emphasis">35.91%</span>
          <div class="decrease"></div>
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
    const chartDom = document.getElementById('total-users-chart')
    const chart = this.$echarts.init(chartDom)
    chart.setOption({
      xAxis: {
        splitLine: false
      },
      yAxis: {
        type: 'category',
        splitLine: false,
        show: false
      },
      grid: {
        top: 0,
        left: 0,
        right: 0,
        bottom: 0
      },
      series: [
        {
          type: 'bar',
          data: [200],
          barWidth: 10,
          color: '#45c946',
          stack: '总量'
        },{
          type: 'bar',
          data: [250],
          barWidth: 10,
          color: '#eee',
          stack: '总量'
        },{
          type: 'custom',
          stack: '总量',
          data: [200],
          renderItem: (param, api) => {
            const value = api.value(0)// 这会获取到data元素里的第一个值，也就是两百
            console.log(value)
            const endPoint = api.coord([value, 0])//这会帮我们计算value的坐标系是多少
            console.log(endPoint)
            return {
              type: 'group',
              position: endPoint,//要绘制在哪个位置
              children: [
                {
                  type: 'path',//显示为线段
                  shape: {
                    d: 'M957.056 338.624C951.84 327.296 940.512 320 928 320L96 320c-12.512 0-23.84 7.296-29.088 18.624-5.216 11.36-3.328 24.704 4.768 34.208l416 485.344c6.08 7.104 14.944 11.2 24.288 11.2s18.208-4.096 24.288-11.2l416-485.344C960.448 363.328 962.272 349.984 957.056 338.624z',
                    x: -5,
                    y: -20,
                    width: 10,
                    height: 10
                  },
                  style: {
                    fill: '#45c946'
                  }
                },{
                  type: 'path',
                  shape: {
                    d: 'M952.32 715.2l-416-485.376c-12.16-14.176-36.448-14.176-48.608 0l-416 485.376c-8.128 9.472-9.984 22.848-4.768 34.176C72.16 760.704 83.488 768 96 768l832 0c12.512 0 23.84-7.296 29.056-18.624S960.448 724.672 952.32 715.2z',
                    x: -5,
                    y: 10,
                    width: 10,
                    height: 10
                  },
                  style: {
                    fill: '#45c946'
                  }
                }
              ]
            }
          }
        }
      ]
    })
  }
}
</script>

<style scoped lang="scss">
  .total-user-footer {
    display: flex;
    align-items: center;
    .month {
      margin-left: 10px;
    }
  }
</style>
