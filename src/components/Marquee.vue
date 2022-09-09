<!--
 * @Date: 2022-09-09 15:21:53
 * @LastEditors: lichen39 lichen39@58.com
 * @LastEditTime: 2022-09-09 15:42:35
 * @FilePath: /horizontal-marquee/src/components/Marquee.vue
-->
<template>
  <div>
      <ul ref="ul" :style="`left: ${left1}px`">
        <li v-for="(item, index) in data" :key="index">
          <h3><img :src="item.logo" alt="" /></h3>
          <p>{{ item.name }}</p>
        </li>
      </ul>
      <ul :style="`left: ${left2}px`">
        <li v-for="(item, index) in data" :key="index + 'a'">
          <h3><img :src="item.logo" alt="" /></h3>
          <p>{{ item.name }}</p>
        </li>
      </ul>
    </div>
</template>

<script setup>
import { ref, computed, onMounted, nextTick, watch, defineProps } from 'vue'
const props = defineProps({
  data: {
    type: Array,
    default: () => []
  }
})
const ul = ref(null)

const left1 = ref(22)
const left2 = ref(22)
onMounted(() => {
  nextTick(() => {
    const boxWidth = computed(() => {
      if (props.data.length) {
        return Math.floor(ul.value.getBoundingClientRect().width)
      }
      return 0
    })
    const screenWidth = screen.width
    left2.value = screenWidth
    let timer1 = null
    let timer2 = null
    watch(
      boxWidth,
      (val) => {
        if (val && (val + 22) > screenWidth) {
          const right = Math.floor(val - screenWidth)
          const fn1 = () => {
            left1.value -= 0.5
            timer1 = requestAnimationFrame(fn1)

            if (left1.value === -right) {
              timer2 = requestAnimationFrame(fn2)
            }
            if (left1.value < -val) {
              left1.value = screenWidth
              cancelAnimationFrame(timer1)
            }
          }
          const fn2 = () => {
            left2.value -= 0.5
            timer2 = requestAnimationFrame(fn2)
            if (left2.value === -right) {
              timer1 = requestAnimationFrame(fn1)
            }
            if (left2.value < -val) {
              left2.value = screenWidth
              cancelAnimationFrame(timer2)
            }
          }
          requestAnimationFrame(fn1)
        }
      },
      {
        immediate: true
      }
    )
  })
})

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
div {
    position: relative;
    // padding: 0 0 0 22px;
    height: 70px;
    width: 100%;
    overflow: hidden;
  }
  ul {
    position: absolute;
    left: 0;
    display: flex;
    width: max-content;
    li {
      margin: 0 8px;
      h3 {
        margin-bottom: 5px;
        width: 50px;
        height: 50px;
        background: url(https://wos.58cdn.com.cn/cDazYxWcDHJ/picasso/tvs84amq.png) no-repeat
          center/cover;
        display: flex;
        align-items: center;
        justify-content: center;
        img {
          width: 45px;
          height: 45px;
        }
      }
      p {
        font-size: 10px;
        line-height: 14px;
        max-width: 50px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
    }
  }
</style>
