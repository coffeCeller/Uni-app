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
      <canvas
        style="width: 400px; height: 500px;"
        canvas-id="secondCanvas"
      ></canvas>
      <canvas
        style="width: 400px; height: 500px;"
        canvas-id="secondCanvas"
        @error="canvasIdErrorCallback"
      ></canvas>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      name: '是否需要登录'
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
