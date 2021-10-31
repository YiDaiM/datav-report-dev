<template>
  <div class="bottom-view">
    <div class="view">
      <el-card shadow="hover">
        <template slot="header">
          <div class="title-wrapper">
            <div class="title">关键词搜索</div>
          </div>
        </template>
        <template>
          <div class="chart-wrapper">
            <div class="chart-inner">
              <div class="chart">
                <div class="chart-title">搜索用户数</div>
                <div class="chart-data">93,634</div>
                <div id="search-user-chart"/>
              </div>
              <div class="chart">
                <div class="chart-title">搜索量</div>
                <div class="chart-data">198,782</div>
                <div id="search-number-chart"/>
              </div>
            </div>
            <div class="table-wrapper">
              <el-table :data="tableData" height="250">
                <el-table-column label="排名" prop="rank"/>
                <el-table-column label="关键词" prop="keyword"/>
                <el-table-column label="总搜索量" prop="count"/>
                <el-table-column label="搜索用户数" prop="users"/>
              </el-table>
              <el-pagination background layout="prev, pager, next" :total="100" @current-change="onPageChange"/>
            </div>
          </div>
        </template>
      </el-card>
    </div>
    <div class="view">
      <el-card shadow="hover">
        <template slot="header">
          <div class="title-wrapper">
            <div class="title">分类销售排行</div>
            <div class="radio-wrapper">
              <el-radio-group v-model="label1" size="small">
                <el-radio-button :label="label1" />
                <el-radio-button :label="label2" />
              </el-radio-group>
            </div>
          </div>
        </template>
        <template>
          <div class="chart-wrapper">
            <div id="category-sales-chart" />
          </div>
        </template>
      </el-card>
    </div>
  </div>
</template>

<script>

export default {
  name: "Index",
  data() {
    return {
      tableData: [{
        id: 1, rank: 1, keyword: '北京', count: 876, users: 90, range: '90%'
      },{
        id: 2, rank: 2, keyword: '上海', count: 970, users: 90, range: '90%'
      },{
        id: 3, rank: 3, keyword: '广州', count: 990, users: 90, range: '90%'
      },{
        id: 4, rank: 4, keyword: '南京', count: 566, users: 90, range: '90%'
      },{
        id: 5, rank: 5, keyword: '杭州', count: 264, users: 90, range: '90%'
      },{
        id: 6, rank: 6, keyword: '深圳', count: 435, users: 90, range: '90%'
      },{
        id: 7, rank: 7, keyword: '福州', count: 777, users: 90, range: '90%'
      },{
        id: 8, rank: 8, keyword: '合肥', count: 124, users: 90, range: '90%'
      },{
        id: 9, rank: 9, keyword: '邯郸', count: 435, users: 90, range: '90%'
      }],
      label1: '品类',
      label2: '商品',
      mockData: [{
        legendname: '粉面粥店',
        value: 67,
        percent: '24.87%',
        itemStyle: {
          color: '#e7e702'
        },
        name: '粉面粥店 | 24.87%'
      },{
        legendname: '简餐便当',
        value: 97,
        percent: '20.00%',
        itemStyle: {
          color: 'red'
        },
        name: '简餐便当 | 20.00%'
      },{
        legendname: '汉堡披萨',
        value: 92,
        percent: '13.59%',
        itemStyle: {
          color: '#5085f2'
        },
        name: '汉堡披萨 | 13.59%'
      },{
        legendname: '香锅冒菜',
        value: 92,
        percent: '17.69%',
        itemStyle: {
          color: 'yellow'
        },
        name: '香锅冒菜 | 17.69%'
      },{
        legendname: '小吃炸串',
        value: 92,
        percent: '17.18%',
        itemStyle: {//这里的itemStyle是单个的style
          color: 'lightgreen'
        },
        name: '小吃炸串 | 17.59%'
      },{
        legendname: '地方菜系',
        value: 92,
        percent: '6.67%',
        itemStyle: {
          color: '#5085f2'
        },
        name: '地方菜系 | 6.67%'
      }]
    }
  },
  methods: {
    onPageChange(page) {
      console.log(page)
    }
  },
  mounted() {
    const chartDom = document.getElementById('search-user-chart')
    const chart = this.$echarts.init(chartDom)
    chart.setOption({
      xAxis: {
        type: 'category',
        boundaryGap: false //让左右两边伸展开
      },
      yAxis: {
          show: false
      },
      grid: {
        top: 0,
        left: 0,
        right: 0,
        bottom: 0
      },
      series: [{
        name: '品类分布',
        type: 'line',
        data: [100,156,200,250,200,150,100,50,100,150],
        areaStyle: {
          color: 'rgba(95, 187, 255, .5)'
        },
        lineStyle: {
          color: 'rgb(95, 187, 255)'
        },
        itemStyle: {
          opacity: 0
        },
        smooth: true
      }]
    })
    const chartDom2 = document.getElementById('search-number-chart')
    const myChart = this.$echarts.init(chartDom2)
    myChart.setOption({
      xAxis: {
        type: 'category',
        boundaryGap: false //让左右两边伸展开
      },
      yAxis: {
        show: false
      },
      grid: {
        top: 0,
        left: 0,
        right: 0,
        bottom: 0
      },
      series: [{
        type: 'line',
        data: [100,156,200,250,200,150,100,50,100,150],
        areaStyle: {
          color: 'rgba(95, 187, 255, .5)'
        },
        lineStyle: {
          color: 'rgb(95, 187, 255)'
        },
        itemStyle: {
          opacity: 0
        },
        smooth: true
      }]
    })
    const categoryDom = document.getElementById('category-sales-chart')
    const categoryChart = this.$echarts.init(categoryDom)
    categoryChart.setOption({
      title: [{
        text: '品类分布',
        textStyle: {
          fontSize: 14,
          color: '#666'
        },
        left: 20,
        top: 20
      },{
        text: '累计订单量',
        subtext: '320',
        x: '34.5%',
        y: "42.5%",
        textAlign: 'center',//在这里面，left是往右偏移，right是往左偏移，center是中间
        textStyle: {
          fontSize: 14,
          color: '#999'
        },
        subtextStyle: {
          fontSize: 28,
          color: '#333'
        }
      }],
      series: [{
        name: '品类分布',
        type: 'pie',
        data: this.mockData,
        label: {
          normal: {
            show: true,
            position: 'outter',
            formatter: params => params.data.legendname
          }
        },
        center: ['35%', '50%'],
        radius: ['45%', '60%'],
        labelLine: {
          length: 5,
          length2: 3,
          smooth: true
        },
        itemStyle: {
          borderWidth: 4,
          borderColor: '#fff'
        }
      }],
      legend: {
        type: 'scroll',
        height: 200,
        orient: 'vertical',
        left: '70%',
        top: 'middle',
        textStyle: {
          color: '#8c8c8c'
        }
      },
      tooltip: {
        formatter: (params) => {
          let str = params.seriesName + "<br />" + params.marker + params.data.legendname + "<br />" +
            "数量 : " + "&nbsp" + params.data.value + "<br />" + "占比 :" + "&nbsp" +
            params.data.percent
          return str
        }
      }
    })
  }
}
</script>

<style scoped lang="scss">
  .bottom-view {
    display: flex;
    margin-top: 20px;
    .view {
      flex: 1;
      width: 50%;
      box-sizing: border-box;
      &:first-child {
        padding-right: 10px;
      }
      &:last-child {
        padding-left: 10px;
      }
      .title-wrapper {
        display: flex;
        align-items: center;
        height: 60px;
        padding-left: 20px;
        box-sizing: border-box;
        border-bottom: 1px solid #eee;
        font-size: 14px;
        font-weight: 500;
        .radio-wrapper {
          flex: 1;
          display: flex;
          justify-content: flex-end;
          padding-right: 20px;
        }
      }
      .chart-wrapper {
        display: flex;
        flex-direction: column;
        margin-top: 20px;
        height: 452px;
        #category-sales-chart {
          width: 100%;
          height: 100%;
        }
        .chart-inner {
          display: flex;
          padding: 0 10px;
          margin-top: 20px;
          .chart {
            flex: 1;
            padding: 0 10px;
            .chart-title {
              color: #999;
              font-size: 14px;
            }
            .chart-data {
              font-size: 22px;
              color: #333;
              font-weight: 500;
              letter-spacing: 2px;
            }
            #search-user-chart {
              height: 50px;
            }
            #search-number-chart {
              height: 50px;
            }
          }
        }
        .table-wrapper {
          flex: 1;
          margin-top: 20px;
          padding: 0 20px 20px;
          .el-pagination {
            display: flex;
            justify-content: flex-end;
            margin-top: 15px;
          }
        }
      }
    }
  }
</style>
