<template>
  <view class="content">
    <image
      class="logo"
      src="/static/logo.png"
    />
    <view class="text-area">
      <text class="title">{{title}}</text>
    </view>
    <button
      type="primary"
      @tap="getlogin()"
    >跳转到登录的页面</button>
    <view class="page-section page-section-gap">
      <map
        style="width: 100%; height: 300rpx;"
        :latitude="latitude"
        :longitude="longitude"
        :markers="covers"
      >
      </map>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      title: 'Hello',
      latitude: 39.909,
      longitude: 116.39742,
      covers: [{
        latitude: 39.909,
        longitude: 116.39742,
        iconPath: '@/logo.png'
      }, {
        latitude: 39.90,
        longitude: 116.39,
        iconPath: '@/logo.png'
      }]
    }
  },
  onLoad() {
    uni.$emit('update', { msg: '页面更新' })
  },
  methods: {
    getlogin() {
      uni.switchTab({
        url: '../login/index',
        success: res => { },
        fail: () => { },
        complete: () => { }
      });
    }
  }
}
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.page-section {
  width: 100%;
}
.logo {
  height: 200rpx;
  width: 200rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
}

.text-area {
  display: flex;
  justify-content: center;
}

.title {
  font-size: 36rpx;
  color: #8f8f94;
}
</style>
