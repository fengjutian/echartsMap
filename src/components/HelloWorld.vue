<template>
  <div class="hello">
    <div id="map" @georoam='zoomFun' @dblclick='dblclickFun'></div>
  </div>
</template>

<script>
import echarts from 'echarts'
// import '../../static/china.js'

export default {
  name: 'HelloWorld',
  data () {
    return {
      jiangsuData: require('../../static/jiangsu.json'),
      china: require('../../static/china.json'),
      mapType: 'china'
    }
  },
  mounted () {
    // this.getMapFun()

    // this.getChinaMap()
    // this.getChinaMap1()
    // this.getJSMap()

    this.changeMap()
  },
  methods: {
    dblclickFun (data) {
      console.log(777, data)
      if (data) {

      }
    },
    zoomFun (res) {
      console.log('res', res)
    },
    changeMap () {
      var dom = document.getElementById('map')
      var myChart = echarts.init(dom)
      var option = null

      myChart.showLoading()
      myChart.hideLoading()
      let geoJson = {}
      if (this.mapType == 'china') {
        geoJson = this.china
      } else {
        geoJson = this.jiangsuData
      }

      echarts.registerMap(this.mapType, geoJson)

      myChart.setOption(option = {
        // title: {
        //   text: '香港18区人口密度 （2011）',
        //   subtext: '人口密度数据来自Wikipedia',
        //   sublink: 'http://zh.wikipedia.org/wiki/%E9%A6%99%E6%B8%AF%E8%A1%8C%E6%94%BF%E5%8D%80%E5%8A%83#cite_note-12'
        // },
        // tooltip: {
        //   trigger: 'item',
        //   formatter: '{b}<br/>{c} (p / km2)'
        // },
        // toolbox: {
        //   show: true,
        //   orient: 'vertical',
        //   left: 'right',
        //   top: 'center',
        //   feature: {
        //     dataView: {readOnly: false},
        //     restore: {},
        //     saveAsImage: {}
        //   }
        // },
        visualMap: {
          min: 800,
          max: 50000,
          text: ['High', 'Low'],
          realtime: false,
          calculable: true,
          inRange: {
            color: ['lightskyblue', 'yellow', 'orangered']
          }
        },
        series: [
          {
            name: '',
            type: 'map',
            roam: true,
            mapType: this.mapType, // 自定义扩展图表类型
            label: {
              show: false
            },
            data: [
              {name: '北京', value: Math.round(Math.random() * 1000)},
              {name: '天津', value: Math.round(Math.random() * 1000)},
              {name: '上海', value: Math.round(Math.random() * 1000)},
              {name: '重庆', value: Math.round(Math.random() * 1000)},
              {name: '河北', value: Math.round(Math.random() * 1000)},
              {name: '河南', value: Math.round(Math.random() * 1000)},
              {name: '云南', value: Math.round(Math.random() * 1000)},
              {name: '辽宁', value: Math.round(Math.random() * 1000)},
              {name: '黑龙江', value: Math.round(Math.random() * 1000)},
              {name: '湖南', value: Math.round(Math.random() * 1000)},
              {name: '安徽', value: Math.round(Math.random() * 1000)},
              {name: '山东', value: Math.round(Math.random() * 1000)},
              {name: '新疆', value: Math.round(Math.random() * 1000)},
              {name: '江苏', value: Math.round(Math.random() * 1000)},
              {name: '浙江', value: Math.round(Math.random() * 1000)},
              {name: '江西', value: Math.round(Math.random() * 1000)},
              {name: '湖北', value: Math.round(Math.random() * 1000)},
              {name: '广西', value: Math.round(Math.random() * 1000)},
              {name: '甘肃', value: Math.round(Math.random() * 1000)},
              {name: '山西', value: Math.round(Math.random() * 1000)},
              {name: '内蒙古', value: Math.round(Math.random() * 1000)},
              {name: '陕西', value: Math.round(Math.random() * 1000)},
              {name: '吉林', value: Math.round(Math.random() * 1000)},
              {name: '福建', value: Math.round(Math.random() * 1000)},
              {name: '贵州', value: Math.round(Math.random() * 1000)},
              {name: '广东', value: Math.round(Math.random() * 1000)},
              {name: '青海', value: Math.round(Math.random() * 1000)},
              {name: '西藏', value: Math.round(Math.random() * 1000)},
              {name: '四川', value: Math.round(Math.random() * 1000)},
              {name: '宁夏', value: Math.round(Math.random() * 1000)},
              {name: '海南', value: Math.round(Math.random() * 1000)},
              {name: '台湾', value: Math.round(Math.random() * 1000)},
              {name: '香港', value: Math.round(Math.random() * 1000)},
              {name: '澳门', value: Math.round(Math.random() * 1000)}
            ],
            // 自定义名称映射
            nameMap: {

            }
          }
        ]
      })

      if (option && typeof option === 'object') {
        myChart.setOption(option, true)
      }
    },
    getJSMap () {
      var dom = document.getElementById('map')
      var myChart = echarts.init(dom)
      var option = null

      myChart.showLoading()
      myChart.hideLoading()
      const geoJson = this.jiangsuData
      echarts.registerMap('JS', geoJson)

      myChart.setOption(option = {
        // title: {
        //   text: '香港18区人口密度 （2011）',
        //   subtext: '人口密度数据来自Wikipedia',
        //   sublink: 'http://zh.wikipedia.org/wiki/%E9%A6%99%E6%B8%AF%E8%A1%8C%E6%94%BF%E5%8D%80%E5%8A%83#cite_note-12'
        // },
        // tooltip: {
        //   trigger: 'item',
        //   formatter: '{b}<br/>{c} (p / km2)'
        // },
        // toolbox: {
        //   show: true,
        //   orient: 'vertical',
        //   left: 'right',
        //   top: 'center',
        //   feature: {
        //     dataView: {readOnly: false},
        //     restore: {},
        //     saveAsImage: {}
        //   }
        // },
        visualMap: {
          min: 800,
          max: 50000,
          text: ['High', 'Low'],
          realtime: false,
          calculable: true,
          inRange: {
            color: ['lightskyblue', 'yellow', 'orangered']
          }
        },
        series: [
          {
            name: '香港18区人口密度',
            type: 'map',
            roam: true,
            mapType: 'JS', // 自定义扩展图表类型
            label: {
              show: false
            },
            data: [

            ],
            // 自定义名称映射
            nameMap: {

            }
          }
        ]
      })

      if (option && typeof option === 'object') {
        myChart.setOption(option, true)
      }
    },
    getChinaMap () {
      var dom = document.getElementById('map')
      var myChart = echarts.init(dom)
      let option = null
      option = {
        // title: {
        //   text: 'iphone销量',
        //   subtext: '纯属虚构',
        //   left: 'center'
        // },
        tooltip: {
          trigger: 'item'
        },
        // legend: {
        //   orient: 'vertical',
        //   left: 'left',
        //   data: ['iphone3', 'iphone4', 'iphone5']
        // },
        // visualMap: {
        //   min: 800,
        //   max: 50000,
        //   text: ['High', 'Low'],
        //   realtime: false,
        //   calculable: true,
        //   inRange: {
        //     // color: ['#24CFF4', '#2E98CA', '#1E62AC']
        //     color: ['lightskyblue', 'yellow', 'orangered']
        //   }
        // },
        // toolbox: {
        //   show: true,
        //   orient: 'vertical',
        //   left: 'right',
        //   top: 'center',
        //   feature: {
        //     mark: {show: true},
        //     dataView: {show: true, readOnly: false},
        //     restore: {show: true},
        //     saveAsImage: {show: true}
        //   }
        // },
        series: [
          {
            name: '',
            type: 'map',
            mapType: 'china',
            roam: true
            // label: {
            //   normal: {
            //     show: false
            //   },
            //   emphasis: {
            //     show: true
            //   }
            // }
            // data: [
            //   {name: '北京', value: Math.round(Math.random() * 1000)},
            //   {name: '天津', value: Math.round(Math.random() * 1000)},
            //   {name: '上海', value: Math.round(Math.random() * 1000)},
            //   {name: '重庆', value: Math.round(Math.random() * 1000)},
            //   {name: '河北', value: Math.round(Math.random() * 1000)},
            //   {name: '河南', value: Math.round(Math.random() * 1000)},
            //   {name: '云南', value: Math.round(Math.random() * 1000)},
            //   {name: '辽宁', value: Math.round(Math.random() * 1000)},
            //   {name: '黑龙江', value: Math.round(Math.random() * 1000)},
            //   {name: '湖南', value: Math.round(Math.random() * 1000)},
            //   {name: '安徽', value: Math.round(Math.random() * 1000)},
            //   {name: '山东', value: Math.round(Math.random() * 1000)},
            //   {name: '新疆', value: Math.round(Math.random() * 1000)},
            //   {name: '江苏', value: Math.round(Math.random() * 1000)},
            //   {name: '浙江', value: Math.round(Math.random() * 1000)},
            //   {name: '江西', value: Math.round(Math.random() * 1000)},
            //   {name: '湖北', value: Math.round(Math.random() * 1000)},
            //   {name: '广西', value: Math.round(Math.random() * 1000)},
            //   {name: '甘肃', value: Math.round(Math.random() * 1000)},
            //   {name: '山西', value: Math.round(Math.random() * 1000)},
            //   {name: '内蒙古', value: Math.round(Math.random() * 1000)},
            //   {name: '陕西', value: Math.round(Math.random() * 1000)},
            //   {name: '吉林', value: Math.round(Math.random() * 1000)},
            //   {name: '福建', value: Math.round(Math.random() * 1000)},
            //   {name: '贵州', value: Math.round(Math.random() * 1000)},
            //   {name: '广东', value: Math.round(Math.random() * 1000)},
            //   {name: '青海', value: Math.round(Math.random() * 1000)},
            //   {name: '西藏', value: Math.round(Math.random() * 1000)},
            //   {name: '四川', value: Math.round(Math.random() * 1000)},
            //   {name: '宁夏', value: Math.round(Math.random() * 1000)},
            //   {name: '海南', value: Math.round(Math.random() * 1000)},
            //   {name: '台湾', value: Math.round(Math.random() * 1000)},
            //   {name: '香港', value: Math.round(Math.random() * 1000)},
            //   {name: '澳门', value: Math.round(Math.random() * 1000)}
            // ]
          }
          // {
          //   name: 'iphone4',
          //   type: 'map',
          //   mapType: 'china',
          //   label: {
          //     normal: {
          //       show: false
          //     },
          //     emphasis: {
          //       show: true
          //     }
          //   },
          //   data: [
          //     {name: '北京', value: Math.round(Math.random() * 1000)},
          //     {name: '天津', value: Math.round(Math.random() * 1000)},
          //     {name: '上海', value: Math.round(Math.random() * 1000)},
          //     {name: '重庆', value: Math.round(Math.random() * 1000)},
          //     {name: '河北', value: Math.round(Math.random() * 1000)},
          //     {name: '安徽', value: Math.round(Math.random() * 1000)},
          //     {name: '新疆', value: Math.round(Math.random() * 1000)},
          //     {name: '浙江', value: Math.round(Math.random() * 1000)},
          //     {name: '江西', value: Math.round(Math.random() * 1000)},
          //     {name: '山西', value: Math.round(Math.random() * 1000)},
          //     {name: '内蒙古', value: Math.round(Math.random() * 1000)},
          //     {name: '吉林', value: Math.round(Math.random() * 1000)},
          //     {name: '福建', value: Math.round(Math.random() * 1000)},
          //     {name: '广东', value: Math.round(Math.random() * 1000)},
          //     {name: '西藏', value: Math.round(Math.random() * 1000)},
          //     {name: '四川', value: Math.round(Math.random() * 1000)},
          //     {name: '宁夏', value: Math.round(Math.random() * 1000)},
          //     {name: '香港', value: Math.round(Math.random() * 1000)},
          //     {name: '澳门', value: Math.round(Math.random() * 1000)}
          //   ]
          // },
          // {
          //   name: 'iphone5',
          //   type: 'map',
          //   mapType: 'china',
          //   label: {
          //     normal: {
          //       show: false
          //     },
          //     emphasis: {
          //       show: true
          //     }
          //   },
          //   data: [
          //     {name: '北京', value: Math.round(Math.random() * 1000)},
          //     {name: '天津', value: Math.round(Math.random() * 1000)},
          //     {name: '上海', value: Math.round(Math.random() * 1000)},
          //     {name: '广东', value: Math.round(Math.random() * 1000)},
          //     {name: '台湾', value: Math.round(Math.random() * 1000)},
          //     {name: '香港', value: Math.round(Math.random() * 1000)},
          //     {name: '澳门', value: Math.round(Math.random() * 1000)}
          //   ]
          // }
        ]
      }
      if (option && typeof option === 'object') {
        myChart.setOption(option, true)
      }
    },
    getChinaMap1 () {
      var dom = document.getElementById('map')
      var myChart = echarts.init(dom)
      let option = null

      myChart.showLoading()
      myChart.hideLoading()
      const geoJson = this.jiangsuData
      echarts.registerMap('JS', geoJson)

      option = {
        // title: {
        //   text: 'iphone销量',
        //   subtext: '纯属虚构',
        //   left: 'center'
        // },
        tooltip: {
          trigger: 'item'
        },
        // legend: {
        //   orient: 'vertical',
        //   left: 'left',
        //   data: ['iphone3', 'iphone4', 'iphone5']
        // },
        // visualMap: {
        //   min: 800,
        //   max: 50000,
        //   text: ['High', 'Low'],
        //   realtime: false,
        //   calculable: true,
        //   inRange: {
        //     // color: ['#24CFF4', '#2E98CA', '#1E62AC']
        //     color: ['lightskyblue', 'yellow', 'orangered']
        //   }
        // },
        // toolbox: {
        //   show: true,
        //   orient: 'vertical',
        //   left: 'right',
        //   top: 'center',
        //   feature: {
        //     mark: {show: true},
        //     dataView: {show: true, readOnly: false},
        //     restore: {show: true},
        //     saveAsImage: {show: true}
        //   }
        // },
        series: [
          {
            name: '',
            type: 'map',
            mapType: 'JS',
            roam: true
            // label: {
            //   normal: {
            //     show: false
            //   },
            //   emphasis: {
            //     show: true
            //   }
            // }
            // data: [
            //   {name: '北京', value: Math.round(Math.random() * 1000)},
            //   {name: '天津', value: Math.round(Math.random() * 1000)},
            //   {name: '上海', value: Math.round(Math.random() * 1000)},
            //   {name: '重庆', value: Math.round(Math.random() * 1000)},
            //   {name: '河北', value: Math.round(Math.random() * 1000)},
            //   {name: '河南', value: Math.round(Math.random() * 1000)},
            //   {name: '云南', value: Math.round(Math.random() * 1000)},
            //   {name: '辽宁', value: Math.round(Math.random() * 1000)},
            //   {name: '黑龙江', value: Math.round(Math.random() * 1000)},
            //   {name: '湖南', value: Math.round(Math.random() * 1000)},
            //   {name: '安徽', value: Math.round(Math.random() * 1000)},
            //   {name: '山东', value: Math.round(Math.random() * 1000)},
            //   {name: '新疆', value: Math.round(Math.random() * 1000)},
            //   {name: '江苏', value: Math.round(Math.random() * 1000)},
            //   {name: '浙江', value: Math.round(Math.random() * 1000)},
            //   {name: '江西', value: Math.round(Math.random() * 1000)},
            //   {name: '湖北', value: Math.round(Math.random() * 1000)},
            //   {name: '广西', value: Math.round(Math.random() * 1000)},
            //   {name: '甘肃', value: Math.round(Math.random() * 1000)},
            //   {name: '山西', value: Math.round(Math.random() * 1000)},
            //   {name: '内蒙古', value: Math.round(Math.random() * 1000)},
            //   {name: '陕西', value: Math.round(Math.random() * 1000)},
            //   {name: '吉林', value: Math.round(Math.random() * 1000)},
            //   {name: '福建', value: Math.round(Math.random() * 1000)},
            //   {name: '贵州', value: Math.round(Math.random() * 1000)},
            //   {name: '广东', value: Math.round(Math.random() * 1000)},
            //   {name: '青海', value: Math.round(Math.random() * 1000)},
            //   {name: '西藏', value: Math.round(Math.random() * 1000)},
            //   {name: '四川', value: Math.round(Math.random() * 1000)},
            //   {name: '宁夏', value: Math.round(Math.random() * 1000)},
            //   {name: '海南', value: Math.round(Math.random() * 1000)},
            //   {name: '台湾', value: Math.round(Math.random() * 1000)},
            //   {name: '香港', value: Math.round(Math.random() * 1000)},
            //   {name: '澳门', value: Math.round(Math.random() * 1000)}
            // ]
          }
          // {
          //   name: 'iphone4',
          //   type: 'map',
          //   mapType: 'china',
          //   label: {
          //     normal: {
          //       show: false
          //     },
          //     emphasis: {
          //       show: true
          //     }
          //   },
          //   data: [
          //     {name: '北京', value: Math.round(Math.random() * 1000)},
          //     {name: '天津', value: Math.round(Math.random() * 1000)},
          //     {name: '上海', value: Math.round(Math.random() * 1000)},
          //     {name: '重庆', value: Math.round(Math.random() * 1000)},
          //     {name: '河北', value: Math.round(Math.random() * 1000)},
          //     {name: '安徽', value: Math.round(Math.random() * 1000)},
          //     {name: '新疆', value: Math.round(Math.random() * 1000)},
          //     {name: '浙江', value: Math.round(Math.random() * 1000)},
          //     {name: '江西', value: Math.round(Math.random() * 1000)},
          //     {name: '山西', value: Math.round(Math.random() * 1000)},
          //     {name: '内蒙古', value: Math.round(Math.random() * 1000)},
          //     {name: '吉林', value: Math.round(Math.random() * 1000)},
          //     {name: '福建', value: Math.round(Math.random() * 1000)},
          //     {name: '广东', value: Math.round(Math.random() * 1000)},
          //     {name: '西藏', value: Math.round(Math.random() * 1000)},
          //     {name: '四川', value: Math.round(Math.random() * 1000)},
          //     {name: '宁夏', value: Math.round(Math.random() * 1000)},
          //     {name: '香港', value: Math.round(Math.random() * 1000)},
          //     {name: '澳门', value: Math.round(Math.random() * 1000)}
          //   ]
          // },
          // {
          //   name: 'iphone5',
          //   type: 'map',
          //   mapType: 'china',
          //   label: {
          //     normal: {
          //       show: false
          //     },
          //     emphasis: {
          //       show: true
          //     }
          //   },
          //   data: [
          //     {name: '北京', value: Math.round(Math.random() * 1000)},
          //     {name: '天津', value: Math.round(Math.random() * 1000)},
          //     {name: '上海', value: Math.round(Math.random() * 1000)},
          //     {name: '广东', value: Math.round(Math.random() * 1000)},
          //     {name: '台湾', value: Math.round(Math.random() * 1000)},
          //     {name: '香港', value: Math.round(Math.random() * 1000)},
          //     {name: '澳门', value: Math.round(Math.random() * 1000)}
          //   ]
          // }
        ]
      }
      if (option && typeof option === 'object') {
        myChart.setOption(option, true)
      }
    },
    getMapFun () {
      // console.log('start')

      // import sichuan from 'echarts/map/js/province/sichuan'
      // import anhui from 'echarts/map/js/province/anhui'

      // 定义全国省份的数组
      let provinces = ['shanghai', 'hebei', 'shanxi', 'neimenggu', 'liaoning', 'jilin', 'heilongjiang', 'jiangsu', 'zhejiang', 'anhui', 'fujian', 'jiangxi', 'shandong', 'henan', 'hubei', 'hunan', 'guangdong', 'guangxi', 'hainan', 'sichuan', 'guizhou', 'yunnan', 'xizang', 'shanxi1', 'gansu', 'qinghai', 'ningxia', 'xinjiang', 'beijing', 'tianjin', 'chongqing', 'xianggang', 'aomen', 'taiwan']

      let provincesText = ['上海', '河北', '山西', '内蒙古', '辽宁', '吉林', '黑龙江', '江苏', '浙江', '安徽', '福建', '江西', '山东', '河南', '湖北', '湖南', '广东', '广西', '海南', '四川', '贵州', '云南', '西藏', '陕西', '甘肃', '青海', '宁夏', '新疆', '北京', '天津', '重庆', '香港', '澳门', '台湾']

      // 初始化echarts
      let map = echarts.init(document.getElementById('map'))
      // console.log(map)

      // 定义初始加载的地图区域,中国地图
      let selected = 'china'

      // 定义加载地图的方法
      // 参数为要显示地图区域的名字
      let loadMap = (param) => {
        map.setOption({
          geo: {
          //  map: 'china' | '四川', // 必须要先引入了对应地图的js文件或者json文件，在这一步的时候，echarts会自动将对应的JS文件注入，地图才会显示.
            map: param
          }
        })
      }

      // 第一次加载地图
      loadMap(selected)

      // 判断当前要加载的地图是不是省？
      let isProvince = (name) => {
        return provincesText.some((province) => {
          return province === name
        })
      }

      // 定义方法加载某个省的地图文件
      let loadScriptMap = (name, callback) => {
        // 获取这个省的拼音名字 name = '四川' => pinyinName = 'sichuan'
        let pinyinName = provinces[provincesText.indexOf(name)]
        console.log(pinyinName)
        // 引入这个对应的地图JS，如果是在项目中要打包，请将这些文件提取出来，放在静态资源中
        // build的时候这些文件不会被打包，无可加载资源地图是不会显示的！！！！
        //   let currentMap = require(`echarts/map/js/province/${pinyinName}`)
        callback(name)
      }

      // 监听地图点击事件
      map.on('click', (ev) => {
        // 如果点击的是一个省，那就切换到这个省的地图
        if (isProvince(ev.name)) {
          selected = ev.name
          console.log(selected)
          // 从外部加载这个省的地图文件
          loadScriptMap(ev.name, loadMap)
        } else {
          // 否则切换中国地图
          selected = 'china'
          loadMap(selected)
        }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
   #map {
      width: 1200px;
      height: 800px;
    }
</style>
