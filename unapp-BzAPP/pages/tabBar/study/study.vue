<template>
  <view class="home">
    <!-- <web-view src="/static/video.mp4" /> -->
    <view class="video" statusBar>
      <video src="/static/video2.mp4" autoplay loop></video>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {

    }
  },
}
</script>

<style lang="scss">
.video {
  height: 100vh;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  video {
    width: 100%;
    height: 1115rpx;
  }

}
</style>