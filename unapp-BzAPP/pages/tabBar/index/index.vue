<template>
  <view class="home">

    <NavBar />

    <view class="index_banner_box">
      <swiper class="swiper" indicator-dots :autoplay="true" circular interval="3000" duration="500">
        <swiper-item v-for="(item, index) in topBanner" :key="index">
          <image class="banner" :src="item.img_url" mode="" />
        </swiper-item>
      </swiper>
    </view>

    <CourseNav />

    <view class="online_box">
      <image :src="index_banner.img_url" class="online_img" mode="widthFix" />
    </view>

    <view class="free_box">
      <view class="free_T_box public_tow_box">
        <view class="public_T">限时免费</view>
      </view>
      <FreeCard />
    </view>

    <view class="title_box">
      <view class="title_T_box public_tow_box">
        <view class="public_T">零基础就业班</view>
      </view>
      <JobScroll />
    </view>

    <view class="recommend_box">
      <view class="recommend_T_box public_tow_box">
        <view class="public_T">推荐课程</view>
      </view>
      <CourseCard />
    </view>

    <view class="daotu_box">
      <view class="daotu_T">驱动教学—贯穿教 | 学 | 练 | 测 | 评</view>
      <image :src="foot_banner.img_url" mode="widthFix" />

    </view>

  </view>
</template>

<script>
import NavBar from '../../../components/navBar/navBar.vue'
import CourseNav from '../../../components/courseNav/courseNav.vue'
import FreeCard from '../../../components/freeCard/freeCard.vue'
import JobScroll from '../../../components/jobScroll/jobScroll.vue'
import CourseCard from '../../../components/courseCard/courseCard.vue'

export default {
  data() {
    return {
      topBanner: [],
      index_banner: "",
      foot_banner: ""
    }
  },
  methods: {

  },
  mounted() {
    uni.request({
      url: 'http://html5.bjsxt.cn/api/index/banner',
      success: (res) => {
        this.topBanner = res.data.top_banner
        this.index_banner = res.data.index_banner
        this.foot_banner = res.data.foot_banner
      },
    })
  },
  // 监听下拉刷新
  onPullDownRefresh() {
    uni.switchTab({
      url: '/pages/tabBar/index/index'
    })

    uni.stopPullDownRefresh()
  },
  components: {
    NavBar,
    CourseNav,
    FreeCard,
    JobScroll,
    CourseCard
  }
}
</script>

<style lang="scss" scoped>
.home {
  display: flex;
  flex-direction: column;
  flex: 1;
  overflow: hidden;

  .index_banner_box {
    box-sizing: border-box;
    display: flex;
    width: 100%;
    padding: 25rpx;
    justify-self: center;
    align-items: center;
    border-radius: 5px;
    overflow: hidden;

    .swiper {
      width: 100%;
      height: 260rpx;

      .banner {
        width: 100%;
        height: 260rpx;
      }
    }

  }

  .online_box {
    box-sizing: border-box;
    display: flex;
    width: 100%;
    padding: 13rpx;
    justify-self: center;
    align-items: center;
    margin-bottom: 30rpx;

    .online_img {
      width: 100%;
    }
  }

  .public_tow_box {
    display: flex;
    width: 100%;
    justify-self: center;
    align-items: center;
    padding: 0 30rpx;
    justify-content: space-between;
    align-content: space-between;
    flex-wrap: wrap;

    .public_T {
      font-size: 45rpx;
      font-weight: 700;
    }
  }

  .recommend_T_box {
    margin-bottom: 50rpx;
  }

  .daotu_box {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 15rpx;

    .daotu_T {
      font-size: 45rpx;
      font-weight: 700;
      margin: 30rpx 0;
    }

    image {
      width: 100%;
    }
  }

}
</style>