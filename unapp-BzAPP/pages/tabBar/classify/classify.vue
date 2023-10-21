<template>
  <view>

  </view>
</template>

<script>
export default {
  data() {
    return {

    }
  },
  methods: {

  },
  onload() {

  },
  onPullDownRefresh() {
    uni.switchTab({
      url: '/pages/tabBar/classify/classify',
    })

    uni.stopPullDownRefresh()
  },
}
</script>

<style lang="scss" ></style>