<!--
 * @Date: 2022-09-09 15:21:53
 * @LastEditors: lichen39 lichen39@58.com
 * @LastEditTime: 2022-09-09 15:37:53
 * @FilePath: /horizontal-marquee/src/App.vue
-->
<template>
  <Marquee :data="data" />
</template>

<script setup>
import { ref } from 'vue'
import Marquee from './components/Marquee.vue'
const data = ref([
  {
    logo: 'http://pic1.58cdn.com.cn/nowater/chrcmspic2021/n_v20342437046344e588f61b9b6b184bc65.png',
    name: '重庆交通职业学校'
  },
  {
    logo: 'http://pic1.58cdn.com.cn/nowater/chrcmspic2021/n_v2de982c44f3fb44f6a4d5529dfc1fc566.png',
    name: '大连大学'
  },
  {
    logo: 'http://pic1.58cdn.com.cn/nowater/chrcmspic2021/n_v236e881ad4491461f8e875822454c67cb.png',
    name: '贵州工商职业学校'
  },
  {
    logo: 'http://pic1.58cdn.com.cn/nowater/chrcmspic2021/n_v2a5467a67bd1c4412bdb03e84ab3fb292.png',
    name: '哈尔滨广厦学院'
  },
  {
    logo: 'http://pic1.58cdn.com.cn/nowater/chrcmspic2021/n_v2997f4e80eb734e48839fd222440c22e1.png',
    name: '河北化工医药'
  },
  {
    logo: 'http://pic1.58cdn.com.cn/nowater/chrcmspic2021/n_v2d498ff254f6a486ca39ec3c82de6420f.png',
    name: '河北石油职业技术学校'
  }
])
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
ul,li{
  list-style: none;
}
</style>
