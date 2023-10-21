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
  onLoad() {

  },
  onPullDownRefresh() {
    uni.switchTab({
      url: '/pages/tabBar/study/study'
    })

    uni.stopPullDownRefresh()
  }
}
</script>

<style lang="scss"></style>