<template>
  <view class="container">
    <button
      type="primary"
      class="login"
    > {{name}}</button>
    <view>
      <canvas
        style="width: 300px; height: 200px;"
        canvas-id="firstCanvas"
      ></canvas>
    </view>
    <view>
      <uni-badge text="1">12</uni-badge>
      <uni-badge
        text="2"
        type="success"
        @click="bindClick"
      >12</uni-badge>
      <uni-badge
        text="3"
        type="primary"
        :inverted="true"
      >121</uni-badge>
    </view>
  </view>
</template>

<script>
import { uniBadge } from '@dcloudio/uni-ui'
//import uniBadge from '@dcloudio/uni-ui/lib/uni-badge/uni-badge.vue' //也可使用此方式引入组件
export default {
  components: { uniBadge }
  ,
  data() {
    return {
      name: '需要登录'
    }
  },
  onLoad() {
    this.getName()
  },
  onReady: function (e) {
    var context = uni.createCanvasContext('firstCanvas')

    context.setStrokeStyle("#00ff00")
    context.setLineWidth(5)
    context.rect(0, 0, 200, 200)
    context.stroke()
    context.setStrokeStyle("#ff0000")
    context.setLineWidth(2)
    context.moveTo(160, 100)
    context.arc(100, 100, 60, 0, 2 * Math.PI, true)
    context.moveTo(140, 100)
    context.arc(100, 100, 40, 0, Math.PI, false)
    context.moveTo(85, 80)
    context.arc(80, 80, 5, 0, 2 * Math.PI, true)
    context.moveTo(125, 80)
    context.arc(120, 80, 5, 0, 2 * Math.PI, true)
    context.stroke()
    context.draw()
  },
  methods: {
    getName() {
      uni.showModal({
        content: '登录页面',
        showCancel: false
      });
    },
    canvasIdErrorCallback(e) {
      console.error(e.detail.errMsg)
    }
  }
}
</script>

<style scoped>
.login {
  width: 300rpx;
  height: 80rpx;
}
</style>
